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

**Implementation owner:** [Taskbars // Post-Apollo](https://github.com/kudokudo1/taskbars-post-apollo)

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

**Implementation owner:** [Taskbars // Post-Apollo](https://github.com/kudokudo1/taskbars-post-apollo)

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

# PX // DEV EXPERIENCE

**Implementation owner:** [The Post-Apollo Dev Experience](https://github.com/kudokudo1/The-Post-Apollo-Dev-Exp)

Dev Experience identifies itself as the **developer control plane** of the Post-Apollo family.

The live control CLI is `px`.

Current Dev Experience documentation explicitly covers:

- CLI usage
- workflow operations
- run operations
- watch
- rerun
- cancel
- developer runbooks

Current PX implementation also participates in:

- GitHub repository / workflow operations
- guarded mutation preflight
- operation journaling / recovery
- Hospital room / session state
- AI doctor / provider operations
- exact repository / commit / workflow identity checks

PX is frequently the control-plane implementation underneath higher-level Taskbars / Hospital UI.

Therefore:

> **When a visible UI exists, teach the UI first. Use PX second as control-plane detail / fallback.**

Do not make the user operate PX manually by default merely because PX powers the visible interface.

# SILVERBLUE // TOOLBOX

**STATE //** reserved for implementation recon

This control-surface guide must include the user's Fedora Silverblue host and Toolbox environment because host/container boundaries materially change:

- package-management instructions
- filesystem assumptions
- available commands
- runtime dependencies
- which machine state is being mutated

Rules already established:

- identify host vs Toolbox/container when the distinction matters
- do not assume a normal mutable-Fedora procedure applies unchanged to Silverblue
- do not assume host aliases/packages/paths exist inside Toolbox
- local-machine mutation still follows [AUTHORITY AND PERMISSIONS](./AUTHORITY-AND-PERMISSIONS.md)

Exact operator routes and environment-specific procedures must be documented from current state rather than guessed.

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
