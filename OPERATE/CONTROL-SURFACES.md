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

# TERMINAL // SHELL // SESSION // EDITOR

The user's command-line development environment is a connected stack rather than four unrelated programs.

Verified current relationship:

```text
PRETTY KITTY
terminal / CRT presentation / terminal entry
        ↓
ZELLIJ
persistent terminal workspace / session / panes / tabs
        ↓
OH MY APOLLO
Zsh shell behavior / aliases / completion / command language
        ↓
ASTRO SNACKS
Neovim / AstroNvim development editor
```

Dev Experience / PX intersects this stack when semantic development operations, cross-environment tool resolution, or Toolbox compensation are needed.

```text
Pretty Kitty → Zellij → Oh My Apollo → Astro Snacks
                         ↕
                   PX / Dev Exp
                         ↕
                host / Toolbox
```

Do not explain commands, terminal behavior, or editor launch as though the user were operating a stock terminal + stock Bash + stock Vim environment.

# PRETTY KITTY

**Implementation owner:** [Post-Apollo Pretty Kitty](https://github.com/kudokudo1/Post-Apollo-Pretty-Kitty)

Pretty Kitty is the Post-Apollo Kitty terminal surface.

Verified current configuration includes:

- Kitty as the terminal frontend
- CRT / shader presentation infrastructure
- background opacity `0.8`
- `GohuFont 11 Nerd Font Mono`
- Kitty shell entry through `~/.local/bin/kitty-zellij`

The tracked `kitty-zellij` wrapper is:

```text
zellij attach --create main
```

Therefore opening the normal Pretty Kitty terminal does not merely spawn an isolated shell.

It enters or creates the persistent Zellij session named:

```text
main
```

## CRT state as diagnostic evidence

Pretty Kitty's CRT behavior is not merely decorative.

The current shader pipeline has persistent visual state and responds to Kitty activity / focus events. Visible states such as:

- active
- sleep
- `NO SIGNAL`
- wake / transition behavior

are meaningful observations of the terminal's current CRT state machine.

When the user reports a state such as:

```text
Pretty Kitty still says NO SIGNAL.
Pretty Kitty is not waking up.
Pretty Kitty is not responding to activity.
```

treat that report as literal runtime evidence.

Do **not** begin by assuming the user does not know how to wake or focus the terminal.

If activity / focus that normally triggers wake does not move the CRT out of its sleeping / no-signal state, something in the expected:

```text
Kitty event
→ persistent CRT state
→ wake transition
→ rendered output
```

relationship is not behaving correctly.

The visible state is strong diagnostic evidence, but it does not by itself identify the failing internal component. Use it to narrow investigation rather than replacing investigation.

## Guidance rule

When the user asks to run something **in the terminal**, assume the existing Pretty Kitty / Zellij environment is relevant unless the task specifically requires a fresh external terminal, a different environment, or another control surface.

Do not casually tell the user to open another terminal when an operation can be performed in the terminal / pane they already occupy.


# CRT-TV // RECEIVER DECK

**Implementation owner:** [Post-Apollo CRT-TV](https://github.com/kudokudo1/Post-Apollo-CRT-TV)

CRT-TV is the receiver-style appliance layer around a Kitty / Zellij terminal workspace.

It is distinct from Pretty Kitty:

```text
Pretty Kitty
→ terminal presentation / CRT shader-state behavior

CRT-TV
→ spatial receiver / deck / side-panel composition around terminal workspace
```

## Current launcher

The current launcher is:

```text
post-apollo-tv
```

from the project's `bin/post-apollo-tv` implementation.

The launcher currently assembles:

```text
Kitty terminal
        ↓
Zellij

+ Quickshell receiver deck
+ Quickshell side panel
+ Sway geometry follower
```

The terminal window uses:

```text
app_id // post-apollo-terminal
title  // Post-Apollo Terminal
```

The launcher deliberately removes inherited Zellij session variables before starting the TV terminal so it can create its own Zellij runtime rather than accidentally nesting inside the caller's current session.

## Physical / spatial relationship

The launcher first creates the terminal, deck, and side surfaces, then uses the shared TV geometry helper to convert / synchronize them as one spatial unit.

Current assembly includes:

- terminal / screen
- deck underneath the terminal
- side panel beside the terminal
- shared Sway movement / geometry tracking

Treat a geometry failure as a possible relationship failure between:

```text
Kitty
Quickshell deck / side
Sway
TvGeometry.py
```

rather than assuming Zellij itself is broken.

## Receiver display language

The current receiver face visibly presents state concepts including:

```text
SESSION
TAB
MODE
CONTROL
SOURCE
ZELLIJ
DVD / TERMINAL
DIGITAL VIDEO / DATA DECK
```

It also contains physical-looking controls labeled:

```text
POWER
EJECT
NEW
CLOSE
FULL
FLOAT
RENAME
PIN
FRAME
SYNC
OPTION
```

and a MODE dial / rocker controls.

## Important current limitation // faceplate controls are not yet wired

The current `ReceiverDeck.qml` contains the visual control components and labels, but the verified implementation does **not** currently contain click / tap handlers for those faceplate controls.

The deck's `DeckButton`, rocker, mode dial, power, eject, and labeled button surfaces are currently presentation / chassis work rather than verified live Zellij mutations.

Therefore:

> **Do not instruct the user to press a receiver-deck control as though it already performs the labeled operation until current implementation recon shows that control is wired.**

The CRT-TV shell / geometry assembly is real.

The labeled receiver hardware is currently ahead of its control wiring.

## Guidance rule

Use CRT-TV when the task concerns the receiver-style terminal appliance, its spatial assembly, its future physical controls, or the relationship between the TV shell and Zellij.

Use Pretty Kitty when the task concerns terminal rendering / CRT state / shaders.

Use Zellij when the task concerns actual session / tab / pane behavior.

Do not collapse all three into "Kitty."

# ZELLIJ // PERSISTENT TERMINAL WORKSPACE

**Implementation owner:** [Post-Apollo Zellij](https://github.com/kudokudo1/Post-Apollo-Zellij)

Zellij owns persistent terminal workspace structure:

- sessions
- panes
- tabs
- terminal workspace continuity
- Post-Apollo layout / plugin behavior

Current verified version documented by the project:

```text
0.45.0
```

Current config uses:

```text
default_shell "zsh"
```

so new Zellij panes enter the user's Zsh / Oh My Apollo shell environment rather than an unrelated shell.

Useful verified control modes include:

```text
Ctrl-p → pane mode
Ctrl-t → tab mode
Ctrl-o → session mode
```

Verified direct controls also include:

- `Alt-h` / `Alt-l` → move focus or tab left / right
- `Alt-n` → new pane
- `Alt-f` → toggle floating panes
- pane mode → new panes, rename, pin, stack, float, move
- tab mode → new / rename / close / navigate tabs
- session mode → session manager and related session controls

The Post-Apollo repository also carries a custom Zellij layout and WASM plugin.

## Continuity role

Pretty Kitty supplies the terminal window.

Zellij supplies persistence and internal terminal structure.

A terminal window disappearing does not necessarily mean the Zellij workspace disappeared.

When troubleshooting terminal state, distinguish:

```text
Kitty window
Zellij session
Zellij pane / tab
shell process inside the pane
program running inside the shell
```

# OH MY APOLLO // ZSH

**Implementation owner:** [Post-Apollo Oh My Apollo](https://github.com/kudokudo1/Post-Apollo-Oh-My-Apollo)

Oh My Apollo is the user's interactive shell layer.

Primary tracked live configuration corresponds to:

```text
~/.config/zsh
```

The current shell stack includes:

- Zsh
- Oh My Zsh
- Powerlevel10k
- Zinit
- shared command history
- completion menu behavior
- zoxide
- fzf integration
- Post-Apollo command aliases

Current environment declares:

```text
EDITOR=nvim
VISUAL=nvim
```

and places:

```text
~/.local/bin
```

on `PATH`.

Verified command-language conventions include:

```text
ls   → eza --icons
ll   → eza -lh --icons --git
la   → eza -lah --icons --git
tv   → eza --tree --icons
cat  → bat / batcat when available
grep → rg --color=auto
vim  → nvim
```

These are user environment semantics, not mistakes to repeatedly "correct" back to stock GNU command names.

When exact underlying binaries matter, use the explicit primitive rather than assuming the alias.

See also [COMMAND ENVIRONMENT](./COMMAND-ENVIRONMENT.md).

# ASTRO SNACKS // NEOVIM

**Implementation owner:** [Post-Apollo Astro Snacks](https://github.com/kudokudo1/Post-Apollo-Astro-Snacks)

Astro Snacks is the user's actual Neovim configuration and should be treated as the canonical editor surface for operator guidance.

It is based on:

```text
Neovim
→ AstroNvim v6+
→ Lazy.nvim
→ Post-Apollo plugin configuration
```

Do not substitute generic Vim instructions when the current Astro Snacks surface already provides the operation.

## Editor entry

The shell environment already maps:

```text
vim → nvim
EDITOR → nvim
VISUAL → nvim
```

Dev Experience TERM EXP also recognizes **Neovim** as an approved interactive specialist and re-resolves it through `px which` before launch.

This means editor launch can participate in Dev Experience's host / Toolbox compensation instead of requiring the operator to manually choose an environment first.

## Core editor language

Verified AstroNvim configuration uses:

```text
Leader      = Space
LocalLeader = ,
```

Current LSP behavior includes:

- AstroLSP
- codelens enabled
- semantic tokens enabled
- inlay hints disabled by default
- format-on-save enabled
- QML language server `qmlls`

Mason-managed tools currently include:

- `lua-language-server`
- `stylua`
- `debugpy`
- `tree-sitter-cli`

## Verified operator controls

### Diagnostics // Trouble

```text
<leader>xx → diagnostics
<leader>xX → diagnostics for current buffer
<leader>xq → quickfix list
```

Trouble intentionally does **not** own the symbols / outline job.

### Outline // Aerial

```text
<leader>lo → toggle outline
```

Aerial owns the code outline relationship.

### Minimap

```text
<leader>mm → toggle minimap
```

The minimap integrates:

- search hits
- diagnostics
- Git signs

### Focus // Twilight

```text
<leader>tw → toggle Twilight
```

### Navigation // Flash

```text
s → Flash jump
S → Flash Treesitter jump
```

### Embedded terminal // termim.nvim

Configured terminal commands include:

```text
:Fterm / :FTerm
:Sterm / :STerm
:Tterm / :TTerm
:Vterm / :VTerm
```

Use the actual editor terminal capability when the desired operation belongs inside the editor.

Do not automatically open a separate terminal window.

## Additional verified editor behavior

Current configuration also includes:

- Snacks
  - dashboard support
  - indent support
  - Zen support
  - Snacks scrolling disabled
- Mini
  - icons
  - indent scope
  - cursor-word highlighting
  - animated cursor / scrolling
- Noice
  - command-palette / message presentation
- Vimade
  - inactive-window fading
- LSP signature support
- completion / snippets / autopairs through the AstroNvim configuration
- the `oasis-twilight` colorscheme selection

## Ownership distinctions

Use the correct layer when diagnosing behavior:

```text
Pretty Kitty
→ terminal rendering / Kitty configuration / CRT shaders

Zellij
→ session / pane / tab structure

Oh My Apollo
→ shell startup / aliases / completion / command behavior

Astro Snacks
→ editing / LSP / diagnostics / editor navigation / editor UI

PX / Dev Experience
→ semantic development control + environment resolution
```

A visual problem in Kitty is not automatically a Zellij problem.

A shell alias problem is not automatically a Neovim problem.

A missing binary may be an environment-resolution problem rather than an editor configuration problem.

## Guidance rule

When the user asks how to perform editor or terminal development work:

1. prefer the existing Astro Snacks operation when the editor owns the task;
2. prefer the existing Zellij operation when pane / tab / session structure owns the task;
3. respect Oh My Apollo command semantics when giving shell commands;
4. treat Pretty Kitty as the normal terminal entry / presentation surface;
5. use PX / TERM EXP before forcing the user to manually reason about host vs Toolbox when Dev Experience already abstracts that boundary;
6. expose raw primitives only when the higher-level surfaces do not cover the operation or when diagnosis requires them.


# SWAY // SWAYPX // SPATIAL CONTROL

The Post-Apollo spatial layer is split across two repositories with different ownership.

```text
SwayPX
→ compositor capabilities / renderer / animation / effects / IPC behavior

Post-Apollo Sway Config
→ operator/session policy / keybindings / outputs / rules / startup

Taskbars / CRT-TV / Social / Weather / AppControl
→ higher-level consumers of spatial behavior

swaymsg
→ raw compositor primitive
```

Do not collapse the compositor source, the live session config, and the applications consuming Sway IPC into one thing.

## SWAYPX // compositor implementation

**Implementation owner:** [Post-Apollo SwayPx](https://github.com/kudokudo1/Post-Apollo-SwayPx)

SwayPX is the Post-Apollo compositor fork.

It preserves SwayFX / Sway lineage and upstream-oriented source structure while adding Post-Apollo spatial behavior.

The current Sway Config repository declares the custom compositor runtime at:

```text
~/.local/opt/swayfx/bin/sway
```

Treat that path as the configured project relationship, not as proof that an arbitrary current process still uses that exact binary without runtime inspection.

### Verified compositor capabilities

Inherited / current SwayFX-style capabilities include:

- blur
- rounded corners / borders / titlebars
- shadows
- inactive-window dimming
- layer-shell effects
- scratchpad-minimize behavior
- ordinary Sway window / workspace / output IPC

Post-Apollo SwayPX also has explicit animation configuration.

Current animation events understood by the compositor include:

```text
OPEN
CLOSE
MOVE
RESIZE
WORKSPACE
```

Current animation styles include:

```text
DEFAULT
CRT
INHERIT
```

The compositor implementation has special CRT semantics for window opening and closing.

CRT open begins from a horizontal-line-like collapsed height and expands to the final geometry.

CRT close collapses the window toward a thin horizontal line before completion.

This is compositor behavior, not a Kitty shader effect.

Do not confuse:

```text
Pretty Kitty CRT
→ terminal shader / signal-state behavior

SwayPX CRT
→ compositor window open / close animation
```

## POST-APOLLO SWAY CONFIG // session policy

**Implementation owner:** [Post-Apollo Sway Config](https://github.com/kudokudo1/Post-Apollo-Sway-Config)

This repository owns the live Sway session policy:

- displays
- workspaces
- gaps
- window rules
- keybindings
- startup
- Quickshell launch
- terminal / file-manager routes
- audio / brightness / screenshot keys
- application-specific spatial rules

The runtime `config` remains in Sway's normal configuration shape rather than being moved into Meta Apollo documentation rooms.

### Current configured entry routes

Verified current key routes include:

```text
Mod+Return
→ terminal

Mod+d
→ AppControl

Mod+g
→ Git control menu

Mod+h
→ Hospital control menu

Mod+Shift+f
→ file explorer

Mod+Shift+e
→ Post-Apollo power menu
```

The current terminal command in the config resolves to the later assignment:

```text
kitty zellij
```

The current file-explorer command is:

```text
kitty yazi
```

These session routes sit underneath the richer Pretty Kitty / Zellij / AppControl relationships documented elsewhere in this guide.

### Focus / movement

Verified current spatial shortcuts include:

```text
Mod+Arrow
→ move focus

Mod+Shift+Arrow
→ move focused window

Mod+1..0
→ switch workspace

Mod+Shift+1..0
→ move focused container to workspace

Mod+f
→ fullscreen

Mod+Shift+Space
→ toggle floating

Mod+Space
→ switch focus between tiling / floating areas

Mod+Shift+-
→ move focused window to scratchpad

Mod+-
→ show / cycle scratchpad

Mod+r
→ resize mode
```

The traditional `Mod+h` focus-left route is intentionally displaced because `Mod+h` is reserved for Hospital; current config uses `Mod+Left` for focus left.

### Pointer move / resize

The current floating modifier is:

```text
Mod + left mouse
→ move

Mod + right mouse
→ resize
```

This relationship is also used by higher-level Social / Discord geometry behavior.

### Current visual session policy

The current Sway config sets:

```text
animation_duration_ms 250
animation open CRT
animation close CRT
```

and also configures:

- inner / outer gaps
- focused / inactive / urgent border colors
- window shadows
- active / inactive shadow colors

These are compositor/session presentation rules rather than Taskbars widget styling.

## Output names // live state wins

The Sway Config repository intentionally preserves machine-specific output names and geometry as a known-working baseline.

Current repository text includes output names such as:

```text
DP-3
HDMI-A-1
```

Do **not** treat a repository snapshot as authoritative proof of the currently connected output names.

Before current-state monitor instructions, use live Sway state such as:

```text
swaymsg -t get_outputs
```

when available.

If the user's observed live output identity conflicts with an older config snapshot, investigate the drift rather than assuming the user is wrong.

The same rule applies to resolution, position, refresh rate, focus, and workspace-output attachment.

## Higher-level spatial control // AppControl WINDOWS

For ordinary window operations, AppControl already exposes a higher-level Sway control surface.

Verified current WINDOW actions include:

```text
FOCUS
MOVE HERE
TOGGLE FLOATING
TOGGLE CENTER
TOGGLE FULLSCREEN
```

These operate against Sway container identity.

Therefore, when the user asks how to focus, bring over, float, center, or fullscreen a discovered window:

> **Use AppControl → WINDOWS first when that UI route fits the task.**

Use `swaymsg` second as the raw primitive / diagnostic / fallback.

AppControl also subscribes to Sway window / workspace events and refreshes from the authoritative Sway tree rather than attempting to maintain an entirely separate spatial truth.

## Higher-level consumers

Sway / SwayPX is infrastructure underneath several Post-Apollo surfaces.

### Notifications

Notification Hub app navigation uses Sway to:

- focus an exact matching window
- move an exact matching window to the current workspace
- focus it after movement
- fall back to launching the application when no matching window exists

### Social // Discord

Social uses Sway for:

- shared floating-window geometry
- workspace-relative placement
- move / resize tracking
- Vesktop scratchpad lifecycle
- synchronized Discord / Social positioning

Its persistent geometry helper uses direct Sway IPC.

### Weather Station

Weather Station's Star Map uses Sway to:

- detect the dedicated `weather-screen` Kitty window
- float it
- remove its border
- resize it into the instrument bay
- move it to exact geometry
- show it from scratchpad
- kill it when closed

### CRT-TV

CRT-TV uses Sway to assemble:

- Kitty terminal
- receiver deck
- side panel

into one coordinated spatial appliance.

It first lets Sway establish the tiled relationship, then its geometry helper converts / follows the assembled surfaces as the TV unit.

### AppControl RUN

AppControl's FLOAT / FULLSCREEN Kitty routes create unique application IDs and use temporary Sway criteria so only the intended Kitty window receives the spatial rule.

## SwayPX vs application geometry

When a Post-Apollo surface visibly moves / resizes / focuses another window, do not assume that logic belongs inside SwayPX.

Use this ownership test:

```text
Does the behavior define compositor capability for all windows?
→ SwayPX

Does it define the user's desktop/session rule?
→ Post-Apollo Sway Config

Does it coordinate one Post-Apollo appliance/widget/application?
→ that application's own geometry/controller layer

Does it perform one raw spatial operation?
→ swaymsg / Sway IPC
```

This prevents appliance-specific layout logic from being pushed into the compositor merely because Sway ultimately executes the movement.

## Dev Experience relationship

Current recon does not show a general PX abstraction for Sway window / workspace / geometry operations comparable to PX's host / Toolbox executable resolver.

For spatial operations, current higher-level abstraction primarily lives in:

- Taskbars control surfaces
- application-specific geometry helpers
- Sway Config keybindings / rules

with Sway IPC / `swaymsg` underneath.

Do not invent a `px sway` route that does not currently exist.

## Configuration reload / mutation

Current Sway config provides:

```text
Mod+Shift+r
→ reload Sway configuration
```

Editing the live Sway config, changing output policy, changing keybindings, rebuilding / replacing SwayPX, or restarting the compositor is a local-machine mutation.

Those actions remain subject to [AUTHORITY AND PERMISSIONS](./AUTHORITY-AND-PERMISSIONS.md).

Reading Sway IPC state for diagnosis does not by itself authorize changing that state.

## Guidance rule

For spatial questions:

1. identify whether the request belongs to a higher-level Post-Apollo surface;
2. use that actual UI / control first when it exists;
3. use current Sway state for factual window / workspace / output claims;
4. use Sway Config for persistent operator/session policy;
5. use SwayPX for compositor capability / animation / renderer changes;
6. use `swaymsg` as the direct primitive when needed;
7. do not infer live output geometry from stale config alone.

# APPCONTROL

**Implementation owner:** [The Post-Apollo Project](https://github.com/kudokudo1/The-Post-Apollo-Project)

AppControl is the general desktop / application / command / process control surface.

The dock launcher is the visible:

```text
-⋆♱⋆-
```

button.

Current verified top-level AppControl modes are:

```text
FAVORITES
APPS
FILES
RUN
WINDOWS
REMOTE
THERMAL
KILL
SYSTEM
```

These are real mode labels from the current implementation.

## FAVORITES

FAVORITES is a cross-surface collection rather than a separate subsystem.

Current implementation can preserve / reconstruct favorites for multiple AppControl families, including application entries, run commands, windows / tabs, tasks, and monitor metrics.

Use FAVORITES when the operator has already promoted a frequently used object or metric into their preferred control set.

## APPS

APPS owns application discovery and launching.

Verified current distinctions include:

- normal / native application entries
- Flatpak entries
- hidden commands that do not normally expose a launchable desktop entry
- normal launch
- Toolbox launch
- Bottles launch

Hidden command entries are automatically given a terminal when needed so interactive tools remain usable.

The Flatpak-specific source view intentionally prevents native entries from exposing mixed launch / control actions while they are shown only for comparison.

## FILES

FILES owns filesystem browsing / searching through the shared AppControl surface.

Verified behavior includes:

- browse
- search
- parent / up navigation
- open file or directory
- reveal entry
- open terminal here
- favorite-aware ordering

Filesystem provider behavior is delegated to the file service; AppControl retains the shared selection, search, detail, focus, and favorite interaction.

## RUN

RUN is AppControl's command surface.

Verified current list modes include:

- user-entered command / favorites / session history
- terminal history
- all executable command names available from the current PATH

Verified launch prefixes are:

```text
NORMAL
KITTY
TOOLBOX
```

`NORMAL` executes through the configured shell.

`KITTY` launches through a dedicated Kitty instance.

`TOOLBOX` launches Kitty, executes the command inside the default Toolbox, and leaves an interactive shell open inside that Toolbox afterward.

AppControl also has dedicated FLOAT and FULLSCREEN Kitty launch behavior through Sway.

The RUN surface has a deliberately conservative process-termination action. It only offers that destructive path when a simple command can be mapped to an exact currently running process; ambiguous pipelines / wrappers / services are not treated as safe kill targets.

### Relationship to PX / Dev Experience

AppControl's explicit `TOOLBOX` RUN prefix is a **chosen environment route**.

PX's `px which` is a **resolver** that decides host vs Toolbox according to the Dev Experience policy.

Do not collapse these into the same behavior:

```text
AppControl RUN → TOOLBOX
operator explicitly chooses Toolbox

px which <tool>
PX resolves the appropriate environment
```

## WINDOWS // TABS

WINDOWS owns live desktop-window and tab-level control.

The current implementation has distinct window and tab views.

Tab discovery currently has provider paths for environments including:

- Kitty remote-control tabs
- Chromium / Electron DevTools targets when a debug endpoint exists
- accessibility / AT-SPI-discovered application controls

The same AppControl family also contains application / window / tab audio state and policy machinery.

When giving tab instructions, identify the actual provider / application when that distinction changes what AppControl can do.

## REMOTE

REMOTE owns SSH-oriented remote targets.

Verified behavior includes:

- configured SSH targets
- known-host targets
- search
- SSH activation
- SFTP activation
- connection testing
- editing SSH configuration
- copying useful target text through the shared clipboard helper

REMOTE provider behavior is delegated to its controller; AppControl supplies the shared operator UI.

## THERMAL

THERMAL owns the temperature / fan monitoring and control surface.

Verified current UI includes:

- thermal sensor detail
- fan sensor detail
- `THERMAL LOAD`
- `FAN SPEED`
- `FAN CONTROL`

Do not assume all hardware exposes every control. Use the current sensor / controller state.

## KILL // TASK MANAGER // HUNTER

KILL owns process / task inspection and guarded process actions.

Verified task detail includes:

- CPU
- memory percentage
- RSS
- threads
- PID
- uptime
- CPU / memory history

Verified guarded actions include:

- restart process
- memory limit
- freeze / resume behavior
- terminate

Protected or dangerous targets use explicit unlock / confirmation machinery rather than silently executing destructive actions.

### HUNTER

HUNTER is a process-analysis / bulk-action view inside the KILL family.

Verified Hunter metrics include:

- combined score
- CPU
- memory
- I/O
- age

Verified visibility classes include:

- `TARGETS`
- `PROTECTED`
- `ALL`

Current code also has explicit candidate / confirmation flows for the operator-facing `KILL HOGS` and `KILL MICE` operations.

Treat those labels literally as AppControl operations rather than rewriting them into generic process-manager language.

## SYSTEM

SYSTEM owns system-component monitoring / control presentation.

Verified current UI includes:

- `UTILIZATION`
- component-specific metric presentation
- `SYSTEM CONTROL`
- `PROCESS / APP CONTRIBUTORS`

System categories include component-specific handling such as network and storage presentation.

Inspect the selected component's live control availability before promising an action.

## Destructive-action rule

AppControl has a dedicated destructive-confirmation surface.

Dangerous process / system operations must be described as guarded operator actions when the current UI requires confirmation or unlocking.

Do not instruct the user to bypass the existing safety surface with a raw command merely because the underlying primitive is known, unless the user explicitly requests the primitive or the UI path is unavailable / broken.

# NOTIFICATIONS

**Implementation owner:** [The Post-Apollo Project](https://github.com/kudokudo1/The-Post-Apollo-Project)

Notifications has two related operator surfaces:

```text
POPUP
active / transient notification presentation

NOTIFICATION HUB
persistent history / search / policy / app navigation
```

The dock button uses the visible icon:

```text
-⋆🗒⋆-
```

and toggles the Notification Hub.

## Popup behavior

The popup surface displays currently active notifications.

The backend accepts both ordinary and rich notifications, including structured fields such as:

- source / source ID
- title / message
- category
- severity
- tags
- metrics
- context
- actions
- live-state metadata

Source-wide snooze / DND policy can suppress new active popups without deleting the durable history.

## NOTIFICATION HUB

The current hub title is:

```text
NOTIFICATION HUB
```

Verified history controls include:

- `SEARCH HISTORY...`
- `ALL`
- `APPS`
- `SYSTEM`
- `SOCIAL`
- `APOLLO`
- `WARNING`
- `MANAGER`

Notification history is persisted by the service and is currently bounded to 300 retained entries.

Do not treat the popup list and durable history as the same thing.

## Card controls

Current notification cards expose:

- favorite `✦ / ✧`
- `ZZ` snooze
- `DND`
- `CLEAR ALL` for that source
- `×` dismiss for one notification
- `⇲` bring the source application to the current workspace / open it when needed

Card navigation also supports taking the operator to the source application.

The navigation path is deliberately non-destructive: it focuses / moves / launches the matching application and does not hide a kill / privileged operation inside notification navigation.

## Snooze

`ZZ` is source-wide popup suppression for a configured duration.

The current Manager presets are:

```text
1H
6H
12H
1D
3D
7D
```

Snooze is timed.

## DND

DND is persistent source-wide suppression until explicitly cleared.

The `MANAGER` view exposes:

```text
DO NOT DISTURB
ALLOW
```

for managing suppressed sources.

The backend persists notification policy separately from notification history.

## Notification actions

The service has an action router for structured notification actions.

Current routed action IDs include resource-oriented operations such as:

- open resource
- limit resource
- kill resource

Do not assume an arbitrary notification has those actions. Inspect the notification's actual structured action list.

## Visual-state note

Notification popup / Hub spacing, glow, opacity, and placement are active presentation details and may continue to be tuned.

Treat the behavioral contracts above as the stable operator map.

When diagnosing a visual complaint, inspect the current implementation rather than assuming this document freezes the exact current pixel geometry.


# MEDIA // AUDIO

**Implementation owner:** [The Post-Apollo Project](https://github.com/kudokudo1/The-Post-Apollo-Project)

Media and audio are related but not interchangeable control domains.

The current implementation has at least four distinct identities:

```text
PLAYBACK PLAYER
MPRIS / MPD transport target

MEDIA ITEM
track / title / loaded media

AUDIO STREAM
PipeWire / PulseAudio sink-input observation

DESKTOP OUTPUT
default output sink / combined desktop mix
```

Do not collapse these into one "current audio source."

A transport command can correctly target one player while a mute / volume mutation targets a different PipeWire stream.

That is a real architectural distinction, not automatically a bug.

## Current integration status // active development

The current `main` branch contains:

- `modules/Mediaplayer.qml`
- `widgets/MediaDeckW.qml`
- generic MPRIS transport support
- MPD transport support
- CAVA visualization
- PipeWire stream evidence / targeting experiments
- the extracted `ApplicationAudioService`
- the universal-media-controller architecture draft

At the current inspected `main` HEAD, `shell.qml` does **not** instantiate `Mediaplayer {}`.

An open integration PR currently proposes wiring that module into the taskbar.

That PR explicitly reports that the shell integration was not runtime-tested when opened.

Therefore:

> **The Hi-Fi implementation exists, but current remote `main` does not by itself prove that the dock is mounted in the running Taskbars shell.**

The operator may be testing newer or local runtime state.

Before making current-state claims about the Hi-Fi surface, re-check:

```text
current main
current integration PR / branch
live Quickshell state when available
```

Do not infer live integration from the presence of `MediaDeckW.qml`.

## HI-FI // MEDIA DECK

The current Hi-Fi prototype distinguishes two transport modes:

```text
LOCAL / MPD
MPRIS / EXTERNAL
```

MPD is currently the default transport mode.

MPRIS is opt-in.

### LOCAL / MPD

Current local transport uses `mpc`.

Verified transport actions are:

```text
PREV
PLAY
PAUSE
NEXT
-5 SEC
+5 SEC
STOP
```

The compact media module currently polls MPD state every two seconds.

Its MPD state and CAVA state are independent.

### MPRIS / EXTERNAL

The current external-player adapter uses generic MPRIS discovery.

It deliberately does **not** assume:

- Brave
- YouTube
- one particular browser
- one browser tab

The user explicitly selects the MPRIS player.

Visible current controls include:

```text
USE MPRIS
NEXT PLAYER
LOCAL / MPD
```

The adapter ignores `playerctld` relay instances so a relay is not mistaken for an independently addressable player.

Per-action capability checks currently gate:

- play
- pause
- stop
- previous
- next
- seek backward
- seek forward

Sending a supported MPRIS command means the command was issued.

It does **not** prove the remote player actually changed state.

Observed MPRIS state remains the evidence of what happened.

## Transport target != audio target

This distinction is critical.

```text
MPRIS target
→ which player receives PLAY / PAUSE / NEXT / SEEK

PipeWire target
→ which sink-input receives an audio experiment / mutation
```

The current Hi-Fi explicitly keeps these selections separate.

Do not assume that selecting a browser/player through MPRIS identifies a unique browser audio stream.

Do not assume that a matched PipeWire stream identifies a unique browser tab.

## Audio-stream evidence

The Hi-Fi currently consumes the extracted:

```text
services/audio/ApplicationAudioService.qml
```

as read-only stream physiology for its targeting experiment.

The service observes PipeWire/PulseAudio sink inputs through:

```text
pactl -f json list sink-inputs
```

Useful raw evidence includes:

```text
stream index
application.process.id
application.process.binary
application.id
application.name
media.name
```

These are observations.

They are **not** canonical media, application, window, or tab identity.

The extracted audio service owns:

- sink-input discovery
- descriptor-to-stream matching
- match evidence
- mute policy
- one-shot mute synchronization
- volume policy
- actual sink-input mute / volume mutation
- policy refresh machinery

It does not own semantic desktop identity or tab discovery.

## AUTO FOLLOW // evidence-gated targeting

Current Hi-Fi targeting uses:

```text
AUTO FOLLOW
```

as the default mode.

Automatic selection succeeds only when exactly one candidate PipeWire stream has a raw `media.name` that exactly matches the current MPRIS track title after narrow normalization.

The current resolver intentionally refuses generic titles such as:

```text
playback
audio
unknown
untitled
media
no track metadata
default
```

If there is no unique exact title match, AUTO FOLLOW fails closed.

Current statuses include relationships such as:

```text
EXACT MEDIA TITLE / TAB UNVERIFIED
MULTIPLE TITLE MATCHES / SELECT STREAM
NO EXACT TITLE MATCH / SELECT STREAM
NO MPRIS PLAYER
```

The system must **not** silently select the first browser stream.

A unique exact title match is still evidence only:

> **exact media title != certified browser-tab ownership**

## NEXT STREAM // explicit manual override

`NEXT STREAM` manually cycles through the current candidate PipeWire sink inputs.

A manual selection is bound to:

- current MPRIS bus name
- current media title
- stream index
- process ID / binary evidence
- application ID
- raw media name

The binding expires when the media session changes.

The current media-target resolver then returns to AUTO FOLLOW.

A disappearing / replaced stream becomes stale rather than silently selecting its neighbor.

Current manual status explicitly says:

```text
MANUAL STREAM / UNVERIFIED TAB
```

That wording is important.

Manual selection proves operator choice of a stream observation, not browser-tab identity.

## STREAM EVIDENCE // read-only diagnostic surface

When exact-title matching fails, the current empty cassette bay can show a temporary:

```text
STREAM EVIDENCE / READ ONLY
```

panel.

It displays up to three current candidate sink-inputs with evidence such as:

- stream index
- raw `media.name`
- application name
- binary
- PID

The purpose is comparison against the MPRIS media title.

It does not perform volume or mute mutation.

Treat that panel as diagnostic evidence.

Do not "fix" a mismatch by automatically choosing the first row.

## ARM TEST // temporary audio experiment

The Hi-Fi currently has an explicitly experimental audio-isolation bench.

Visible controls include:

```text
ARM TEST
NEXT STREAM
MUTE / 3S
VOLUME / 3S
```

The test requires an explicit resolved target and explicit arming.

Arming is consumed by the next experiment.

A changed media session or changed target requires re-arming.

The helper validates the selected stream fingerprint before mutation and before restoration.

Current tests:

```text
MUTE / 3S
→ temporarily mute selected sink-input
→ request restoration of prior mute state

VOLUME / 3S
→ temporarily halve selected sink-input channel values
→ request restoration of prior values
```

These are test-bench operations.

They are **not** certification that the permanent Hi-Fi has safe per-tab volume control.

If two browser tabs share one sink-input, both may change together.

That result means isolation failed for that path.

Even if only one tab changes in one experiment, the current test contract explicitly treats that result as promising evidence rather than universal proof of tab isolation.

## Current audio targeting safety rule

Use the current relationship:

```text
MPRIS player
        ↓
application / process evidence
        ↓
candidate PipeWire streams
        ↓
exact-title evidence OR explicit manual stream selection
        ↓
armed temporary experiment
```

Do not shorten this to:

```text
browser selected
→ mutate first browser stream
```

The latter is specifically disallowed by the current implementation.

## CAVA // current vs intended behavior

The compact media module currently launches its own CAVA process.

Its current CAVA configuration uses:

```text
PulseAudio-compatible input
source = auto
```

against the default desktop output.

Therefore the current visualizer represents the mixed desktop output, not isolated deck-owned media.

The architecture draft distinguishes future:

```text
CAVA Desktop
→ combined desktop output

CAVA Player
→ deck-owned audio only
```

That Player-only isolation is an intended architecture boundary, not a certified current implementation.

Do not describe today's CAVA as per-player isolated.

## DESKTOP VOLUME BAR

The ordinary taskbar Volume module is a separate control surface from the Hi-Fi.

It uses Quickshell's PipeWire service and targets:

```text
Pipewire.defaultAudioSink
```

Current direct controls are:

```text
right click
→ mute / unmute default sink

mouse wheel
→ change default sink volume by 5%
```

This is **desktop output volume**.

It is not the Hi-Fi's planned music-only volume.

Do not substitute one for the other.

## APPCONTROL AUDIO

AppControl currently has application / window / tab audio presentation and mutation behavior.

Current live donor code still performs direct `pactl` stream probing / mutation and maintains APP / WINDOW / TAB audio policy state internally.

The separately extracted `ApplicationAudioService.qml` also exists.

Therefore current audio architecture is **partially extracted but not fully unified**.

Do not assume every AppControl audio action already routes through the shared extracted service.

Before changing this seam:

1. inspect current AppControl audio donor code;
2. inspect the current extracted service;
3. inspect current identity/provider contracts;
4. preserve APP / WINDOW / TAB scope semantics;
5. avoid creating a third competing stream-mutation engine.

## APP / WINDOW / TAB audio identity

The audio service's central rule is:

> **matching evidence is not semantic identity**

APP, WINDOW, and TAB may all match the same sink-input.

They may also have distinct policy scopes.

A PID match is strong process-attachment evidence but is not persistent application identity.

A PipeWire sink-input index is ephemeral.

Provider-owned tab/window/application identity must come from the appropriate identity/discovery layer rather than being invented by the audio service.

This matters especially for browsers where:

```text
one MPRIS player
one browser process
one PipeWire stream
one browser tab
```

are not guaranteed to have a one-to-one relationship.

## UNIVERSAL MEDIA CONTROLLER // architecture draft, not current runtime

The repository also contains:

```text
MODEL/contracts/media-controller-v0-draft.md
```

Its current status is explicitly:

```text
Architecture draft
no executable implementation is certified by this document
```

The proposed future architecture separates:

```text
UI consumer
source/provider adapter
Universal Media Controller
playback-backend adapter
```

and separately models:

- Source
- MediaRef
- BrowseContext
- Selection
- LoadedMedia
- PlaybackSession
- VisualizationMode

Important intended rules include:

- browsing does not replace loaded media
- selection does not imply load
- load does not imply play
- source/provider identity does not equal playback backend identity
- player volume must not alter unrelated desktop/browser audio
- a future controller should not depend on Brave
- a running session must not silently switch backend or seize an unrelated player

These are architecture commitments / draft contract statements.

Do not describe the permanent universal controller, provider registry, YouTube browsing, isolated Player CAVA, or music-only volume as already implemented.

## Media guidance rule

For current Media / Audio work:

1. determine whether the question is about playback transport, media identity, audio stream identity, or desktop output;
2. do not infer one identity from another;
3. treat MPRIS state and PipeWire observations as evidence at their own layers;
4. use the Hi-Fi's explicit target / status text literally;
5. fail closed on ambiguous stream targeting;
6. use the taskbar Volume control for desktop output, not as a substitute for player-only volume;
7. re-check current `main`, active media integration work, and live shell state before modifying the rapidly changing Hi-Fi;
8. preserve the existing shared-audio-service boundary rather than adding another mutation backend.

# SOCIAL // SESSIONS // DISCORD

**Implementation owner:** [The Post-Apollo Project](https://github.com/kudokudo1/The-Post-Apollo-Project)

The Social surface is a shared messaging / communication window rather than a single application wrapper.

The dock entry is the Sessions image button.

Current visible application selector entries are:

```text
SESSIONS
DISCORD
TELEGRAM
```

These labels do **not** imply equal implementation maturity.

## Shared window model

The visible Social menu is a normal floating window so the existing Sway move / resize behavior can act on it.

Social maintains one shared geometry relationship for its communication surfaces.

For Discord, the current implementation keeps the real Vesktop window and the Social shell geometrically synchronized rather than pretending Discord is a native QML chat client.

When troubleshooting this surface, distinguish:

```text
Social shell
Sessions data / composer
Discord / Vesktop application
shared Sway geometry helper
```

## SESSIONS

SESSIONS is backed by the current Session bridge / adapter.

Verified adapter capabilities include:

- backend health
- conversation list
- message history
- conversation selection
- message send request
- background conversation refresh
- background message refresh

The contact surface exposes:

```text
CONTACTS
CONVERSATION(S)
```

and the messaging window has distinct app-selector, contact, and composer focus zones.

### Runtime-health rule

The existence of a send path in the UI / adapter is not proof that the external Session backend is healthy at this exact moment.

The adapter exposes backend / send / message errors explicitly.

Therefore:

> **Treat Sessions availability as runtime state.**

If the user reports that reading works but sending fails, do not erase that observation because a `sendMessage()` implementation exists.

Inspect the current bridge health / send error and treat the observed failure as evidence.

## DISCORD

DISCORD is currently integrated through Vesktop.

The Social surface can:

- launch Vesktop when needed
- move it through the Sway scratchpad lifecycle
- show / hide it with the Social selector
- synchronize its geometry with the Social shell
- keep a backing surface underneath it
- preserve the shared move / resize relationship

Current implementation identifies the Discord application by:

```text
app_id // vesktop
Flatpak // dev.vencord.Vesktop
```

The geometry follower uses persistent direct Sway IPC rather than repeatedly launching a shell polling pipeline.

This means a Discord-placement problem may belong to the shared geometry relationship rather than Discord itself.

## TELEGRAM

`TELEGRAM` is present as a visible selector entry.

Current activation code does **not** show a distinct Telegram backend / application lifecycle comparable to the real Sessions or Discord paths.

Treat Telegram as **present in the UI but not verified as a complete current integration**.

Do not tell the user that Telegram is working merely because its selector button exists.

# CPU++

**Implementation owner:** [The Post-Apollo Project](https://github.com/kudokudo1/The-Post-Apollo-Project)

CPU++ is the dedicated machine-monitoring surface.

The dock button uses the visible:

```text
🖥
```

icon.

Current top-level CPU++ modes are:

```text
FAVORITES
PROCESS
THERMAL
SYSTEM
```

The modes are not equally complete.

## THERMAL // working monitor surface

THERMAL is a current live monitor / control surface.

Its target submodes are:

```text
TEMP
FAN
```

It reuses the shared Post-Apollo thermal controller / view relationship rather than maintaining a second unrelated interpretation of temperature and fan state.

Verified UI concepts include:

- thermal sensor identity
- temperature state
- fan identity / RPM
- `THERMAL LOAD`
- `FAN SPEED`
- `FAN CONTROL`

Hardware-dependent fan mutation remains subject to the current controller / safety-lock availability.

Do not promise fan control for a sensor that does not expose it.

## SYSTEM // working monitor surface

SYSTEM is a current live machine-component monitor.

Current target categories include:

```text
ALL
CPU
MEM
GPU
DISK
NET
SWAP
```

The shared System Monitor presentation includes:

- utilization
- component metric / state
- system-control area where supported
- process / app contributors

CPU++ deliberately reuses the same System Monitor family used by AppControl instead of creating an independent competing telemetry model.

## FAVORITES // current shell, incomplete bay

The `FAVORITES` mode exists.

The current central content for this mode is still explicitly labeled:

```text
FAVORITES BAY
```

and does not yet contain the same completed monitor body as THERMAL / SYSTEM.

Treat this as a present surface with unfinished content.

## PROCESS // current shell, incomplete bay

The `PROCESS` mode exists.

The current central content is explicitly:

```text
PROCESS BAY
```

rather than a completed dedicated process monitor.

AppControl's KILL / Task Manager remains the verified detailed process-control surface today.

Do not redirect the user to CPU++ PROCESS for functionality that only exists in AppControl.

## CPU++ ACTUATORS // reserved, intentionally empty

The current UI contains a bay labeled:

```text
CPU++ ACTUATORS
```

The source explicitly states that the actuator bay is intentionally structurally empty and reserved for future controls that mutate machine state.

Therefore:

> **A visible actuator bay is not evidence that CPU++ currently exposes machine-state mutation there.**

Do not invent actuator controls.

## CPU++ ↔ AppControl relationship

Current CPU++ THERMAL / SYSTEM surfaces consume shared telemetry / control concepts also present in AppControl.

Useful current split:

```text
CPU++
→ dedicated machine-monitoring presentation

AppControl
→ broader desktop / application / process control surface
```

When both expose the same underlying monitor family, prefer the surface that best matches the user's intent rather than treating the duplicate presentation as conflicting truth.


# WEATHER STATION

**Implementation owner:** [The Post-Apollo Project](https://github.com/kudokudo1/The-Post-Apollo-Project)

Weather Station is a multi-domain environmental / celestial telemetry surface rather than a single temperature widget.

The dock button uses:

```text
🌡
```

and toggles the station.

The main title is:

```text
✦ WEATHER STATION ✦
```

## Domain model

Current domains are:

```text
GROUND
SKY
SPACE
```

Current view selectors are:

```text
HOME
MAP
NEWS
RADIO
TERMINAL
```

The domain and view are separate dimensions.

For non-HOME views, the station reports context in the form:

```text
<DOMAIN> // <VIEW>
```

## HOME // working telemetry

HOME is the current consolidated live telemetry view.

### SPACE

Verified current space-weather telemetry includes:

- `KP INDEX`
- `SOLAR WIND`
- `IMF BZ`
- `F10.7 FLUX`

The current Space service retrieves these from NOAA Space Weather Prediction Center endpoints.

The service tracks readiness of the individual feeds rather than treating a partial response as complete space telemetry.

### SKY

Verified current weather / atmospheric telemetry includes:

- temperature
- feels-like temperature
- condition
- condition icon
- air quality
- humidity
- wind

Current weather data is fetched from `wttr.in`.

Current air-quality data is fetched from the Open-Meteo air-quality API after coordinates are available.

The weather service can allow `wttr.in` to resolve location when no explicit location is configured, then reuse returned coordinates for the air-quality request.

### GROUND

Verified current ground / environmental telemetry includes:

- air quality
- PM2.5
- PM10
- latitude / longitude position display

GROUND and SKY deliberately overlap on some environmental data because they present different operator contexts.

## TERMINAL // STAR MAP // working integration

The current TERMINAL view is a real external terminal integration rather than a placeholder.

It launches a dedicated Kitty window with:

```text
app_id // weather-screen
title  // STAR MAP
```

using the Weather Station Kitty configuration and the current:

```text
weatherstation-starmap
```

program.

The Weather Station then synchronizes that Kitty window into the terminal bay through Sway geometry.

Current visible terminal states include:

- `IDLE`
- `STARTING`
- `VISIBLE`
- launch / start / sync error states

Visible controls include:

```text
[ STAR MAP ]
[ CLOSE ]
```

Treat Star Map launch / geometry failures as a relationship between Weather Station, Kitty, the Star Map program, and Sway—not automatically as a weather-data failure.

## MAP // NEWS // RADIO // current placeholders

The selectors:

```text
MAP
NEWS
RADIO
```

exist in the current UI.

Their present view bodies explicitly report:

```text
map display offline...
news receiver offline...
radio receiver offline...
```

Therefore these are **reserved / visible but not currently implemented receiver views**.

Do not describe them as working features because their buttons exist.

## Focus behavior

Weather Station takes exclusive keyboard focus while open.

This is intentional current behavior.

If keyboard interaction elsewhere appears blocked while the Station is open, first check whether Weather Station still owns focus before treating the other application as unresponsive.

## Guidance rule

For a request that is already represented in Weather Station:

1. use the Weather Station route first;
2. distinguish the active domain;
3. distinguish HOME telemetry from MAP / NEWS / RADIO placeholders and the separate TERMINAL Star Map;
4. use raw weather / NOAA / shell primitives only when the Station does not expose the needed operation or when diagnosis requires them.

Do not replace the current station with a generic `wttr.in` terminal command merely because that service backs part of the station.

# ADDITIONAL POST-APOLLO SURFACES

Additional Post-Apollo operator surfaces should be added here as they become relevant.

Document them from their current implementation rather than inferring capabilities from names, placeholders, or planned UI.

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
- Post-Apollo SwayPx
- Post-Apollo Sway Config
- Post-Apollo Pretty Kitty
- Post-Apollo CRT-TV
- Post-Apollo Zellij
- Post-Apollo Oh My Apollo
- Post-Apollo Astro Snacks
- The Post-Apollo Project media / audio services and Hi-Fi prototype

Technical behavior remains canonical in the repository that owns it.

When this guide drifts from the live implementation, inspect the implementation and report the drift rather than silently pretending the guide is current.
