✦︎✦︎✦︎ Meta Apollo Logos //

# 🖳 OPERATE // AUTHORITY AND PERMISSIONS

![](../BUILD/assets/design/chassis/warning-rail.svg)

> **STATE //** active \~\~ **VIEW //** actuation boundary

This document separates conversation from authority.

The central rule is:

> **Capability is not permission.**

## 1 // INTENT STATES

Treat these as different states:

| STATE | MEANING |
|---|---|
| **DISCUSS** | talk about the thing |
| **ARCHITECT** | design / compare / reason about possible structure |
| **PLAN** | define intended work and sequencing |
| **INSPECT** | read / observe / diagnose without mutation |
| **IMPLEMENT** | make bounded approved changes |
| **DESTRUCTIVE / SYSTEM** | alter live state with elevated recovery risk |

Do not silently promote DISCUSS, ARCHITECT, PLAN, or INSPECT into IMPLEMENT.

## 2 // LOCAL MACHINE

A connected local machine is a live environment.

Inspection may proceed when the task calls for it.

**Any local write or mutation requires explicit approval for that change.**

Examples:

- editing a local file
- changing live configuration
- installing or removing packages
- moving or deleting files
- changing permissions
- killing or restarting services
- restarting or reloading Quickshell
- changing the live Git worktree through pull, reset, checkout, rebase, clean, or similar operations

A prior approval does not silently authorize the next unrelated mutation.

When local work is approved:

- preserve the current live state
- change only the approved scope
- avoid unrelated cleanup
- verify the resulting diff / state
- report what changed

## 3 // LIVE QUICKSHELL

Treat the live Quickshell tree as an operating surface, not merely source code.

Do not casually:

- pull from another source
- reset local changes
- switch branches
- overwrite concurrent work
- reload / restart the shell

The user may have several active chats or tools modifying adjacent areas.

Reconstruct current local state first.

## 4 // GITHUB / REMOTE REPOSITORIES

GitHub work is more recoverable because branches, commits, diffs, PRs, and history provide rollback.

When the user clearly asks to:

- fix
- implement
- continue
- land
- merge
- patch

bounded repository work may proceed using the established branch / test / PR workflow.

When the user is only exploring architecture or asking what should happen, remain non-mutating.

## 5 // CANONICALITY

An agent may not silently declare its own proposal canonical.

A proposal becomes canonical through the user's authority and/or the project's established acceptance path.

Do not:

- rewrite governing principles without approval
- silently change permission models
- convert provisional language into frozen definitions
- erase provenance to make a cleaner story
- self-approve disputed interpretations

## 6 // CONCURRENT AGENTS

Before writes in an active project:

- re-check current head / branch / shared seam
- identify likely ownership collisions
- avoid unrelated hotspots
- preserve other agents' landed work
- report collisions rather than overwriting them

## 7 // APPROVAL IS SCOPED

"Go ahead" authorizes the immediately established task scope.

It does not imply unlimited authority over:

- the rest of the repository
- the local machine
- adjacent projects
- future architectural ideas
- unrelated cleanup
- destructive operations

If the next action materially changes the risk or target, ask again.

## 8 // REPORT AFTER ACTUATION

After meaningful mutation, report:

- target
- action
- evidence
- resulting state
- remaining uncertainty
- rollback / recovery information when relevant

## SOURCE RELATIONSHIP

This file generalizes the authority model already visible in Forest's Bristlecone `AGENTS.md`, the preserved How I Think working protocols, and explicit local-machine boundaries established during current Post-Apollo work.
