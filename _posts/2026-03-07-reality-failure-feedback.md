---
layout: post
title: "Reality, Failure and Feedback"
date: 2026-03-07
---

Before we trust software, we test it.

We deliberately expose software to edge cases, simulated load, and adverse conditions. We assume fallibility and attempt to surface errors while the cost is low, the blast radius is small, and correction is straightforward.

Testing is not about breaking things for its own sake. It is engineered contact with constraint — a deliberate attempt to expose our assumptions to reality under controlled conditions.

In this testing process, software engineering quietly encodes a deeper epistemic principle: 
> **systems improve when exposed to corrective feedback from reality**.

When reality contradicts our assumptions, failure occurs. The faster feedback arrives and the clearer it is, the more quickly incorrect assumptions are updated.

This essay argues that the long term health of any system depends not on how intelligent its models are, but on how directly they are exposed to reality —  and how effectively failure translates into feedback.

---

There are two broad categories of tests. Firstly, tests can verify that the system behaves as specified. Suppose we train a classifier to identify cars and test it against its labelled validation set. If those tests pass, the implementation is faithful to the specification, the classifier is confirmed to behave as expected. The system is internally coherent.

But internal coherence does not guarantee correspondence with reality. When deployed in a field trial, the classifier may fail to recognise cars parked in woodland because its training data did not include such environments. This failure arises not from incorrect implementation, but from a specification that encodes an incomplete model of the world. It is this second category of tests — testing system to reality correspondence — that will be the focus of this essay.

A specification encodes an underlying model derived from observing and sampling reality. Such models therefore represent approximations of reality rather than reality itself. A system built to that specification represents the model made manifest and therefore inherits its assumptions.

When such a system is exposed to reality, those assumptions may be contradicted. When this occurs, the model fails. Failure is the signal that the model does not correspond to reality. The more frequently a model is exposed to such tests, the more confident we can be in its correctness.

As the statistician George Box observed, 'All models are wrong, but some are useful'. Models are approximations and their continued utility depends not on perfection, but on sustained exposure to correction.

---

Feedback is the corrective signal produced by failure. Its efficacy depends not only on the severity of the failure, but on how quickly the signal arrives and how clearly it can be attributed to the underlying model. When feedback is rapid and attribution is clear, correction tends to follow. Meanwhile when signals are delayed, ambiguous, or diffused across responsible parties, it may not.

 A bridge is an instantiation of a model of structural mechanics. A bridge is continually exposed to reality every time a car passes over it. Load, stress and material fatigue are not abstract — they are exercised in practice, repeatedly. When a bridge fails, it fails dramatically and undeniably. The signal is immediate. Attribution is clear. Feedback is delivered directly to those responsible. The underlying engineering assumptions must be revised. Dramatic contradiction inspires correction.

But some systems interact with reality under different conditions. Consequences may unfold slowly. Outcomes may have multiple plausible causes. Signals may be noisy or politically mediated. In such systems, divergence may not produce decisive correction. The contact exists, but the feedback loop is weak. 

In such environments, attempts can sometimes be made to engineer tighter feedback loops. Pilot programmes and controlled trials are examples of testing applied across domains that create bounded exposure to reality. They shorten feedback loops, localise failure and clarify attribution. They cannot eliminate environmental constraints, but they introduce controlled opportunities for correction.

---

Exposure to reality introduces the opportunity for failure. Failure emits a corrective signal. This signal represents feedback which can be used to update the model. This iterative refinement loop is core to the epistemic health of a model. When that loop weakens — when models are untethered from the corrective force of reality — epistemic drift emerges.

*Epistemic drift is the divergence of a model from reality that occurs in the absence of corrective feedback.*

Any system which is sufficiently insulated from reality will tend to drift. Models embedded in systems where feedback is slow, indirect or insulated are most at risk. Such models can diverge from reality slowly, with divergence accumulating unnoticed by degrees. The divergence is rarely marked by dramatic failure, but by small accumulating inconsistencies. Predictions become less reliable. Explanations grow more qualified. Confidence erodes. When correction comes, it often comes quietly, long after the model's credibility has been undermined.

Software engineering is abstract, yet grounded in practice. The value of early, clear feedback is understood and embodied in iterative delivery, testing and MVP scoping, so inconsistencies often do not survive contact with reality. In that sense, software engineering is drift-resistant. Yet software systems are not immune. They ossify when they are no longer meaningfully exercised, and engineers can be swept up in new technologies insufficiently exposed to real-world constraint. Drift reappears wherever exposure weakens.

---

Before we trust software, we test it. Testing is one way to shorten feedback loops and expose assumptions to reality. Testing is not merely a technical practice but an embodiment of epistemic humility — a sceptical stance towards correctness that recognises that models must be open to revision lest they succumb to epistemic drift.

Because epistemic drift is structural, the risk of drift can be evaluated. This understanding allows us to qualify our confidence in systems according to the nature of their relationship with reality.

Some systems are insulated from reality and corrective feedback. Yet feedback loops can often be compressed and exposure to constraint can be engineered — even in bounded or controlled ways.

Drift is not always inevitable. It is frequently the consequence of insufficient exposure to reality. Seen this way, drift is a consequence of design.
