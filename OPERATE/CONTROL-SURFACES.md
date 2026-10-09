✦︎✦︎✦︎ Meta Apollo Logos //

# 🖳 OPERATE // CONTROL SURFACES

![](../BUILD/assets/design/chassis/system-rail.svg)

> **STATE //** active / expanding \~\~ **VIEW //** operator-interface map

This document tells humans and AI agents **which interface the user is meant to operate first** when a capability already exists in the user's environment.

It is an index and routing layer, not a replacement for the implementation repositories that own the actual controls.

## 1 // CORE RULE // UI FIRST

When the user asks how to perform an operation and an existing Post-Apollo or operator-facing interface exposes it, give the **actual UI / menu route first**.

Use the labels that are visible in the interface.

Preferred answer shape:

```text
PREFERRED
Git → GIT // LOCAL → BRANCHES → <actual control>

CLI EQUIVALENT / FALLBACK
<command>
```

Do not default to raw commands when the user deliberately built a control surface for the operation.

## 2 // CLI SECOND

After the operator route, include the relevant CLI equivalent or fallback when useful.

CLI remains important for:

- diagnostics
- exact inspection
- automation
- recovery
- implementation details
- capabilities not exposed by the UI
- cases where the user explicitly asks for commands

The CLI is not hidden. It is simply **not automatically the first human interface**.

## 3 // DO NOT GUESS ABOUT CURRENT UI

If an AI is unsure whether the current interface exposes a capability:

1. inspect the current implementation / documentation
2. identify the real visible route
3. report missing or incomplete functionality honestly
4. then provide the best available fallback

Do not invent menu items from memory.

Do not assume a feature is missing because an older version lacked it.

Do not describe an unfinished or broken control as working.

## 4 // BROKEN / INCOMPLETE SURFACES

If the intended control exists but is currently broken, incomplete, unavailable, or missing the requested variation:

- say that explicitly
- identify the closest working UI route
- provide the fallback
- distinguish the intended interface from the currently functioning path

CLI fallback must not hide missing operator-interface functionality.

A missing UI capability is useful product information.

## 5 // USE THE INTERFACE'S REAL LANGUAGE

Instructions should use the actual visible labels wherever possible.

Examples already verified in the current Taskbars implementation include:

- `GIT // LOCAL`
- `GITHUB // REMOTE`
- `RECEPTION`
- `SURGERY`
- `ATTENTION`
- `ARCHIVE`
- `REPORTS`
- `ROUNDS`
- `STAFF`

Do not rename them into generic equivalents unless explanation requires it.

The route should correspond to something the user can actually locate on screen.

# CONTROL-SURFACE STACK

A useful default model is:

```text
OPERATOR INTERFACE
Taskbars / Git / Hospital / editor / desktop controls
        ↓
CONTROL PLANE
PX / Dev Experience / shared services
        ↓
UNDERLYING PRIMITIVE
git / gh / shell / API / system tool
```

Start from the highest existing operator surface that fits the task.

Descend when the task requires more direct control or explanation.

# GIT // GITHUB

**Implementation owner:** [Taskbars // Post-Apollo](https://github.com/kudokudo1/The-Post-Apollo-Project)

## Boundary

Git / GitHub own ordinary repository and remote-development operations.

They report repository, branch, commit, workflow, issue, pull-request, project, review, and related remote facts.

When the operation becomes part of Hospital-managed surgery or certification, preserve the existing Hospital boundary rather than bypassing it.

## Verified top-level surfaces

```text
Git
├── GIT // LOCAL
└── GITHUB // REMOTE
```

### GIT // LOCAL

Current implementation has distinct navigation for:

- control
- branches
- changes
- history
- repository
- operations

Verified visible controls / concepts include:

- repository selection
- local target
- remote target
- explicit sync direction
- `FETCH`
- `STATUS`
- `DIFF`
- `LOG`
- `LAZYGIT`

The Git surface can also move between related contexts, including:

- branch → history
- file → history
- file → changes
- blame → commit / history
- commit / branch context → related Git views

### GITHUB // REMOTE

Verified current implementation includes operator surfaces for:

- workflows
- saved workflow library / procedures
- workflow runs
- run details
- rerun
- cancel
- issues
- pull requests
- review threads
- projects / work items
- merge queue
- repository profile / metadata-related services

Exact routes should be inspected from the current implementation before giving step-by-step instructions when the route is not already documented here.

# HOSPITAL

**Implementation owner:** [Taskbars // Post-Apollo](https://github.com/kudokudo1/The-Post-Apollo-Project)

## Boundary

Hospital owns:

- surgery
- rooms
- ownership
- coordination
- certification
- evidence interpretation
- integration state
- surgical continuity

Git / GitHub provide factual evidence.

Hospital decides what those facts mean for surgical readiness and progression.

PX performs operations assigned to the control plane.

## Verified top-level surfaces

```text
Hospital
├── RECEPTION
├── SURGERY
├── ATTENTION
├── ARCHIVE
├── REPORTS
├── ROUNDS
└── STAFF
```

Verified Hospital UI concepts include:

- floor / repository
- bed / local checkout
- room
- patient
- worktree / beds
- branch
- location
- HEAD
- relation
- last touched
- operating rooms
- Intercom
- Phone

The current codebase also contains dedicated Hospital surfaces / services for:

- charts
- room chat
- room reports
- specialists
- GitHub attention
- merge queue
- checkpoints
- certification
- provider state
- rounds
- archive / history

## Git ↔ Hospital boundary

For ordinary repository work:

```text
Git / GitHub
→ repository operation
```

For Hospital-managed surgery:

```text
Hospital
→ room / ownership / certification / integration meaning
→ Git / GitHub evidence where needed
→ PX operation where needed
```

Do not redesign this boundary while merely explaining how to use it.

# PX // DEV EXPERIENCE // SILVERBLUE // TOOLBOX

**Implementation owner:** [The Post-Apollo Dev Experience](https://github.com/kudokudo1/The-Post-Apollo-Dev-Exp)

These are coupled surfaces.

Dev Experience is not merely another tool that happens to run on a Silverblue workstation. Part of its job is to compensate for the host / Toolbox split so the operator does not have to manually solve that boundary for every command.

## Role

Dev Experience identifies itself as the **developer control plane** of the Post-Apollo family.

The live control CLI is `px`.

The current relationship is:

```text
TASKBARS / HOSPITAL / GIT UI
        ↓
semantic PX operations
        ↓
DEV EXPERIENCE CONTROL PLANE
        ↓
host / Toolbox / GitHub / AI-provider / system primitive
```

For ordinary executable discovery, Dev Experience adds another relationship:

```text
operator asks for tool
        ↓
PX discovers host + Toolbox
        ↓
PX resolves exact environment
        ↓
exact invocation
```

## Taskbars relationship

Current Taskbars implementation already delegates substantial control-plane behavior to PX.

Verified examples include:

- GitHub workflows
- workflow runs
- run inspection
- run logs
- workflow dispatch
- workflow factory operations
- Hospital provider discovery
- Hospital Doctor sessions
- Hospital Doctor turns
- Hospital reports / feedback

Taskbars also checks whether the installed `~/.local/bin/px` matches the current Dev Experience runtime source and exposes stale / missing / out-of-date PX states.

Taskbars therefore uses PX as a semantic backend.

Current recon does **not** show Taskbars using the generic `px which` cross-environment resolver for arbitrary executable launch. That host / Toolbox compensation currently belongs primarily to Dev Experience / TERM EXP.

## Tool discovery // `px tools`

PX maintains a live executable registry across:

- the host
- the configured Toolbox

Current default Toolbox:

```text
fedora-toolbox-44
```

The default is configurable with:

```text
PX_TOOLBOX
```

Toolbox discovery intentionally scans sanitized system directories rather than inheriting the host's shared-home wrapper paths.

In particular, the registry tests explicitly prevent paths such as:

```text
~/.local/bin
```

from being inherited into the Toolbox scan.

This prevents a host-visible wrapper in shared home from being misidentified as a real Toolbox-native installation.

Operator / diagnostic route:

```text
px tools
px tools <query>
```

## Cross-environment resolution // `px which`

PX has an explicit resolver policy:

```text
host-first-v1
```

Its default behavior is:

```text
1. preserve normal host PATH behavior
2. if the command is unavailable on the host, fall back to Toolbox
3. return the exact invocation for the selected environment
```

A Toolbox resolution carries an invocation equivalent to:

```text
toolbox run -c <toolbox> -- <resolved-path>
```

PX can also deliberately force:

- a backend
- a specific environment

when the environment itself matters.

Operator / diagnostic route:

```text
px which <tool>
```

Use direct `toolbox run ...` instructions when diagnosing the boundary, explicitly forcing an environment, or when PX does not cover the requested operation.

Do not make the user manually choose Toolbox first when the PX resolver can correctly choose the execution environment.

## TERM EXP // environment-normalizing frontend

Current Dev Experience includes the TERM EXP terminal control surface.

Open with:

```text
px term
```

Alias:

```text
px tui
```

TERM EXP consumes the live:

```text
px actions --json
px tools --json
```

registries.

Its Find Anything surface spans:

- semantic PX actions
- preferred host commands
- preferred Toolbox commands

Current approved interactive specialists include:

- Lazygit
- Neovim
- btop
- Zellij
- fzf

Before launching one of these specialists, TERM EXP re-resolves it through the current PX resolver and uses the exact returned invocation.

This means the operator can select **Neovim** or **Lazygit** as a capability without first remembering whether that executable currently lives on the host or in Toolbox.

TERM EXP is therefore one of the primary ways Dev Experience compensates for the Silverblue / Toolbox split.

## Silverblue / Toolbox operator model

The workstation has two materially different execution environments:

```text
SILVERBLUE HOST
immutable / host-integrated operating environment

TOOLBOX
mutable development container environment
```

The boundary affects:

- package-management instructions
- executable availability
- PATH
- runtime dependencies
- filesystem assumptions
- whether a command changes host or container state

An AI should first determine whether Dev Experience already abstracts the distinction.

Preferred decision path:

```text
Does a Post-Apollo UI expose the capability?
        ↓ yes
use that UI

        ↓ no

Does PX / TERM EXP expose or resolve it?
        ↓ yes
use PX / TERM EXP

        ↓ no

Does the operation specifically belong to host or Toolbox?
        ↓
give the environment-specific primitive
```

## What Dev Experience currently abstracts

Verified current compensation includes:

- host + Toolbox executable discovery
- deterministic host-first resolution
- exact Toolbox invocation generation
- searchable cross-environment tool selection in TERM EXP
- specialist launch without making the operator choose the backend first
- semantic PX actions above raw GitHub / Hospital / AI-provider primitives
- guarded mutation preview / confirmation / verification
- durable operation journaling and recovery evidence

## What still leaks through

The abstraction is intentionally not a claim that host and Toolbox are identical.

The environment still matters for:

- installing or removing software
- host services
- system configuration
- immutable-host package changes
- container-specific dependencies
- debugging missing binaries
- path / environment-specific behavior
- operations that PX has not modeled

Current Taskbars surfaces consume many semantic PX operations, but the generic cross-environment executable resolver is currently a Dev Experience / TERM EXP capability rather than a universal Taskbars launcher.

Also, `px term` currently launches the TERM EXP Rust crate through Cargo from the Dev Experience runtime tree until the later installer/runtime lane supplies a compiled installed binary.

## Guidance rule

Do not teach Silverblue, Toolbox, and Dev Experience as three unrelated systems.

Before telling the user to enter Toolbox or manually construct a container command:

1. check whether the existing Post-Apollo UI already exposes the operation;
2. check whether PX / TERM EXP already resolves or performs it;
3. only expose the raw host / Toolbox boundary when it is actually relevant.

When the raw environment boundary is relevant, name it explicitly.

Do not assume a normal mutable-Fedora procedure applies unchanged to Silverblue.

Do not assume host aliases, packages, or paths exist inside Toolbox.

Local-machine mutation still follows [AUTHORITY AND PERMISSIONS](./AUTHORITY-AND-PERMISSIONS.md).

# NEOVIM // EDITOR

**STATE //** reserved for implementation recon

The user's Neovim environment is a first-class operator surface, not merely a generic text editor.

When an operation is already exposed through the user's actual editor configuration, AI guidance should prefer that real editor workflow before generic editor instructions.

Exact plugins, key routes, commands, and editor-specific procedures must be inspected from the current configuration before being promoted here.

# ADDITIONAL POST-APOLLO SURFACES

The following are explicitly in scope for this guide and should be documented from their current implementations:

- AppControl
- Social
- Notifications
- CPU++
- Weather Station
- other Post-Apollo operator surfaces as they become relevant

Their existence is in scope now.

Their detailed capabilities are **not** to be invented before recon.

# ROUTING RULE FOR FUTURE ENTRIES

For each control surface added here, record:

```text
SURFACE
what it owns

VISIBLE ROUTE
actual labels / path

CAN DO
verified capabilities

WHEN TO USE IT
operator intent

CONTROL-PLANE BACKING
PX / service / provider / system layer when relevant

CLI / PRIMITIVE FALLBACK
actual lower-level equivalent

KNOWN LIMITS
broken / missing / incomplete behavior
```

# SOURCE RELATIONSHIP

This policy is user-approved.

Verified implementation facts in the current version were drawn from:

- Taskbars Git / GitHub UI and services
- Taskbars Hospital UI and services
- Hospital certification and evidence contracts
- The Post-Apollo Dev Experience
- PX implementation

Technical behavior remains canonical in the repository that owns it.

When this guide drifts from the live implementation, inspect the implementation and report the drift rather than silently pretending the guide is current.
