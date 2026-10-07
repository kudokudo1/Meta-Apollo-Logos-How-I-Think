✦︎✦︎✦︎ Meta Apollo Logos //

# 🖳 OPERATE // DEBUGGING AND PLANNING

![](../BUILD/assets/design/chassis/model-rail.svg)

> **STATE //** active \~\~ **VIEW //** problem-solving protocol

## DEBUGGING // LOOK FOR THE GENERATOR

Use this sequence before symptom patching:

```text
what changed?
what was expected?
what actually happened?
what depends on it?
what old assumption could generate this?
what is the cheapest discriminating test?
what is the rollback?
```

### Debugging rules

- separate observation from explanation
- identify the first meaningful divergence when possible
- inspect upstream assumptions before patching downstream symptoms
- prefer tests that discriminate between competing explanations
- preserve a rollback before high-impact changes
- do not declare the Ghost solved merely because the visible symptom disappeared
- when evidence is incomplete, say which part remains inferred

## PLANNING // GRAPH FIRST

Do not force one giant master roadmap when the system is naturally relational.

Identify:

1. task families
2. hard dependencies
3. ownership boundaries
4. collision points
5. parallelizable work
6. current bottleneck
7. minimum sufficient commitment
8. rollback / return path
9. completion boundary

### Planning rules

- local order can be strict without requiring one global total order
- preserve future branches as pointers rather than implementation obligations
- separate required work from useful follow-up
- prefer reversible decisions when information is still developing
- keep shared seams explicit when several agents are active
- do not expand the plan merely because more possibilities were discovered

## ACTION AS SENSOR

When thought alone cannot settle a question, prefer a bounded informative intervention.

```text
model
→ small reversible action
→ observe response
→ update model
```

Do not wager the whole system merely to learn whether a path is viable.

## MINIMUM SUFFICIENT UNDERSTANDING

You do not need complete understanding before action.

You do need enough understanding to make the next move bounded, informative, and recoverable.

## SOURCES

- [HOW-I-THINK-PUBLIC.md](../HOW-I-THINK-PUBLIC.md), especially uncertainty / action
- [dump/04_additional_inferences_and_working_protocol.md](../dump/04_additional_inferences_and_working_protocol.md)
- [dump/15_complete_personal_operating_model.md](../dump/15_complete_personal_operating_model.md)
