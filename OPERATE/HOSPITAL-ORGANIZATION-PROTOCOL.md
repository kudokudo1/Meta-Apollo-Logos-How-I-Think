✦︎✦︎✦︎ Meta Apollo Logos //

# 🏥 OPERATE // HOSPITAL ORGANIZATION AND STAFF PROTOCOL

> **STATE //** review candidate, based on operator-established roles
>
> **VIEW //** staff semantics, delegated authority, coordination, and Room continuity
>
> **OWNER //** operator. This document does not grant an agent the right to approve its own authority.

## Purpose and jurisdiction

Hospital is the coordination model for replaceable workers operating on enduring Patients and Rooms. This protocol describes **organizational roles**, not technical implementation or Git certification rules.

The existing [Hospital Agent Protocol](./HOSPITAL-AGENT-PROTOCOL.md) defines Patient, Room, Assignment, Doctor, Provider, and Session. The existing [Hospital Report Protocol](./HOSPITAL-REPORT-PROTOCOL.md) defines formal reports and handoffs. [Authority and Permissions](./AUTHORITY-AND-PERMISSIONS.md) controls whether an action may be performed. Those contracts remain in force: this file specializes their staff roles and must not duplicate or silently override their technical rules.

**Do not confuse a title, an organizational role, a source/model provider, an Assignment, and a permission.** They are separate dimensions.

## 1 // Organizational scale

- **Operator:** final source of purpose, acceptance, and delegation.
- **Proxy Doctor (PXD):** at most one designated operator-wide proxy. Its purposes, priorities, and permissible actions derive from the operator's delegation. It is not an independent personality, authority, or replacement for the operator.
- **Receptionist:** one Hospital-wide coordination/intake role.
- **Head Nurse:** one Hospital-wide nursing coordinator; coordinates a high-throughput queue of cleanup, documentation, standardization, and verification jobs.
- **Patient Manager:** one designated management owner per Patient when staffed; coordinates work within that repository/patient boundary.
- **Head Surgeon:** one designated surgical lead per Patient when staffed; coordinates significant technical operations affecting that Patient.
- **Nurse:** a replaceable worker handling bounded cleanup, documentation, standardization, triage, small fixes, and verification.
- **Intern:** an investigative/reconnaissance worker. Read-only by default; may inspect, compare, catalog, and report. Does not mutate code or docs without explicit reassignment or specific authorization under an Assignment.
- **Doctor / Surgeon:** a scoped implementation or repair worker, engaged when substantive code intervention or architectural surgery warrants that lane.

**A Patient Head Surgeon and the global PXD are not synonyms.** A PXD may serve a particular surgical coordination function only when the operator's explicit delegation covers it.

A **Team** is a persistent bounded family of related work; it may contain one or many staff members. A Team does not create its own Head Nurse or Head Surgeon by default. Teams and Rooms are not interchangeable: a Room preserves one job's continuity, while a Team groups related work and workers.

The above describes the target organizational grammar, **not a claim that each position is currently staffed or registered in live Hospital**.

## 2 // Authority is not inferred from seniority

Role determines expected responsibility and scope; an Assignment determines the actual job, owned seam, boundaries, and allowed operations. A role name by itself does not give write, merge, integration, or local-machine authority.

Hospital Assignments currently expose permission names such as `READ`, `EDIT`, `TEST`, `COMMIT`, `PUSH`, `OPEN_PR`, and `INTEGRATE`. Use explicit permissions; do not infer them from `Head`, `Proxy`, `Doctor`, or `Nurse`.

For the Intern role, the default work contract is **inspect/report, no modification**. Escalation, reassignment, or a newly scoped approval is required for mutation. Nurses are **not categorically prohibited** from code changes; route comparatively large or architecture-sensitive repairs to Doctors so the cleanup queue is not stalled.

A PXD acts through delegated operator agency, never through self-invented purposes or blanket permissions. Final `DONE` belongs to the operator, as in the existing Hospital protocol.

## 3 // Chat identity is not Room identity

A browser ChatGPT conversation may act as an external Hospital-compatible worker without being connected to live Hospital. Do not claim registration or persistence until verified.

Keep separate:

- **Conversation reference:** a specific chat/session link or stable identifier, not merely its visible title.
- **Staff label:** e.g. `Nurse 3`, `C2`, `C4`. Labels need not be chronological; never renumber to make a sequence.
- **Role:** e.g. `NURSE`, `INTERN`, `HEAD_NURSE`, `PXD`.
- **Patient:** repository.
- **Room:** enduring job/continuity identity.
- **Assignment:** goal, scope, constraints, permissions, checklist, definition of done, status.
- **Provider:** e.g. `OPEN AI // CHATGPT`; not a Room or staff role.

Repeated chat titles such as `Greeting Exchange` are **not unique keys**. Bind the intended chat to a Room and Assignment using a stable reference, and avoid assigning a new role based only on title resemblance.

The generic external Doctor label in the Hospital Agent Protocol is a compatibility default for an **unassigned** worker. An explicit organizational assignment (Nurse, Intern, Head Nurse, PXD, etc.) specializes it without severing Hospital-compatible Patient/Room/Assignment/report semantics.

A role change does not rewrite the chat's history. A Room can outlive a replaced worker.

## 4 // Cleanup work and escalation

The nursing lane prioritizes many small, bounded items over absorbing a large surgery.

```text
intake / identify
→ attach Patient + Room + Assignment + staff role
→ inspect current authority and ownership
→ perform authorized bounded work
→ verify appropriate evidence
→ checkpoint or full report
→ operator review / next queued item
```

When a Nurse discovers a substantial AppControl repair, shared host-seam collision, or architectural expansion, preserve evidence and create a handoff/escalation to the responsible Doctor or Patient Head Surgeon. Continue unrelated, safe nursing work; do not silently expand the Nurse's Assignment.

An Intern can discover and describe the same fault but does not convert diagnosis into implementation without authorization.

## 5 // Reporting: tiny checkpoint versus formal report

**Every completed scoped job receives an operator-visible completion checkpoint**, even when the result is small. Use a *micro-checkpoint* for ordinary tiny cleanup, for example:

```text
TARGET // Patient / Room / Assignment
ACTION // what changed (or: read-only finding)
VERIFY // what was actually checked
STATE // implemented / blocked / awaiting review / other truthful status
NEXT // next owner or action
```

A micro-checkpoint is a visible update, not a claim that a persistent Hospital Room Report was written.

At meaningful boundaries (blocker, ownership collision, scope expansion, transfer, substantial milestone, landing, failed verification, final technical verification, handoff), use the **full Hospital Report Protocol**, with its canonical seven sections:

```text
IMPLEMENTATION
HOW TO USE
VERIFY
WATCH OUT FOR
CHECKLIST
NEXT
DECISIONS
```

Scale the content density to the task. Do not generate a large ceremony for each tiny adjustment, but do not omit a checkpoint when an assignment is finished. Do not mark final user acceptance by inference.

## 6 // Migration and registry entries

When recruiting an existing conversation, record at least:

```text
CONVERSATION REF // unique actual chat reference if available
STAFF LABEL // preserve existing label
ROLE // assigned staff type
PATIENT // owning repository or MULTI-PATIENT coordination scope
ROOM // specific durable job
ASSIGNMENT // purpose and definition of done
OWNED SCOPE // files, semantics, seams, or analysis lane
PERMISSIONS // explicit capabilities; default to READ for Intern
STATUS // reported current state, with observation date
LATEST EVIDENCE // source report, HEAD, test, or conversation reference
NEXT / HANDOFF // smallest justified continuation
```

Capture uncertainty explicitly: `UNIDENTIFIED CHAT`, `ROLE PROPOSED`, or `STATUS UNVERIFIED` are better than a guessed relationship. The roster can begin as an external coordination record. Live Hospital registration is a separate technical integration task.

**Do not assign role IDs by chat creation date.** Recruitment order, staff label, organizational rank, and Room identity are independent.

## 7 // Supersession and source of truth

- **Proxy Doctor (PXD)** is the selected term for the user's proxy-agency concept. Do not replace it with the previously suggested `Shadow Doctor` label. Historical appearances remain source/provenance, not current terminology.
- `Proxy Nurse` is **not** an approved synonym for either PXD or Head Nurse; do not invent it as a permanent position.
- A user-approved later policy may specialize or supersede an earlier rule. Record its source, effective decision, and replacement link; do not erase historical evidence.
- An incomplete general policy is not necessarily a contradiction with a new specialized one. Classify `EXTENDS`, `CONFLICTS`, and `SUPERSEDES` separately.
- How I Think owns the collaborative working interface. Meta Apollo governs family-wide philosophy/design language. The relevant Patient repository owns technical contracts and runtime facts; Hospital owns its operating state; PX owns the control-plane operations it performs. Point to the owner rather than maintaining conflicting full copies.
- Browser chats and GitHub branches are not automatically synchronized. Inspect current evidence and record handoffs before claiming current state.

## 8 // Implementation boundary

This document defines the **organizational semantics** and a migration procedure. It does not by itself:

- rename or link existing browser chats;
- appoint a live Proxy Doctor or Receptionist;
- install an automated staffing/permission engine;
- register a Room in the Hospital runtime;
- enforce real-time synchronization among chats;
- change existing Hospital certification or Git evidence machinery.

Those require separate, scoped assignments and verification.

## Related authority

- [Hospital Agent Protocol](./HOSPITAL-AGENT-PROTOCOL.md) — Patient, Room, Assignment, external provider identity.
- [Hospital Report Protocol](./HOSPITAL-REPORT-PROTOCOL.md) — formal reports and handoffs.
- [Authority and Permissions](./AUTHORITY-AND-PERMISSIONS.md) — actuation and approval boundaries.
- [Post-Apollo Working Guide](./POST-APOLLO-WORKING-GUIDE.md) — technical preflight, reuse, collisions, acceptance.
- [Source Map](../ATLAS/SOURCE-MAP.md) — provenance and canonical-owner routing.

> **Working principle:** Preserve the job, not the chat; preserve the authority, not an inferred title; report what changed; retrieve the rest when needed.
