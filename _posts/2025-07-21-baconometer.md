---
layout: post
title: "Building the Baconometer"
---

## Introduction

The Baconometer is a playful yet technically interesting web app that answers the question: _how connected are two actors through shared films?_ Inspired by the "Six Degrees of Kevin Bacon" game, the app computes the shortest path of collaboration between actors using movie credits. At the time of writing the baconometer is hosted [here] (https://baconometer.foobarcat.com). The baconometer is inspired by venerable [oracle of bacon](https://oracleofbacon.org/).

This post outlines how the Baconometer was designed and built - from database selection, and service development to deployment strategy.

---

## The Problem

At the core, the Baconometer is about finding connections in a network. Given two actors, how are they linked through shared films and co-stars? This is a classic graph problem, where nodes are actors and films, and edges represent acting roles in those films.

Solving this efficiently for hundreds of thousands of actors and millions of credits means choosing the right data model and tools.

---

## Data Gathering: TMDB Over IMDb

One of the earliest hurdles was data sourcing. IMDb data is comprehensive but comes with restrictive licensing terms that prohibit many forms of redistribution and use.

Instead, I opted for [TMDB (The Movie Database)](https://www.themoviedb.org/), which offers a more permissive API and license. However, TMDB does not provide a bulk data dump like IMDb, which made ingestion less straightforward.

To solve this, I wrote a custom TMDB crawler that recursively traverses the API:

- Starting with a list of popular and credited actors
- Querying their movie credits
- Expanding the graph through co-actors in each film

This strategy incrementally builds a usable actor–film–actor graph suitable for import into Neo4j. The crawler is available here: [tmdb-crawler](https://github.com/aultimus/tmbd-crawler).

## Design Decisions

### Database

Most data problems can be solved with relational databases, indeed the Oracle of Bacon is implemented using a small Postgres database (source: [github](https://oracleofbacon.org/how.php)).

But the Baconometer is fundamentally a graph problem:

- Each actor can appear in many films
- Each film can have many actors
- The shortest path between two actors is a traversal problem


| Feature / Aspect                     | Neo4j (Graph DB)                                     | SQL (Relational DB)                                   |
|-------------------------------------|------------------------------------------------------|--------------------------------------------------------|
| **Data Model**                      | Nodes and relationships (Actor, Film, ACTED_IN)      | Tables with foreign keys (actors, films, credits)      |
| **Querying connections**            | Optimized for path traversal via `MATCH` and `shortestPath` | Requires recursive CTEs or multiple joins             |
| **Shortest path query**             | 1–2 lines in Cypher, efficient                       | Complex recursive SQL or application-side logic        |
| **Performance on deep traversals**  | Fast, native graph traversal                         | Slower, needs multiple joins and careful indexing      |
| **Schema flexibility**              | Schema-optional; easy to evolve                      | Rigid schema; requires migrations for changes          |
| **Learning curve**                  | Graph model and Cypher require some learning         | SQL is widely known and supported                      |
| **Tooling and ecosystem**           | Neo4j Browser for graph visualisation                | Mature RDBMS tools, but not graph-native               |
| **Debugging data relationships**    | Intuitive with visual graph tools                    | Requires interpreting JOINs or ERDs manually           |
| **Storage efficiency**              | Less compact, higher overhead                        | Very compact and efficient for tabular data            |
| **Deployment complexity**           | Requires Neo4j server setup                          | Easier and more portable with PostgreSQL/MySQL         |
| **Maturity / portability**          | Newer technology, evolving standards                 | Mature, portable, and widely adopted                   |

---

- The oracle of bacon uses **recursive CTEs** to compute paths between actors.
- The system works well because:
  - The dataset is relatively small.
  - Queries are optimized and rarely change.
- However, the SQL is **hard to maintain** and not naturally suited to variable-length path queries.


Choose Neo4j when:

- You’re modeling complex, interconnected data.
- You need to perform shortest-path or graph algorithms.
- Your schema is evolving or semi-structured.
- You want readable, expressive queries.

Choose SQL when:

- Your data is tabular and well-structured.
- You’re working with a small dataset and don’t need recursive traversal often.
- You prioritize ease of deployment and cost.
- Your team is experienced with SQL and relational tooling.

#### Conclusion

The Baconometer benefits from **Neo4j’s graph-native capabilities**, allowing it to perform efficient shortest-path queries with readable, maintainable code.

While the **Oracle of Bacon** demonstrates that SQL can technically solve the same problem, it requires significantly more effort in both design and query complexity. Neo4j offers a more elegant and scalable solution for this graph-based problem.

Neo4j provides native graph storage and a query language (`Cypher`) that's optimized for path-finding. I saw this project as an opportunity to learn neo4j and to experiment with a graph database.

With Neo4j, the query to find the shortest path between two actors is as simple as:

```cypher
MATCH path = shortestPath(
  (a:Actor {name: 'Kevin Bacon'})-[:ACTED_IN*]-(b:Actor {name: 'Some Other Actor'})
)
RETURN path
```
This made it a natural choice for the core database.

### Server Software
Python was chosen for its ecosystem and familiarity. Flask, in particular, is:

- Lightweight
- Easy to integrate with background scripts and custom crawlers
- Good enough for serving a simple API and UI
- I wanted to practice my python and flask skills

## Service Implementation

The Baconometer is a simple web app with a single page and a single API endpoint. The API endpoint is a Flask route that takes two actor names as input and returns the shortest path between them.

I added scripts that enable bootstrapping the neo4j database from either IMDB or TMDB datasets.

I added system tests to validate the API endpoint.

## Hosting and Deployment
Initially, I considered managed Neo4j services, but they were expensive and restrictive. I wanted full control over the database and filesystem, especially during debugging and import.

After evaluating AWS, GCP, and some PaaS platforms, I settled on Hetzner Cloud:

- Affordable (€4–10/month range)
- Root access
- Good hardware performance for the price

Hetzner was much more affordable than AWS and co.

### Deployment Setup
The deployment architecture is minimal and simple:

- A single Ubuntu VM (Hetzner)
- System packages: Neo4j (via official APT repo), Python 3.12, pipenv
- Neo4j database files and CSVs mounted in `/var/lib/neo4j/import/`
- Flask app served via gunicorn behind nginx.
- Flask app and neo4j managed via systemd services.
- Neo4j accessed over Bolt (neo4j://localhost:7687)

Deployment steps were handled via a small Bash script and manual provisioning for now. Future improvements could include:

- Dockerizing the whole deployment stack
- CI/CD hooks for auto-deploy

## Conclusion
The Baconometer is a great example of choosing the right tool for the problem. Graphs are a natural fit, and Neo4j's expressiveness made the core logic simple. Flask and Python provided a productive backend environment, and Hetzner offered low-cost flexibility for deployment.

This project demonstrates that you can leverage neo4j to provide a performant and scalable solution for a graph problem in a reasonable time frame (this project was completed in a couple of weeks).

I am excited to think about what other problems neo4j can be targetted at.

