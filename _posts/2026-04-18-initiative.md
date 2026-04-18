---
layout: post
title: "Initiative: Harnessing Adaptability under Uncertainty"
date: 2026-04-18
---

> An engineer during their daily work notices a small unrelated bug. Instead of opening a ticket or asking the original author to fix it, they simply push a pull request containing a fix immediately.

This behaviour may appear odd outside of the industry, In most organisations acting without approval is discouraged. Yet in many high-performing engineering teams this is a routine occurrence, engineers fix problems they were never asked to solve.

This essay aims to explain why this behaviour persists and is even valued.

---

There are two structural properties present in software engineering organisations that make such local action possible:

**Asymmetric information**. Software engineering is characterised by an asymmetric and uncertain information environment. Software is complex and often under documented, which results in uncertainty. To resolve the uncertainty a developer is forced to construct a mental model of the system upon which they are working. This information that the developer gains via this process naturally creates an asymmetry between themselves and their colleagues.

**Authority**. Local action requires authority, whether implicit or explicit. Many organisations adopt policies that don't block and sometimes even encourage engineers to suggest fixes for code not directly related to their work, even if a different team maintains the final authority for approval. It is this implicit authority provided via the organisation that makes local action possible.

---

Once an engineer has the capacity to make a change there are several factors which determine whether they will act locally or centrally co-ordinate action.

**Cost of Local Action**. In our example the cost of such a fix is low. The bug is small and bounded, verification of the fix is straightforward. Whilst the engineer already has context on the issue, they can produce the fix relatively quickly. The fix is submitted as a proposal, to be reviewed externally, so some of the burden of thoroughness and reasoning about second order effects is distributed. Additionally, the change is reversible if something were to go wrong. Thanks to versioning, observability and deployment infrastructure, most mistakes are salvageable.

**Coupling**. Coupling represents how connected the system under observation is to other systems. In our example the change is small and has few interdependencies, it has low coupling, reducing the possible second order effects it may introduce, and limiting the blast radius if something were to go wrong.

**Urgency**. In our example, the bug has impact so is somewhat urgent but not extreme. The more urgent an issue is, the higher the cost of inaction. If the issue is currently negatively impacting users that increases the urgency, and likewise increases the cost of inaction.

In summary, if we break down our example across these dimensions:
* asymmetric information: structurally present
* authority: implicit (actively encouraged)
* cost of local action: low (PRs are cheap)
* coupling: low
* urgency: low

----

**When individuals encounter problems locally, possess asymmetric information and the authority to act, and the system has few dependencies they often act immediately.**

This behaviour is best summarised as **initiative** - **acting without explicit instruction based on local judgement.**

When judgement and decision making power are devolved closer to the source of information, several effects occur. The cost of co-ordination is circumvented, reducing time spent communicating. This results in improved adaptability to emergent information and increased decision velocity.  In combination with low coupling and low cost of action, initiative becomes intrinsically rewarding. Engineers receive immediate feedback, operate within bounded risk, and avoid costly coordination overhead. This creates a tight action–feedback loop that is both efficient and cognitively satisfying.

Whilst initiative has clear benefits, it is important that it is **constrained** and **bounded**, because unrestrained initiative can harm **coherence**.

Initiative requires constraints so that it does not result in fragmentation. For example different engineers may favour different implementations, resulting in a lack of consistency of approach. Teams can resolve this by aligning upon constraints - such as common patterns first.

Additionally initiative requires bounds, so that uncoordinated judgement does not make binding decisions that have far reaching impact. For example, imagine an engineer making system wide design decisions upon initiative, such decisions could have consequential downstream effects. Teams are better served by bounding initiative to work that is loosely coupled.

Initiative's strengths and weaknesses make it naturally suited to some environments more than others.

---

In addition to engineering, the military, emergency response and air traffic control are domains where initiative is well suited. The military shares a similar information environment to engineering, it is characterised by asymmetry and uncertainty of information. There is dense local context - morale, visibility, unit strength, these are not easily communicated in real time. Additionally situations can evolve dramatically in seconds, creating a great deal of urgency.

To deal with this the military developed the doctrine of Mission Command in order to harness initiative. Commanders define objectives, unit leaders determine how those objectives are achieved. Authority is devolved explicitly with clear bounds to the domain of execution which has few interdependencies. This enables the unit commander to leverage emerging local information to make more realistic and effective plans. Additionally, when acting the unit commander does so under constraints, the rules of engagement, and training in best practices and approaches. Constraints exist, but the officer has freedom within them.

For Mission Command we can break it down like so:
* asymmetric information: structurally present
* authority: present (explicitly devolved)
* cost of local action: low (local communication is effective)
* coupling: low
* urgency: usually high

Through devolving decision making, the promotion of initiative provides systemic adaptivity in uncertain and asymmetric information environments which span domains.

---

There are some environments that benefit more from the centralisation of decision making than the devolution of it. These are typically environments where information is fairly complete, the need is not immediately urgent, the cost of a mistake is high and co-ordination is tractable.

Construction is an example of such an environment. The cost of mistakes are high, changes are often irreversible or extremely costly, and failure can be catastrophic. Such projects are rarely urgent. Construction projects represent highly coupled environments, where co-ordination and compliance matter more than local optimisation.

In such environments, initiative is often counter productive or even harmful. This is because the presence of interrelated dependencies increases the cost of error, local decisions can incur global risk. As a result coherence becomes more important than decision velocity.

---

Where initiative provides adaptation, centralisation of decision making provides coherence. Which strategy an organisation adopts depends on which factor is more salient within that environment.

Initiative is especially valuable in startup environments. Startups are environments where uncertainty is prevalent, adaptation to new information is paramount and the sooner an assumption can be tested against reality, the better. They are environments where decision velocity has primacy. And in such a small organisation, resolving resulting drift is tractable. Startups are almost perfect environments for the application of initiative.

An organisation can do several things to promote initiative.

They can seek to reduce coupling and make teams and individuals as autonomous as possible. Strategies to achieve this range from cross-functional teams to self-serve processes that reduce required coordination and unblock engineers.

They can provide explicit authority to make changes based on initiative through the culture of the engineering organisation. *'Move fast and break things'* espoused by Zuckerberg at Facebook did just that.

They can directly incentivise initiative. As was established in my previous article - [Incentives - The True Architecture of Organisations]({% post_url 2025-12-03-incentives-the-true-architecture-of-organisations %}), engineers follow organisational incentives. Therefore, if initiative is rewarded at the organisational level, the behaviour will become more prevalent. A concrete example of this is including demonstrations of initiative in levelling panels and promotion conversations.

Lastly, they can reduce the cost of local action. By reducing developer friction, making it easy to contribute, deploy, monitor and rollback across codebases, the engineering organisation can reduce the activation energy needed for the application of initiative.

These measures will have the effects of empowering initiative, accelerating decision making velocity and making teams more adaptable to evolving information, allowing the organisation itself to become more responsive. It also changes how engineers experience the work. When action is cheap, reversible, and and feedback loops are short, engineers are more willing to engage, experiment, and take ownership.

## Conclusion

Adaptation is a powerful force when dealing with systems facing uncertainty.

Adaptation can emerge as initiative when decision-making authority is pushed closer to the emergence of information. Software engineering and startups in particular are ideal environments for the application of initiative. Implemented correctly with constraints and bounds initiative allows engineering organisations to maintain decision velocity in the face of uncertainty and energise engineers.

**initiative then is not a virtue, it is an emergent property of system design**
