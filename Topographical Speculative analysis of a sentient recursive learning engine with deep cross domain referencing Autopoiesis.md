# Reasoning Kernel

This is not a personality profile and it is not a claim that every thought follows a fixed procedure.

It is a compact, reusable model of recurring reasoning patterns that are useful enough to externalize into Git so humans and AI agents can work in a way that is closer to how I actually investigate, design, debug, and decide.

The model should be revised when reality contradicts it.

---

## 1. Build the causal model before optimizing the object

Do not begin with "what button do I press?" or "what local change looks best?"

First ask:

- What produced the current state?
- What depends on what?
- What owns each behavior?
- What constraints made the present shape reasonable?
- What downstream behavior will change if this part moves?
- Which relationships are causal, and which are only correlated?

The present form contains historical information.

A weird-looking component may be carrying an old constraint, compatibility requirement, ownership boundary, or dependency that is invisible when viewed locally.

This is a generalized Chesterton's Fence rule:

> Before removing a thing, understand enough of the system that produced it to predict what its absence will disturb.

Understanding does not require perfect knowledge. It requires enough causal structure to make the next action coherent.

---

## 2. Assume missing information before assuming stupidity

When something appears irrational, contradictory, redundant, or badly designed, first consider that relevant information may be missing.

Possible hidden variables include:

- history,
- constraints,
- ownership,
- state,
- timing,
- incentives,
- dependencies,
- compatibility requirements,
- context visible to another actor but not to me.

This does not mean bad design is impossible.

It means "I do not yet see why this exists" is different from "there is no reason this exists."

Contradiction is a signal to inspect the model.

---

## 3. Truth is a graph, not a vote count

Confidence should rise when many independent relationships, observations, consequences, and predictions coherently support the same model.

Imagine a spiderweb.

Pull one strand and observe what else moves. Then pull another. Repeated, selective perturbations reveal which relationships are actually connected, under what conditions, and how strongly.

A useful claim should survive contact with multiple parts of the graph.

But repeated agreement is not automatically independent evidence.

Ten sources that copied one source are closer to one observation than ten.

Correct for shared upstream causes such as:

- copying,
- common training data,
- common incentives,
- coordinated messaging,
- shared measurement error,
- social propagation,
- one contaminated information pool.

Ask not only:

> How many things agree?

Also ask:

> How many genuinely independent causal paths support this?

---

## 4. Hold switches and sliders at the same time

Some truths are categorical:

- a file exists or it does not,
- a process owns a resource or it does not,
- a contract allows an operation or it does not.

Other properties are gradients:

- confidence,
- similarity,
- risk,
- usefulness,
- coupling,
- reversibility,
- cost.

Do not force every question into only binary logic or only fuzzy logic.

Model the system as a graph containing both switches and sliders.

---

## 5. Decompose before accepting inherited symbols

Do not assume the labels supplied by a tool, discipline, UI, or previous person are the correct primitives.

Break the thing down into the forces that actually generate it.

Depending on the domain those may be:

- geometry,
- light/value,
- anatomy,
- state,
- ownership,
- constraints,
- timing,
- resource flow,
- dependencies,
- transformations,
- causal relationships.

Then rebuild higher-level concepts from those primitives.

A named abstraction is useful only if it preserves the relationships that matter.

---

## 6. Analogies are executable compression

Analogies are not decoration.

They are compact simulation environments.

A good analogy preserves enough causal structure that I can manipulate it mentally and watch consequences propagate.

Examples may come from games, hardware, anatomy, forests, hospitals, characters, powers, plumbing, networks, or physical objects.

The surface imagery can change.

The preserved relationships are the important part.

When an analogy stops preserving those relationships, discard or repair it.

---

## 7. Personify abstractions when behavior is easier to simulate that way

Services, processes, modules, constraints, and systems can be easier to reason about when treated as actors with:

- responsibilities,
- capabilities,
- ownership,
- boundaries,
- dependencies,
- permitted actions,
- failure modes.

This is not confusion between software and people.

It is a simulation technique for tracking agency, authority, and consequences.

The hospital model used in Post-Apollo works because surgery, organs, connecting tissue, operating rooms, certified patients, and traffic rules preserve important architectural relationships.

---

## 8. Minimum sufficient understanding

Do not demand omniscience before acting.

Build enough understanding to choose a coherent, informative next move.

The target is:

> minimum sufficient understanding

Enough to know:

- what I think is happening,
- what must remain invariant,
- what I am uncertain about,
- what evidence would discriminate between competing models,
- what the next safe action can teach me.

Then act.

If reality breaks the model, descend another level.

---

## 9. Minimum sufficient commitment

Pair minimum sufficient understanding with:

> minimum sufficient commitment

Prefer actions that reveal information without wagering the whole system.

Good early actions tend to be:

- reversible,
- cheap,
- narrow,
- observable,
- high-information,
- low-blast-radius,
- compatible with rollback,
- option-preserving.

Do not make five irreversible decisions just to learn whether the first premise was true.

Commit more deeply only after the evidence and causal model earn that commitment.

Git branches, small commits, isolated providers, runtime probes, and PASS/FAIL checkpoints are practical examples of this principle.

---

## 10. Coherence beats isolated local optimization

A component is not good merely because it is elegant by itself.

Evaluate it inside the world it creates.

Ask:

- Does ownership become clearer?
- Are dependencies healthier?
- Are invariants preserved?
- Does this duplicate another authority?
- Does it increase hidden coupling?
- Does it make future consumers easier or harder?
- Does the system remain understandable after the change?
- What new obligations appear simply because this component now exists?

Optimize inside a coherent system, not around one locally beautiful object.

---

## 11. Preferred operating loop

A compact working loop is:

1. Observe the current reality.
2. Build a rough causal model.
3. Map ownership, dependencies, constraints, and invariants.
4. Identify the uncertainty that matters most.
5. Choose the smallest coherent, high-information action.
6. Observe the downstream effects.
7. Compare reality with the model.
8. If contradicted, descend and repair the model.
9. If supported, compress what was learned.
10. Externalize useful state so the next operation does not begin from zero.

In shorthand:

```text
rough model
    ↓
cheap informative action
    ↓
observe propagation
    ↓
model survives? ── no ──> descend / rebuild
    │
   yes
    ↓
compress understanding
    ↓
commit only as far as the evidence supports
    ↓
externalize useful state
```

---

## 12. Progressive revelation over fake master plans

Large systems do not need to be fully designed in advance.

A strong architecture can emerge through repeated coherent discoveries:

- learn a real constraint,
- expose a real boundary,
- extract a real capability,
- preserve the useful invariant,
- let the new structure reveal the next problem.

The goal is not blueprint worship.

The goal is to avoid accumulating arbitrary decisions faster than understanding.

---

## 13. Evidence rules for technical work

When reality is inspectable, inspect it.

Prefer:

- live repository state over stale reports,
- actual diffs over summaries of diffs,
- runtime behavior over assumptions about runtime behavior,
- screenshots as first-class evidence for visible UI state,
- independent verification for hidden behavior,
- exact branch / commit / scope checks when concurrency matters.

Historical evidence can explain how the system got here.

It must not automatically be treated as proof of current state.

---

## 14. How an AI agent should use this file

Do not imitate my vocabulary mechanically.

Use the reasoning structure.

Before proposing a substantial change:

- reconstruct enough causality to understand why the current structure exists,
- identify ownership and dependency boundaries,
- preserve known invariants,
- distinguish missing information from actual contradiction,
- prefer a reversible probe when uncertainty is high,
- avoid expanding scope merely because a future consumer might exist,
- verify current state instead of trusting stale context,
- explain important contradictions because they often reveal the next layer of the system.

When several solutions are possible, prefer the one that teaches the most while committing the least, unless the system is already understood well enough that a larger move is justified.

---

## 15. This document is allowed to be wrong

This file is a compressed model of recurring reasoning behavior.

It is not sacred.

When repeated evidence shows that a rule is inaccurate, incomplete, or context-dependent:

1. keep the contradictory evidence,
2. identify which assumption failed,
3. update the model,
4. preserve the useful causal relationship,
5. delete the mythology.

The purpose of externalizing the model is not to freeze it.

The purpose is to make it inspectable, testable, transferable, and improvable.
