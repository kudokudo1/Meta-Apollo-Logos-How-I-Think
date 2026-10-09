✦︎✦︎✦︎ Meta Apollo Logos //

# 🖳 OPERATE // DESKTOP LIFECYCLE

![](../BUILD/assets/design/chassis/system-rail.svg)

> **STATE //** active ~~ **VIEW //** startup / ownership / health / recovery boundaries

This document maps the current Post-Apollo desktop lifecycle.

It answers a different question from the control-surface catalog:

> **What owns the desktop at each layer, what starts what, and how much of the system is actually unhealthy when one thing fails?**

Technical implementation remains canonical in the repositories that own it.

## 1 // STARTUP CHAIN

The verified current chain begins once the Sway / SwayPX session is running.

The repository evidence inspected here does **not** establish which login/session launcher starts that compositor process, so do not invent that layer.

From Sway onward:

```text
SwayPX compositor
        ↓
Post-Apollo Sway Config
        ↓
exec_always
        ├── kill old Quickshell
        ├── start Quickshell
        └── start autotiling
                ↓
Quickshell shell.qml
        ↓
bar + windows + shared services
        ↓
feature-specific backends / helpers
```

The current Sway Config launches Quickshell with:

```text
pkill -x quickshell
quickshell >/tmp/quickshell.log 2>&1 &
```

and separately launches:

```text
/var/home/mapple/.local/bin/autotiling
```

These are `exec_always` entries.

That means a Sway config reload applies them again.

## 2 // LOGIN AND LOCK BOUNDARY

The current login/session entry is the default Silverblue login path.

That login surface is not currently a custom Post-Apollo component.

The current manual lock path is different.

The Post-Apollo Power menu already exposes:

```text
Lock
```

and the current implementation executes:

```text
swaylock
```

So the present relationship is:

```text
default Silverblue login
        ↓
SwayPX session
        ↓
Post-Apollo desktop

manual lock request
        ↓
Post-Apollo Power → Lock
        ↓
swaylock
```

This means the **lock trigger is already part of Post-Apollo**, while the lock-screen runtime itself is still Swaylock rather than a custom Post-Apollo lock surface.

Do not describe the desktop as having no lock behavior.

Do not describe Swaylock as a custom Post-Apollo lock screen unless that implementation actually exists.

## 4 // SWAY RELOAD HAS A QUICKSHELL BLAST RADIUS

Because the current session config uses `exec_always` and explicitly kills Quickshell before starting it:

```text
reload Sway config
        ↓
Quickshell is killed
        ↓
Quickshell starts again
        ↓
shell-local runtime state is reconstructed
```

A Sway config reload is therefore **not** a zero-impact configuration reread for the Post-Apollo shell.

Do not recommend it casually when the problem belongs to one widget or service.

The current keyboard route is:

```text
Mod+Shift+r
→ reload Sway configuration
```

Use it only when changing / reapplying Sway session policy actually matters.

Local reload / restart remains a live-machine mutation and requires the appropriate approval.

## 4 // QUICKSHELL DOES NOT HOT-RELOAD SOURCE CHANGES

Current `shell.qml` explicitly sets:

```text
Quickshell.watchFiles = false
```

The source comment records the reason: automatic QML file watching had repeatedly reloaded partially updated graphs while shader-backed items were detaching and crashed QtQuick.

Therefore:

> **Repository state is not live-shell state.**

Editing / merging QML does not prove the currently rendered shell contains that change.

The current intended apply model is:

```text
edit source
→ verify source
→ explicitly restart Quickshell when authorized
→ inspect the new live runtime
```

Do not claim a Taskbars visual or runtime fix is live merely because the repository changed.

## 5 // QUICKSHELL ROOT OWNERSHIP

Current `shell.qml` is the long-lived Taskbars root.

It owns / instantiates:

- the top bar
- AppControl
- Hospital
- Git
- CPU++
- Weather Station
- Social / Sessions
- Notifications
- power / clock / workspace / network / Bluetooth / volume modules
- shared Weather service
- shared Space Weather service
- shared System Telemetry
- shared Fan Control

The shell deliberately shares one System Telemetry / Fan Control stack between AppControl and CPU++ rather than starting competing hardware-monitor stacks.

This is an important lifecycle distinction:

```text
one Quickshell process
        ↓
one shell root
        ↓
many surfaces
        ↓
some shared services
some surface-owned services
some external helper processes
```

A failure in one child service is not automatically a failure of the shell root.

## 6 // ALWAYS-ON OR BOOT-ACTIVE SHELL WORK

Some work begins when the shell graph is instantiated rather than waiting for the user to open a menu.

### WEATHER

Weather service:

```text
shell start
→ immediate refresh
→ refresh every 15 minutes
```

### SPACE WEATHER

Space service:

```text
shell start
→ immediate refresh
→ refresh every 5 minutes
```

Its readiness is composite: Kp, solar wind, magnetic field, and solar flux each have their own ready state.

### NETWORK

The Network module starts its probes on component completion and currently polls at:

```text
500 ms
```

for Wi-Fi / link / Ethernet state.

### NOTIFICATIONS

Notifications is a Quickshell singleton with a live `NotificationServer`.

It also maintains persistent:

- history
- source policy
- snooze / DND policy

through Quickshell data files.

Transient active notification state and persistent history / policy are not the same lifecycle.

### SESSIONS BACKEND

The Social surface instantiates its Session adapter with the shell.

On component completion the adapter:

- runs a backend health probe
- loads the conversation list

It then refreshes conversations every:

```text
5 seconds
```

and, when a conversation is selected, refreshes its messages every:

```text
3 seconds
```

The Social Discord geometry helper process is also created as a long-lived helper, while active geometry watching is enabled / disabled according to the Social menu state.

## 7 // MENU-GATED / DEMAND-GATED WORK

Other work intentionally becomes active only when its surface is being used.

### CPU++

CPU++ shared thermal / system telemetry refresh currently runs every:

```text
1.9 seconds
```

only while CPU++ is open in THERMAL or SYSTEM mode.

### GIT

Git's GitHub page has a repeating refresh every:

```text
15 seconds
```

only while:

```text
Git menu open
AND
active page = GitHub
```

### HOSPITAL

Hospital's remote watcher is active only when the Hospital menu is open and the selected bed / integration state permits probing.

Attention / merge-queue refresh timers are likewise gated by the relevant open Hospital view.

### APPCONTROL

AppControl starts / schedules much of its probe work when the menu opens.

Its shared monitor refresh can remain active outside the visible THERMAL / SYSTEM screen when monitor favorites require continued state.

Do not assume "menu closed" means every supporting timer or piece of state vanished.

## 8 // ON-DEMAND EXTERNAL APPLIANCES

Several Post-Apollo surfaces are not core desktop daemons.

They exist only when launched or selected.

### PRETTY KITTY

A normal terminal launch starts Kitty and enters / creates the persistent Zellij:

```text
main
```

session through the Pretty Kitty wrapper.

Pretty Kitty not being open does not mean the desktop is unhealthy.

### CRT-TV

CRT-TV is launched separately through:

```text
post-apollo-tv
```

Its Kitty terminal, receiver deck, side panel, and geometry follower are appliance-local lifecycle pieces.

### WEATHER STAR MAP

Weather Station starts the dedicated `weather-screen` Kitty window only when the Star Map terminal view is requested.

Closing that terminal view kills that dedicated window.

### DISCORD

Social launches / reveals Vesktop when the Discord surface is selected.

Discord failure is not equivalent to Social, Quickshell, or Sway failure.

## 9 // HEALTH IS LAYERED

Do not reduce desktop health to one boolean.

Use these layers.

### LAYER 1 // COMPOSITOR HEALTH

Sway / SwayPX owns:

- outputs
- workspaces
- focus
- window placement
- input routing
- compositor animation / effects
- Sway IPC

If these relationships fail broadly, investigate the compositor / session layer.

### LAYER 2 // SHELL HEALTH

Quickshell owns the Post-Apollo bar and most desktop control surfaces.

A healthy compositor with a missing / failed Quickshell root is:

```text
COMPOSITOR HEALTHY
SHELL DOWN
```

not "the entire desktop is dead."

### LAYER 3 // SHARED SERVICE HEALTH

Examples include:

- Network probe
- Notifications server / persistence
- Weather / Space data
- System Telemetry
- Fan Control

One of these can be degraded while the rest of Taskbars remains healthy.

### LAYER 4 // FEATURE BACKEND HEALTH

Examples include:

- PX
- GitHub
- Hospital provider
- Session bridge
- Discord / Vesktop
- external weather feeds

A feature backend can be unavailable while the shell and other surfaces continue working.

### LAYER 5 // APPLIANCE HEALTH

Examples include:

- Pretty Kitty
- CRT-TV
- Weather Star Map
- one special floating Kitty surface

These should be debugged as their own composed systems before escalating the failure to the desktop as a whole.

## 10 // OBSERVED STATE IS HEALTH EVIDENCE

Visible Post-Apollo state is often intentional telemetry.

Examples:

```text
Pretty Kitty // NO SIGNAL
Session backend // ERROR
Weather link // OFFLINE
Star Map // START ERROR
PX // STALE / MISSING
notification history // load-error / save-error
```

Treat these as literal observations.

Do not begin by explaining away the state as user confusion.

At the same time:

> **Observed state identifies a failed relationship; it does not automatically identify the root cause.**

Use it to choose the correct ownership layer.

## 11 // FAILURE SCOPE BEFORE RESTART

Before restarting anything, classify the failure.

```text
one card wrong
→ inspect that surface

one backend unavailable
→ inspect that backend

one Quickshell service broken
→ inspect that service / shell relationship

whole Taskbars shell absent or failed to load
→ inspect Quickshell

window / workspace / output behavior broadly broken
→ inspect Sway / SwayPX
```

Do not jump directly to:

```text
restart Quickshell
restart Sway
reboot
```

when a smaller owner exists.

A restart is an intervention, not a diagnosis.

## 12 // RESTART BOUNDARIES

### Restarting one helper / backend

Smallest blast radius when that helper is actually the owner.

Examples may include an application-specific geometry helper or external provider.

### Restarting Quickshell

Reconstructs the entire shell graph:

- bar
- windows
- shell-local services
- timers
- adapters
- in-memory UI state

Persistent stores may reload where implemented, but do not assume every transient state survives.

Current Quickshell stdout / stderr from Sway startup goes to:

```text
/tmp/quickshell.log
```

Inspecting that log can be useful when the shell fails to instantiate.

### Reloading Sway config

Current config also restarts Quickshell because of its `exec_always` startup rule.

This has a larger blast radius than changing one Taskbars surface.

### Restarting / exiting Sway

Affects the compositor session itself.

Treat it as a much larger intervention than a Quickshell restart.

## 13 // AUTOTILING IS A SEPARATE SESSION HELPER

Current Sway Config launches:

```text
/var/home/mapple/.local/bin/autotiling
```

through `exec_always`.

Autotiling is not Quickshell and is not SwayPX compositor code.

If automatic split behavior fails while:

- Sway still places windows,
- workspaces still work,
- Taskbars still works,

inspect the autotiling helper relationship before blaming the compositor.

The current Sway config does not itself document a duplicate-process guard for repeated `exec_always` launches, so do not invent its exact reload behavior without live inspection.

## 14 // LIVE STATE VS SOURCE STATE

For desktop work distinguish at least:

```text
repository source
        ≠
installed / local source
        ≠
running process
        ≠
rendered / observed behavior
```

Examples:

- merged Taskbars QML may not yet be running
- current Sway config may differ from the repository baseline
- current monitor identity may differ from stored output names
- a backend implementation may exist while the backend is currently unhealthy
- a button may exist while its action remains unwired

Verification should happen at the layer being claimed.

## 15 // DEFAULT DIAGNOSTIC ORDER

For a desktop/runtime complaint:

```text
1. record the literal observed state
2. identify the smallest owning layer
3. distinguish source from live runtime
4. inspect that layer's own status / error / log
5. inspect adjacent dependencies only if needed
6. choose the cheapest discriminating test
7. restart only the smallest justified owner, if authorized
8. verify the observed relationship changed
```

This is the desktop-lifecycle version of the general Ghost / relationship-debugging rule.

## 16 // AUTHORITY

Reading current Sway IPC state, logs, repository source, and exposed health fields is diagnostic inspection.

Changing:

- local QML
- Sway config
- installed compositor code
- user services
- running processes
- Quickshell process state
- Sway process state

is local-machine mutation.

Follow [AUTHORITY AND PERMISSIONS](./AUTHORITY-AND-PERMISSIONS.md).

## SOURCE RELATIONSHIP

Current implementation facts were reconstructed from:

- [Post-Apollo Sway Config](https://github.com/kudokudo1/Post-Apollo-Sway-Config)
- [Post-Apollo SwayPx](https://github.com/kudokudo1/Post-Apollo-SwayPx)
- [The Post-Apollo Project](https://github.com/kudokudo1/The-Post-Apollo-Project)
- [Post-Apollo Pretty Kitty](https://github.com/kudokudo1/Post-Apollo-Pretty-Kitty)
- [Post-Apollo CRT-TV](https://github.com/kudokudo1/Post-Apollo-CRT-TV)

The repositories that implement these systems remain canonical for their technical behavior.
