✦︎✦︎✦︎ Meta Apollo Logos //

# 🖳 OPERATE // COMMAND ENVIRONMENT

![](../BUILD/assets/design/chassis/system-rail.svg)

> **STATE //** active \~\~ **VIEW //** shell / environment conventions

This is the current-facing operational version of the preserved shell-command convention source.

## FEDORA HOST // NORMAL COMMAND LANGUAGE

Treat these mappings as intentional:

```text
grep → rg
cat  → bat
ls   → eza
vim  → nvim
```

Do not repeatedly diagnose or "correct" these mappings.

Prefer commands that work naturally in the user's normal host environment.

## EXACT-SEMANTICS EXCEPTION

If exact GNU/coreutils behavior matters, use the explicit binary path rather than assuming an alias or replacement is equivalent.

Examples:

```bash
/usr/bin/grep
/usr/bin/cat
/usr/bin/ls
```

Use this only when the exact behavior materially matters.

## TOOLBOX / CONTAINER

Do not assume the host's aliases, functions, packages, or paths exist inside Toolbox or another container.

When command resolution matters:

- identify whether the command is running on host or container
- verify tool availability
- use explicit commands when necessary

## POST-APOLLO OPERATOR RULE

A shell command is not automatically the preferred human interface.

If the user's Post-Apollo UI already exposes the requested operation, explain the UI/control-surface route first.

Use CLI for:

- diagnostics
- exact inspection
- automation
- recovery
- capabilities not yet present in the UI
- cases where the user explicitly asks for commands

## SOURCE

Preserved origin:
[dump/0.5-shell-command-conventions.md](../dump/0.5-shell-command-conventions.md)
