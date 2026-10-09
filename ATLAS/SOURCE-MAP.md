✦︎✦︎✦︎ Meta Apollo Logos //

# 🧭 ATLAS // SOURCE MAP

![](../BUILD/assets/design/chassis/scope-rail.svg)

> **STATE //** active \~\~ **VIEW //** provenance / instruction sources

This map records where the current human/AI working interface comes from.

The goal is **centralized entry, not duplicated truth**.

How I Think is the front door. Technical or project-specific facts remain canonical in the repository that owns them.

## LEGEND

| STATUS | MEANING |
|---|---|
| **CANONICAL HERE** | How I Think owns the current rule or operator guidance |
| **CANONICAL ELSEWHERE** | How I Think points to another repository's source of truth |
| **SOURCE** | Historical material used to derive a current-facing rule |
| **CANDIDATE** | Useful rule observed in work, not yet fully promoted |
| **IMPLEMENTATION** | Code or runtime state that demonstrates the rule in practice |

## 1 // HOW I THINK // DIRECT COLLABORATION SOURCES

| SOURCE | STATUS | CONTRIBUTION |
|---|---|---|
| [HOW-I-THINK-PUBLIC.md](../HOW-I-THINK-PUBLIC.md) | CANONICAL HERE | compressed current model of thinking, communication, uncertainty, action, external systems |
| [dump/0.5-shell-command-conventions.md](../dump/0.5-shell-command-conventions.md) | SOURCE | Fedora host command conventions and host/container distinction |
| [dump/04_additional_inferences_and_working_protocol.md](../dump/04_additional_inferences_and_working_protocol.md) | SOURCE | explicit future-AI working protocol; reconstruct → locate → relate → implement → explain → verify → preserve → stop |
| [dump/15_complete_personal_operating_model.md](../dump/15_complete_personal_operating_model.md) | SOURCE | communication, debugging, planning, authority history, externalized context, AI collaboration |
| [dump/20_ai_complementarity_external_cognition_and_behavioral_fossils.md](../dump/20_ai_complementarity_external_cognition_and_behavioral_fossils.md) | SOURCE | AI as external worker / reasoning workspace; continuity under replaceable workers |
| [dump/23.5_three_q_and_a_model_confidence_learning_ai_and_projects.md](../dump/23.5_three_q_and_a_model_confidence_learning_ai_and_projects.md) | SOURCE | AI/project fit; operator agency; continuity and recovery |

## 2 // FOREST // AGENT AUTHORITY ANCESTRY

Forest's Bristlecone workspace already carries an `AGENTS.md` authority model.

It establishes ideas now reused here:

- user is final authority
- distinguish proposal from approval
- work inside approved scope
- isolate changes
- test and inspect regressions
- report uncertainty
- do not silently canonize an agent's own work

**Status:** CANONICAL ELSEWHERE for Forest-specific behavior; SOURCE for this repo's generalized agent contract.

Reference:
[The Post-Apollo Forest Project](https://github.com/kudokudo1/The-Post-Apollo-Forest-Project)

## 3 // META APOLLO LOGOS // GOVERNING DESIGN SOURCES

The parent Meta Apollo Logos repository remains canonical for family-wide design rules.

### Principles
[MODEL/Meta-Apollo-Logos-Principles.md](https://github.com/kudokudo1/Meta-Apollo-Logos/blob/main/MODEL/Meta-Apollo-Logos-Principles.md)

Carries principles including:

- design for a person
- preserve operator agency
- expose important relationships
- preserve history / provenance / recovery when consequences matter
- give components clear responsibilities
- modularity without meaningless fragmentation
- do not hide failure behind presentation
- do not simplify away load-bearing relationships

**Status:** CANONICAL ELSEWHERE.

### Repository Design Language
[MODEL/Repo-Design-Language.md](https://github.com/kudokudo1/Meta-Apollo-Logos/blob/main/MODEL/Repo-Design-Language.md)

Carries:

- seven-room repository grammar
- BUILD vs DEV semantics
- root/runtime exceptions
- semantic color language
- status language
- Ghost String / diagram grammar
- evidence and archive conventions
- literal code / command handling
- consistency rules

**Status:** CANONICAL ELSEWHERE.

### OPERATE / CONTRIBUTING
These provide migration, maintenance, continuity, provenance, and contribution rules.

**Status:** CANONICAL ELSEWHERE.

## 4 // TASKBARS // POST-APOLLO // LIVE DESKTOP SOURCES

Repository:
[taskbars-post-apollo](https://github.com/kudokudo1/taskbars-post-apollo)

### Runtime layout

Canonical live source remains in runtime-sensitive paths such as:

- `shell.qml`
- `widgets/`
- `components/`
- `modules/`
- `services/`
- `assets/`

**Rule derived:** semantic documentation must not break runtime structure.

### Design-system implementation

`components/Colors.qml` is the implementation source for the live palette.

Current named colors include:

| NAME | VALUE |
|---|---|
| red | `#D16041` |
| orange | `#ED981A` |
| yellow | `#F2BE4E` |
| green | `#9ECE6A` |
| omnitrix | `#00F782` |
| cyan | `#55CFCA` |
| blue | `#5B5FD4` |
| magenta | `#C74EC7` |
| white / off-white | `#DCF3FA` |
| black / chassis purple | `#1B0623` |
| dark | `#16051F` |

Current reusable component vocabulary includes:

- `ModeActuator`
- `SelectorDial`
- `SelectorSlider`
- `NeonScrollBar`
- `IndexRail`
- `ConversationFeed`
- `BranchMap`
- `GohuText`
- `NotoText`
- `Colors`
- button and menu templates

**Rule derived:** inspect and reuse existing Post-Apollo primitives before inventing a near-duplicate.

**Status:** IMPLEMENTATION / CANONICAL ELSEWHERE.

## 5 // DEV EXPERIENCE // CONTROL-PLANE SOURCE

Repository:
[The Post-Apollo Dev Exp](https://github.com/kudokudo1/The-Post-Apollo-Dev-Exp)

Carries developer-control-plane concepts, workflow/run operations, CLI behavior, tests, and runtime-preserving repository organization.

**Status:** CANONICAL ELSEWHERE for implementation; source for developer workflow guidance.

## 6 // HOSPITAL / SURGERY ROOM // PROMOTION QUEUE

Hospital currently has substantial behavior encoded in implementation and working history, but not yet one compact current-facing operator specification.

Material to promote includes:

- patient / room / doctor semantics
- ownership
- branch / target / state
- surgical and certification states
- evidence packets
- collision avoidance
- handoffs
- rounds / reports
- intercom / phone
- provider relationships
- meanings of landed / verified / certified

**Status:** PROMOTED for current-facing behavior. General Post-Apollo development guidance lives in [OPERATE/POST-APOLLO-WORKING-GUIDE.md](../OPERATE/POST-APOLLO-WORKING-GUIDE.md), the Hospital doctor / patient / room / assignment model lives in [OPERATE/HOSPITAL-AGENT-PROTOCOL.md](../OPERATE/HOSPITAL-AGENT-PROTOCOL.md), and report / handoff behavior lives in [OPERATE/HOSPITAL-REPORT-PROTOCOL.md](../OPERATE/HOSPITAL-REPORT-PROTOCOL.md).

## 7 // GIT / GITHUB CONTROL SURFACES // PROMOTION QUEUE

Material to externalize includes:

- repository selection
- status / diff / log
- branches and history
- fetch / pull / safe pull / FF-only / push
- issues / pull requests / projects
- workflows / runs
- topics / visibility / metadata
- LazyGit escape hatch
- which operations should be explained through the menu first

**Status:** PROMOTED / EXPANDING in [OPERATE/CONTROL-SURFACES.md](../OPERATE/CONTROL-SURFACES.md). Git, GitHub, Hospital, PX, and Dev Experience have verified initial entries; additional operator surfaces remain queued for recon.

## 8 // CURRENT CONVERSATION-DERIVED RULES // 2026-10-07

These were made explicit during current work and should be promoted into durable guidance:

- local-machine writes require explicit approval
- planning / architecture does not imply local implementation permission
- local permissions are scoped and do not silently carry forward
- live-system Git state changes and service/runtime restarts require explicit approval
- GitHub work may use the established recoverable branch/PR workflow after implementation intent is clear
- prefer Post-Apollo menu/UI instructions before raw CLI when the UI already exposes the capability
- browser ChatGPT may behave as a Hospital-compatible external doctor through a shared protocol
- Hospital reports should use a stable format and appear at meaningful boundaries rather than constantly

**Status:** PROMOTED for the current operator layer. Local-machine authority, Post-Apollo working behavior, control-surface policy, Hospital-compatible browser-agent behavior, and Hospital report / handoff behavior are current-facing.

## 9 // CENTRALIZATION RULE

The relationship between repositories should be:

```text
HOW I THINK
    ↓
human / AI front door
    ↓
working-with-user rules
authority / permissions
project-routing guidance
    ↓
canonical external source when technical detail matters
    ↓
Meta Apollo / Taskbars / Dev Exp / Forest / Hospital implementation
```

> **One entry point. Many owned sources. No unnecessary duplication.**
