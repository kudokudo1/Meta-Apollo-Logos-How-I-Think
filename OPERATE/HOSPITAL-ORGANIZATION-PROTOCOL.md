✦︎✦︎✦︎ Meta Apollo Logos //

# 🏥 OPERATE // HOSPITAL ORGANIZATION PROTOCOL

![](../BUILD/assets/design/chassis/agency-rail.svg)

> **STATE //** active · operator-established staff and Team definitions
>
> **VIEW //** organizational semantics, jurisdiction, delegation, continuity
>
> **OWNER //** operator. Role titles do not independently grant authority.

## PURPOSE // CONTINUITY WITHOUT MULTIPLYING CONTEXT

Hospital organizes replaceable workers across enduring repositories and jobs. This protocol preserves the operator's exact intended distinctions between staff, Teams, and jurisdictions, allowing complex work without forcing every AI to carry all of Post-Apollo's context.

This is **organizational policy**, not a claim that these roles or their automation are already registered in live Hospital. It extends [Hospital Agent Protocol](./HOSPITAL-AGENT-PROTOCOL.md) and [Hospital Report Protocol](./HOSPITAL-REPORT-PROTOCOL.md). [Authority and Permissions](./AUTHORITY-AND-PERMISSIONS.md) still governs the right to act; [Post-Apollo Working Guide](./POST-APOLLO-WORKING-GUIDE.md) still governs scope, tests, concurrent edits, and acceptance.

**Role ≠ worker identity ≠ provider ≠ Team ≠ Room ≠ Assignment ≠ permission.**

## 1 // ORGANIZATIONAL DEFINITIONS

| TERM | DEFINITION |
| --- | --- |
| **Hospital** | Shared coordination environment across repositories and workers |
| **Patient** | Repository: the enduring whole being worked on |
| **Team** | Bounded family of related tasks that need unusually close mutual coordination; has one or many members |
| **Room** | Durable identity and continuity of a particular job, surviving worker replacement |
| **Assignment** | Structured work contract inside a Room: goal, scope, permissions, checklist, completion criteria |
| **Worker** | Generic replaceable participant, independent of its assigned staff role |
| **Doctor** | Specific ordinary-work staff role; existing Agent Protocol also uses "doctor" generically for a Hospital-compatible worker |
| **Provider** | Model/agent execution source, such as ChatGPT, Codex, Hermes; not a staff rank |
| **Session** | One runtime/conversation attachment to a Room |
| **Bed** | Worktree/checkout used for development |
| **Specialist contract** | Bounded outside agent/harness work commissioned through Hospital Phone |

A Team can contain multiple Rooms. Some older Rooms were named after Teams; their names remain valid, but Room and Team **are not synonyms**. Team membership changes do not erase the Team or its Rooms.

A Team is usually scoped to one Patient or closely related subsystem, but may explicitly coordinate work involving multiple Patients. That relationship does not transfer ownership from either repository.

## 2 // STAFF DIRECTORY AND JURISDICTION

| CODE | ROLE | JURISDICTION / COUNT |
| --- | --- | --- |
| **RCP** | Receptionist | Exactly **one per Hospital** |
| **HNS** | Head Nurse | **One per Hospital preferred**; additional only when needed |
| **MGR** | Manager | **One per Patient/repository** |
| **HSG** | Head Surgeon | **One per Patient/repository** |
| **HIN** | Head Intern | Multiple; long-lived Patient/Team structural familiarity |
| **INT** | Intern | Multiple; one-off research and tiny fixes |
| **NRS** | Nurse | Multiple; cleanup, bug fixes, Meta Apollo sync, verification |
| **DOC** | Doctor | Multiple across any number of Teams; normal work |
| **PXD** | Proxy Doctor | Multiple possible; operator-directed construction, not global command |
| **SPC** | Specialist | External bounded Phone contractor; availability limited by actual agents/harnesses |

**One per Patient is a position, not a permanent worker.** A Manager or Head Surgeon can be replaced without changing Patient identity. No Team receives its own Head Nurse or Head Surgeon, though Teams may contain Nurses, Interns, Head Interns, Doctors, or Proxy Doctors. The Receptionist and Head Nurse are Hospital-wide, while Manager and Head Surgeon are Patient-specific.

## 3 // ROLE DEFINITIONS

### RECEPTIONIST // RCP

The Receptionist is Hospital's singular front desk: an AI/code-based assistant that helps the operator navigate Hospital, maintain awareness of Room/staff status, contact workers, relay user commands, and return information. GitHub Copilot is **planned** to improve repository and GitHub help; this policy does not claim Copilot is already integrated.

Reception distributes instructions **within their original authority**, never independently approves surgery or invents the user's intent. It needs to know *where* information and responsibility live, not every repository's detailed implementation.

### HEAD NURSE // HNS

The Head Nurse is a **high-frequency, context-light operational coordinator**, rather than another Patient Manager. Handles the repeatable things the Manager would otherwise have to do: send a bounded task to one Team, manage Interns, read or compare two or three reports or files, gather findings, help draft reports, check GitHub navigation, perform routine verification, approve/send routine reports, graphs and already-authorized actions, and prepare concise escalations.

She should **not** spend her context doing substantial coding or regular bug fixing. Even a tiny syntax correction is preferably delegated to an Intern or Doctor. She can perform one herself as an authorized, exceptional fallback when no worker is available or delegation would be disproportionate.

The Head Nurse **manages Interns**. If a finding has shared architectural consequences, she routes the evidence to the relevant Patient Manager instead of loading the whole system into her own context. One per Hospital is the default; additional Head Nurses are exceptional, not one per repository.

### MANAGER // MGR

The Manager is the **Patient-specific, high-context, consequential coordinator**. Performs normal work if needed, approves/sends reports, graphs, and scoped actions, verifies relevant evidence, and uses broad Patient awareness to allocate work and respond to dependencies across Teams.

Manager decisions are relatively low-frequency but high-impact. If a Team finding could disrupt Favorites or multiple other components, the Manager considers the dependency graph, integration order and affected Teams, then issues appropriate assignments. A Manager who routinely collects every tiny file or report loses the context necessary for this role; the Head Nurse handles that throughput instead.

**The Manager cannot manage Interns.** Approval of a graph/report is not automatically approval to mutate code, nor does role title supersede operator authority.

### HEAD SURGEON // HSG

There is **one Head Surgeon per Patient**, not one for all Hospital. A separate large repository—for example a Weather Station Patient—gets its own surgical lead rather than sharing the AppControl Patient's Head Surgeon.

The Head Surgeon conducts major or mass surgery and integration, receives **more relevant architectural and surgical context**, performs little or no routine research, and produces **denser reports** accounting for shared seams, verification, dependencies, and remaining risks. Research should arrive through Interns, Head Interns, Teams, or contracted Specialists.

The role is not a universal authority over unrelated Patients or protected files. Surgical integration still follows exact current Git evidence, ownership, accepted permissions, and operator review.

### HEAD INTERN // HIN

The Head Intern is a **long-lived, low-activity structural reconnaissance and succession reserve**. Occasional research and small bug fixes build familiarity with entire repositories, modules, and how they interconnect, without filling active context with a mass surgery's every turn.

Regular Interns often investigate a single issue or file; a Head Intern knows the wider body. Its purpose includes the ability to **step directly into Head Surgeon responsibility** when one disappears. It does not have to become a regular Doctor first.

This is **not** an Intern manager; that remains the Head Nurse. Knowledge may be architecturally broad but temporally stale. On succession, reacquire current Patient/Room state, reports, checklist, Git HEAD, ownership, and permissions. Appointment to Head Surgeon is explicit, not automatic, and the Head Intern's structural atlas should be recoverable outside one conversation.

### INTERN // INT

Interns perform specific, comparatively small work: one-off research, file/issue analysis, finding a bug, gathering evidence, comparing sources, or **tiny authorized fixes**. They generally need narrow task context, not a global repository map. Read-only work stays read-only; a tiny repair requires actual scoped edit permission. Interns do not manage other Interns.

### NURSE // NRS

Nurses handle maintenance: cleanup, bug fixes, Meta Apollo synchronization/consistency work, and verification. This is distinct from the Head Nurse's dispatch/report-comparison duties. If work becomes major architecture or another worker's shared seam, report and escalate rather than silently expanding scope.

### DOCTOR // DOC

Doctors perform normal implementation, repair, testing, and development under their Room Assignments. There may be many Doctors on many Teams. Their Team affiliation does not make them a Team-level Head Surgeon, Manager, or source of unbounded permissions.

### PROXY DOCTOR // PXD

**Proxy Doctor** is the operator-selected official name for a construction-oriented AI acting as an **extension of its creator's agency**. The defining relationship is:

```text
CREATOR → PROXY → CREATION
```

The creator acts indirectly through the Proxy Doctor, as through a pen, crane, or vector program—except the proxy can reason and perform complex construction. It acts **within its creator's will**. Its purpose, operating behavior, and expressed personality come from the creator's instructions, often reflecting the creator's own personality, or a persona chosen for the task; it does not independently establish a competing purpose or personality.

The Proxy Doctor is primarily used **to build rather than modify/maintain**: new programs, components, systems, prototypes or replacements. Building separately may be a useful safety mode, but isolation is **not the definition of proxy**. Construction does not authorize integration or changes to protected originals.

**Do not rename this role Shadow Doctor or redefine it as the proxy of another Doctor.** It is a proxy *of its creator*. It is not necessarily unique per Hospital or a leadership rank.

### SPECIALIST // SPC

A Specialist is an **external AI agent or harness hired/contracted through Hospital Phone** for a bounded task. Its contract identifies the originating Room, objective, scope, permissions, expected deliverables, evidence and return route.

A Specialist need not absorb the rest of Hospital's history. A connected harness may fulfill many types of work, but being contracted neither grants leadership nor allows silent scope expansion. The Specialist role and its provider are separate.

## 4 // TEAM // A RELATED WORK FAMILY, NOT A HEADCOUNT

A Team is organized by the **relatedness of tasks and dependencies**, not by how many AIs happen to be available. A one-member Team is as valid as a five-member Team; it can expand or contract without renaming its organ, Patient or purpose.

For example, Team 3 may contain T3-M, T3-R and T3-F, each with a distinct Room/assignment. The suffixes identify local members or sublanes; **they do not inherently mean Manager, Reviewer, Files, or a staff rank**. The Team record establishes their meaning.

Within a Team, members should know more about each other than unrelated workers do, because they share collisions, contracts, and dependencies. They may communicate and share reports directly rather than visiting the Manager for every small question.

Discovering another defect within the same bounded work family does not require inventing a different Team. Adding members or tasks is permitted only within the authorized scope; crossing into another Team's ownership, shared host tissue, broad architecture or another Patient requires an explicit handoff, coordination or escalation.

**Team ≠ Room. Room ≠ Doctor. A Team is not entitled to its own Head Nurse or Head Surgeon.**

## 5 // DELEGATION, REPORT FLOW, AND DECISIONS

The following is a useful default flow, **not a mandatory chain for every conversation**:

```text
OPERATOR ↔ RECEPTIONIST (navigation / relay)
PATIENT MANAGER (consequential Patient-wide decisions)
      ↕
HEAD NURSE (routine dispatch / Intern management / report comparison)
      ↕
TEAMS ↔ THEIR MEMBERS (close internal coordination)
      ↕
DOCTORS / NURSES / INTERNS / HEAD INTERNS / PROXY DOCTORS

PATIENT HEAD SURGEON ↔ MANAGER + TEAMS (mass surgery)
PHONE → SPECIALIST (bounded external contract)
```

The Head Nurse can ask one Team to inspect a problem, compare its two or three reports, and forward a concise **source-linked decision packet** to the Manager. The Manager uses the wider Patient dependency map to decide which other Teams need actions and whether the Head Surgeon must be involved.

A Favorites problem may affect several AppControl consumers. The Head Nurse only needs enough awareness to flag that **the boundary is wider than her packet**; the Manager retains the wider context required to act. Neither needs to absorb the other's whole conversation.

**Approval remains scoped**:

- Head Nurse: routine reports/graphs/authorized local dispatch and verification, Intern management.
- Manager: consequential Patient-wide graphs, reports, prioritization and coordinated Team actions; **not Intern management**.
- Head Surgeon: complex Patient surgery/integration in its assigned authority.
- Operator: governing intent, permission escalation where required, and final DONE.

An approval to transmit a report, approval of a dependency graph, permission to issue an action, evidence that it succeeded, and operator acceptance are **different states**. Staff titles never waive explicit approval required for live local writes or destructive operations.

Cross-Patient dependencies are communicated between the relevant Patient Managers/Head Surgeons. Neither Patient automatically absorbs ownership of the other.

## 6 // CONTEXT DISTRIBUTION AND SUCCESSION

**Context is a resource to conserve, not a seniority prize.** A role should load the smallest relevant context that still preserves its required relationships:

| ROLE | DEFAULT CONTEXT |
| --- | --- |
| Intern | Narrow question and source evidence |
| Nurse | Maintenance target, local tests and relevant neighbors |
| Doctor | Assignment, owned code, relevant dependency seams |
| Proxy Doctor | Creator's construction intention and artifact constraints |
| Head Intern | Broad structural atlas, few active surgery details |
| Head Nurse | Task queue, Interns, a few reports, escalation destinations |
| Manager | Patient-wide Team graph, consequences, decisions, blockers |
| Head Surgeon | Dense *relevant* architecture and integration evidence |
| Receptionist | Awareness of who, where, status and communication routes |
| Specialist | Bounded Phone contract and necessary inputs |

When a Head Surgeon is replaced by a Head Intern, the new lead retains its broad structural knowledge but reconstructs live surgery state from **Patient + Room + Assignment + reports/checkpoints + current Git evidence**. It does not need to replay every conversational turn.

All workers remain replaceable; a chat title or historic HEAD is not a trusted source of live state. Keep structure and evidence pointers externally recoverable.

## 7 // REPORTS AND HANDOFFS // PRESERVE EXISTING SCHEMA

The [Hospital Report Protocol](./HOSPITAL-REPORT-PROTOCOL.md) already defines the seven ordered headings. **Do not create a different official report schema per role**:

```text
IMPLEMENTATION
HOW TO USE
VERIFY
WATCH OUT FOR
CHECKLIST
NEXT
DECISIONS
```

Report **density** changes, not the schema: tiny Intern findings can be terse; a Head Nurse report comparison names its source reports and what needs higher authority; a Head Surgeon produces dense surgical evidence. Do not produce a ceremonial full Report after every trivial intermediate action.

A full Report is required at existing meaningful boundaries (blocker, collision, scope expansion, milestone, landing, failed verification, handoff), and the explicit `REPORT` command still requests one. A small operational update can exist without pretending to be a persisted Hospital Report or inventing a competing `micro-checkpoint` standard.

External-browser report headers may **optionally** include `TEAM //` and `STAFF ROLE //` for clarity, while keeping the original Patient/Room/Doctor/Provider/Assignment header intact. Do not claim connected registration or report persistence without verifying it.

A handoff keeps `REPORT KIND // HANDOFF`, all canonical sections, current checklist, ownership, blockers and source evidence, and instructs the successor to reacquire live Git truth. **Final DONE belongs to the operator.**

## 8 // COMPACT ROLE AND TEAM PACKETS

Staff codes are standardized short labels, **not tokens that grant permission**. An external worker may use a compact, human-readable admission record such as:

```text
HOSPITAL // COMPATIBLE
PATIENT // <repository>
TEAM // <bounded work family or NONE>
ROOM // <durable job>
ASSIGNMENT // <work contract>
STAFF ROLE // DOC
WORKER // <worker identity>
PROVIDER // OPEN AI // CHATGPT
CONNECTION // EXTERNAL
SCOPE // <owned tissue / files / contracts>
PERMISSIONS // <explicitly approved>
DEPENDENCIES // <relevant Rooms / Teams / reports>
EVIDENCE // <source + as-of, or UNAVAILABLE>
NEXT // <justified continuation>
```

A Team label such as `T3-F`, chat title such as `Greeting Exchange`, or staff label such as `Nurse 3` is not by itself a unique persistent Room/session identity. Bind a real reference before claiming a chat or worker is connected.

### 8.1 // SEMANTIC IDENTIFIERS AND SELECTIVE DECOMPRESSION

Staff names, suffixes, and Team labels may be **compressed relational addresses**, not abbreviations with exactly one expansion. An identifier can preserve several operator-established meanings at once: its original context, present purpose, history, and relationships to other work. Later meanings can accumulate without erasing earlier ones.

For example, `Head Nurse .C` carries **Context** (original domain), **Cleanup** (present context-cleanup work), and the connection to the original `C2` / `C4` work family. This is a *local*, layered meaning—not a universal rule that `.C` must mean the same thing everywhere.

Keep the identifier compact until its relationships matter. Decompress only enough to interpret an assignment, resolve ambiguity, or preserve provenance. Record confirmed meanings and distinguish them from plausible inference; do not invent expansions or force identical suffixes to have identical meanings across unrelated work. A semantic address never replaces a unique Room/session reference, a scoped Assignment, or explicit permission.

**Model reference:** [How I Think — Generative Strings, Semantic Compression Integrity, and Return Pointers / Semantic Addresses](../HOW-I-THINK-PUBLIC.md#9-generative-strings).

This packet is a **pointer for reconstructing context**, not a compressed replacement for evidence that has not been inspected.

## 9 // SCOPE, COMPATIBILITY, AND SOURCE

This document formalizes the operator's organizational definitions. It does not create live staffing records, change PX's permission engine, connect Copilot, implement Receptionist command dispatch, attach browser conversations to live Hospital, or perform surgery. These require separate authorized and verifiable technical work.

Keep these distinctions invariant:

- **One Receptionist per Hospital; one preferred Head Nurse per Hospital, more only when needed.**
- **One Manager and one Head Surgeon per Patient**, not globally and not per Team.
- **Head Nurse manages Interns; Manager does not.**
- **Head Intern is a low-workload structural/succession reserve, not a supervisor.**
- **Teams are task families; membership varies without changing Team identity.**
- **Proxy Doctor means the creator's proxy for construction**, not Shadow Doctor or replacement of another Doctor.
- **Specialist is a contracted outsider via Phone**, not generic permanent Hospital staff.
- **Role and report approval are not blanket authority**; current-state evidence and operator acceptance remain required.

This protocol preserves the operator's explicit decisions and corrections from the October 2026 Hospital organization discussions. If implementation and written guidance disagree, inspect current technical owners and report the discrepancy; do not guess that policy has already become live behavior.

> **Preserve the work, not the worker; preserve the relationships, not merely the names; retrieve context only where needed.**
