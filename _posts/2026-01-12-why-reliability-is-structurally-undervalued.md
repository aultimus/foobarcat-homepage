---
layout: post
title: "Why Reliability Is Structurally Undervalued"
date: 2026-01-12
---

Reliability is often framed as a problem to be solved with more discipline, better processes, tooling, or people. Yet reliability failures often occur in organisations with capable engineers, reasonable tooling, adequate process, and stated commitments to quality. This is because, persistent reliability failures are frequently attributable to structural causes, emerging from the incentive architecture of the organisation. As a result,  reliability is frequently structurally undervalued. In contrast, other behaviours — speed, visibility, delivery — are rewarded more consistently.

Reliability work, whilst widely recognised as essential, has the defining property that its successes are largely invisible. Consider goalkeeping in football, which shares this property. In football, goals prevented don’t appear on the scoreboard, while goals scored do. Organisations that optimise for visible progress naturally overweight the observable and underweight the preventative work.

> _Attack wins you games, but defence wins you titles._ — Alex Ferguson

The best teams resolve this not by choosing defence over attack, but by defending in depth, that is, diffusing defensive responsibility across the whole team. With this strategy applied to reliability, reliability stops being a specialised activity and becomes a shared property of the system — even the teams focused on delivery contribute to its defensive posture.

---

The same pattern appears across preventative work from football to fitness. Preventative work shares these common structural properties:

- Success is invisible
- Attribution is weak
- Costs are immediate
- Benefits are delayed

When prevention works nothing happens, success is quiet and responsibility is vague. 
Costs are paid up front and the benefits are amortised over the long term.

As a result, systems reliably drift toward reactive behaviour — regardless of intent or competence.

---

As I discussed in my previous essay — 
[Incentives: The True Architecture of Organisations]({% post_url 2025-12-03-incentives-the-true-architecture-of-organisations %}) — engineers will respond rationally to what is systematically rewarded by the organisation in which they inhabit.

In most organisations the actions rewarded by the local incentive structure dominate. Feature delivery, execution speed and short-term wins — the markers of visible impact have primacy.

Additionally, organisations frequently celebrate firefighting, late-night saves, and emergency fixes. This high-visibility work can feel like reliability, but it is fundamentally reactive rather than preventative.

When heroics are mythologised, prevention is demoted from a continuous responsibility to an episodic concern, triggered by failure rather than embedded by default.

---

Many organisations attempt to centre reliability through structural intervention, but these efforts often fail because they introduce new functions with misaligned incentives.

One example is assigning incident ownership to the team closest to user impact, rather than the team whose service failed. This is usually justified on the grounds that the user-facing team best understands customer-facing consequences. While this can simplify communication, it separates accountability from causality. Teams become responsible for failures they cannot directly fix, while the teams that introduced the risk experience weaker pressure from the incident. Over time, this shifts postmortems and incidents toward documentation and compliance rather than resolution.

A similar pattern appears in the emergence of DevOps teams as dedicated operations teams. DevOps was never intended to be a separate function that “does operations for developers”. Its original insight was that the people who build systems should be involved in running them, because that is how feedback loops stay tight and incentives stay aligned. When organisations create DevOps teams that absorb operational responsibility, they often recreate the original problem under a new name: developers optimise for delivery, Ops lives with the consequences, and reliability becomes a negotiation rather than a property of the system. In that sense, DevOps is not a function — it is what happens when ownership of code and ownership of outcomes are held together, and incentives are aligned.

---

Reliability, mandated into existence via process will only ever be fragile at best. To be durable, it has to be the cheapest long-term strategy available to the people closest to the system. This way reliability is structurally assured. Processes like post-mortems, reviews and best practices help, but they are not sufficient, they do not substitute for ownership and the aligning of incentives.

Reliability improves markedly when the people who deploy a system also live with its failure modes. Meanwhile, when accountability is diffuse and failure is externalised, reliability suffers. When the coupling is broken, reliability work becomes episodic by design. It is ownership of outcomes that creates the structural conditions for the promotion of reliability.

---

In most organisations, reliability work is structurally under-valued due to a tendency to optimise for more legible signs of value creation. This means that reliability failures are inherent to organisational design, not moral or competence based.

Ownership acts as a stabilising force against this drift. When the people who shape a system also live with its failure modes, preventative work stops being abstract and becomes an everyday concern. The cost of fragility is no longer deferred or externalised, and reliability ceases to rely on exhortation or heroics.

Without durable, local ownership of outcomes, no amount of process or tooling can make reliability stick. With it, reliability emerges naturally as a property of the system rather than a periodic intervention.

This leads to a more salient question than whether an organisation “values reliability”:

**who actually owns the outcome when systems fail?**
