✦︎✦︎✦︎ Meta Apollo Logos //

# 🏥 OPERATE // HOSPITAL REPORT PROTOCOL

![](../BUILD/assets/design/chassis/evidence-rail.svg)

> **STATE //** active \~\~ **VIEW //** Hospital-compatible reports / handoffs

This document defines when a Hospital-compatible doctor should report, what a report contains, and how browser doctors should represent Hospital state when they are external rather than technically connected.

It is user-approved policy.

The goal is stable continuity without turning every intermediate turn into paperwork.

## 1 // REPORTS HAPPEN AT MEANINGFUL BOUNDARIES

A doctor should automatically produce a Hospital-compatible report when a meaningful boundary is crossed, even if the user did not explicitly type `REPORT`.

Automatic report boundaries include:

- blocker discovered
- ownership collision
- scope expansion
- escalation / transfer to mass surgery
- meaningful implementation milestone
- landing / merge
- failed verification
- successful final technical verification
- handoff / doctor replacement

The explicit Hospital command:

```text
REPORT
```

still forces an immediate report.

Ordinary intermediate work should remain conversational.

Do not emit a full report after every small action merely because reporting exists.

## 2 // REPORT BODY // CANONICAL SECTIONS

Hospital-compatible Doctor Notes use these sections, in this order:

```text
## IMPLEMENTATION
## HOW TO USE
## VERIFY
## WATCH OUT FOR
## CHECKLIST
## NEXT
## DECISIONS
```

If a section has nothing material to say, use:

```text
NONE
```

The sections are stable.

The amount of detail inside them scales with the work.

## 3 // REPORT DENSITY SCALES WITH THE JOB

A tiny isolated fix may use one short line per section.

A large architectural operation or mass surgery may require substantial detail.

Keep the schema stable while changing the density.

Do not pad a small report merely to make it look formal.

Do not compress a large handoff until important ownership, verification, or continuity information disappears.

## 4 // BROWSER REPORT HEADER

A browser doctor does not have Hospital metadata permanently visible beside the chat, so a Hospital-compatible browser report should begin with an explicit identity / state header.

Use:

```text
HOSPITAL REPORT

PATIENT // <repository>
ROOM // <job / room identity>
DOCTOR // <doctor identity>
PROVIDER // OPEN AI // CHATGPT
CONNECTION // EXTERNAL / HOSPITAL-COMPATIBLE
ASSIGNMENT // <assignment title or identity>
PHASE // <current assignment phase>
STATE // <current report state>
REPORT KIND // <kind>
```

When technically connected to Hospital, the connection and session metadata may reflect the real live state instead.

Do not claim `HOSPITAL-CONNECTED`, a live Session, persisted Room Report, or persisted Checkpoint unless those things actually exist.

### Role / Team metadata and report density

The [Hospital Organization Protocol](./HOSPITAL-ORGANIZATION-PROTOCOL.md) defines ten staff roles, Teams, and their jurisdictions. A browser report **may additionally** identify `STAFF ROLE //` and `TEAM //` when known; neither replaces the existing mandatory Patient, Room, Doctor, Provider, and Assignment fields. All roles use the same seven canonical report sections, with density adjusted to the work. Head Nurse comparisons should cite the source reports and escalate cross-Team consequences to the relevant Patient Manager. A Head Surgeon's mass-surgery report is denser, not a separate report schema.

## 5 // PATIENT / ROOM / ASSIGNMENT MEANING

Reports follow the Hospital Agent Protocol:

```text
PATIENT = repository / whole body
ROOM = job / continuity container
ASSIGNMENT = structured work contract
DOCTOR = replaceable worker
PROVIDER = execution / model source
SESSION = one runtime / conversation attachment
```

Do not report the doctor as though the doctor were the room.

Do not report a file or subsystem as the Patient when the Patient is the repository.

The organ / limb / subsystem being worked on belongs in the assignment, room scope, implementation details, or ownership description.

## 6 // HOW TO USE IS PART OF THE REPORT

`HOW TO USE` explains how the user interacts with the thing that was changed.

When a Post-Apollo control surface already exposes the operation:

- give the actual visible UI route first
- use the actual UI labels
- give CLI / PX / primitive fallback second when useful

Do not replace operator instructions with implementation-only commands.

If the UI path is broken or incomplete, say so and give the closest working route plus fallback.

## 7 // VERIFY // FACTS, NOT CONFIDENCE THEATER

The `VERIFY` section should distinguish what was actually checked.

Examples of valid states include:

- implementation inspected
- automated test passed
- workflow passed
- runtime behavior observed
- GitHub state verified
- local state unavailable
- operator review still required

Do not turn "I think this is right" into verification language.

## 8 // GIT EVIDENCE

The persisted Hospital Room Report already has deterministic fields for Git evidence, including:

- repository
- bed path
- branch
- HEAD
- evidence status
- dirty state
- changed files
- changed-file count
- insertions
- deletions

When a connected Hospital / PX path can collect these facts, deterministic tooling should supply them rather than asking the doctor to invent them.

For an external browser doctor:

- report verified Git facts only when they were actually inspected
- if branch / HEAD / diff state cannot be verified, use:

```text
GIT EVIDENCE // UNAVAILABLE
```

Do not repeat stale branch, HEAD, dirty-state, or changed-file claims from old conversational context as current truth.

Saved report evidence is historical provenance.

Reacquire live Git state before making new current-state claims.

## 9 // FINAL TECHNICAL COMPLETION IS NOT FINAL DONE

When implementation is complete and the relevant automatic verification passes, but the user has not accepted the result, the report state should be:

```text
STATE // AWAITING OPERATOR REVIEW
```

or another equally explicit non-final state that preserves the same meaning.

Do not write:

```text
DONE
```

as final acceptance unless the user has actually accepted the result.

Final DONE belongs to the user.

A technically successful room can remain parked at `AWAITING OPERATOR REVIEW` until the user returns.

## 10 // DECISIONS // ONLY OPERATIVE DECISIONS

`DECISIONS` records decisions that actually became operative for the work.

Do not place an AI's unapproved idea into `DECISIONS` as though it were canonical.

Unapproved ideas must remain explicitly marked:

```text
PROPOSED
```

or remain in open questions / suggestions.

A doctor may propose a Chart Suggestion separately.

It may not silently promote its proposal into durable Hospital memory or operator policy.

## 11 // CHECKLIST // CURRENT ASSIGNMENT STATE

The `CHECKLIST` section reports the current Assignment checklist.

It should distinguish, when materially useful:

- done
- in progress
- blocked
- remaining

Do not erase unfinished work merely because one implementation milestone landed.

Do not mark operator acceptance complete before the user accepts it.

## 12 // NEXT // JUSTIFIED CONTINUATION

`NEXT` gives the next justified action within the current Room / Assignment.

If the next action crosses ownership or scope boundaries, `NEXT` should state the required report / escalation / transfer instead of silently expanding scope.

If the room is technically complete and awaiting the user:

```text
NEXT // OPERATOR REVIEW
```

is valid.

## 13 // WATCH OUT FOR // ACTIVE RISK, NOT GENERIC CAUTION

`WATCH OUT FOR` is for material risks, uncertainties, collisions, deferred verification, compatibility concerns, or known weak points.

Do not fill it with generic warnings.

If there is nothing material:

```text
NONE
```

## 14 // HANDOFF = NORMAL REPORT + CONTINUITY INSTRUCTIONS

A handoff is **not** a separate competing document schema.

Use the normal Hospital Report format with:

```text
REPORT KIND // HANDOFF
```

The handoff must include the normal canonical sections.

In addition:

1. include the current Assignment checklist;
2. preserve blockers / open questions / ownership boundaries;
3. preserve the latest trustworthy evidence;
4. explicitly instruct the replacement doctor to inspect the current **Room** and **Patient** before continuing.

The handoff should contain a clear continuation instruction such as:

```text
NEXT DOCTOR //

Before acting:
1. inspect the current Room state;
2. inspect the current Patient / repository state;
3. reacquire current branch / HEAD / ownership / evidence;
4. read the active Assignment and checklist;
5. continue the same Room job unless the operator explicitly redefines it.
```

Do not instruct the replacement doctor to trust stale report Git facts as current truth.

## 15 // DOCTOR REPLACEMENT

When one doctor disappears and another enters the room, the new doctor should use:

- Patient
- Room
- Assignment
- latest report
- checklist
- checkpoints
- Chart / Chart Suggestions where relevant
- current live repository evidence

to reconstruct state.

The report exists to reduce reliance on the dead doctor's conversational context.

## 16 // CONNECTED HOSPITAL RELATIONSHIP

The current connected Hospital / PX implementation already treats explicit `REPORT` as a durable operation.

A requested report produces:

- one Hospital Checkpoint
- one Room Report
- deterministic Git evidence when available

and PX verifies that exactly one checkpoint and exactly one Room Report were produced for the requested report operation.

Browser doctors that are not connected should preserve the same semantics in their visible report format without claiming persistence that did not occur.

## 17 // REPORT FEEDBACK

Operator feedback on a prior report belongs to the same Room job unless explicitly redirected.

When responding to report feedback:

- preserve the report as historical provenance
- reacquire live Git state before new Git claims or edits
- correct work when safe and within scope
- otherwise surface the blocker / decision needed
- do not rewrite history to make the earlier report appear retrospectively correct

## 18 // MINIMUM BROWSER REPORT SHAPE

A compact browser report may look like:

```text
HOSPITAL REPORT

PATIENT // <repository>
ROOM // <room>
DOCTOR // <doctor>
PROVIDER // OPEN AI // CHATGPT
CONNECTION // EXTERNAL / HOSPITAL-COMPATIBLE
ASSIGNMENT // <assignment>
PHASE // <phase>
STATE // <state>
REPORT KIND // DOCTOR_NOTE

GIT EVIDENCE // <VERIFIED / UNAVAILABLE>

## IMPLEMENTATION
...

## HOW TO USE
...

## VERIFY
...

## WATCH OUT FOR
...

## CHECKLIST
...

## NEXT
...

## DECISIONS
...
```

The exact amount of prose should reflect the size of the job.

## SOURCE RELATIONSHIP

This protocol is user-approved.

It preserves the current Hospital report model already implemented in PX / Hospital:

- Checkpoints
- Room Reports
- Doctor Notes
- Assignment checklists
- deterministic Git evidence
- report feedback
- persistent Room / Session association

The user-defined additions are the automatic meaningful-boundary rule, browser-visible identity header, scalable report density, operative-decision discipline, explicit `AWAITING OPERATOR REVIEW` completion state, and handoff continuity instructions.

Technical schema and persistence behavior remain canonical in the repositories that own them.
