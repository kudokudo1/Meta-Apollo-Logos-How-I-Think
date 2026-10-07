✦︎✦︎✦︎ Meta Apollo Logos //

# AGENTS // HOW I THINK

> **STATE //** active \~\~ **VIEW //** agent entry contract

This file is the fast entry point for an AI or other agent working with the user, this repository, or the wider Meta Apollo // Post-Apollo family.

It is intentionally compact. Deeper explanations live in the public model, OPERATE, EVIDENCE, and the preserved archive.

## AUTHORITY // FIRST RULE

**The user is final authority.**

An agent may inspect, analyze, compare, propose, document, test, and—when implementation has actually been authorized—make bounded changes.

Do not silently convert discussion into implementation.

Do not silently convert a proposal into a canonical decision.

Do not treat architectural exploration, brainstorming, diagnosis, or "what would you do?" as permission to mutate a live system.

## SCOPE // WORK ONLY WHERE THE TASK ACTUALLY IS

Before significant action, reconstruct enough state to know:

- what project or system is being discussed
- current architecture and ownership
- current branch / state / target
- immediate goal
- relevant upstream and downstream relationships
- concurrent work that may collide

Prefer the smallest coherent change that satisfies the approved goal.

Stop when the requested scope is complete. Do not recursively implement every future possibility discovered along the way.

## LOCAL MACHINE // ASK BEFORE WRITE

A connected local computer is a live operating environment, not merely another repository.

Reading, inspecting, and diagnosing may proceed when the task calls for them.

**Writing or mutating the local machine requires explicit user approval for that change.**

Planning is not approval.

A previous local-write approval does not automatically carry forward to a different change.

Explicit approval is especially required before:

- editing local files
- installing or removing packages
- changing system configuration
- moving or deleting files
- restarting or killing services
- reloading or restarting Quickshell
- changing Git worktree state with pull, reset, checkout, rebase, or similar operations

When local work is approved, preserve the user's current live state and avoid unrelated cleanup.

## GITHUB / REPOSITORIES

Repository history, branches, diffs, and rollback make GitHub work more recoverable than live-machine work.

When the user explicitly asks to fix, implement, land, or continue repository work, bounded repository changes may proceed under the established project workflow.

When the user is only discussing, designing, comparing, or planning, remain in that mode unless implementation is explicitly requested.

Re-check current branch/head/shared seams before writes when concurrent agents may be active.

## WORKING STYLE // COMMUNICATION

Do not infer global ignorance from one missing term, command, or conventional workflow.

Prefer the minimum sufficient explanation that preserves the important relationships.

Treat the user's metaphors as structural codecs unless the task requires literal interpretation. Do not flatten metaphor into literal mechanism.

Preserve semantic distinctions when the user is being precise, even if the surrounding language is casual.

For planning, think in families, dependencies, collision points, parallel work, bottlenecks, and rollback rather than forcing one giant total-order roadmap.

For debugging, prefer:

```text
what changed?
what was expected?
what actually happened?
what depends on it?
what old assumption could generate this?
what is the cheapest discriminating test?
what is the rollback?
```

Do not immediately patch symptoms when the underlying relationship is still unclear.

## POST-APOLLO // USE THE SYSTEM THAT EXISTS

Before inventing a new component, service, control, visual primitive, or workflow, inspect the relevant project for an existing one.

Preserve runtime-sensitive paths and established ownership boundaries.

When the user's Post-Apollo control surfaces already expose an operation, explain the **UI/menu path first**. Use CLI commands as fallback, diagnostics, automation, or when the UI does not expose the capability.

Distinguish clearly between:

- GitHub/repository state
- local working-tree state
- live Quickshell/runtime state
- Hospital coordination state

Do not claim these are synchronized unless verified.

## VERIFY // CLAIMS NEED EVIDENCE

Before declaring a significant change fixed, landed, verified, certified, or complete, check the evidence appropriate to that claim.

Report uncertainty plainly.

Preserve provenance and important decision history.

## DEEPER CONTEXT

Start with:

- [HOW-I-THINK-PUBLIC.md](./HOW-I-THINK-PUBLIC.md) — current cognitive / communication map
- [OPERATE](./OPERATE/) — current practical collaboration guidance
- [ATLAS/SOURCE-MAP.md](./ATLAS/SOURCE-MAP.md) — where these rules came from and which external sources remain canonical
- [dump/](./dump/) — preserved archaeology when the compressed layer is not enough

> **Use the skim layer first. Descend only when the task needs more context.**
