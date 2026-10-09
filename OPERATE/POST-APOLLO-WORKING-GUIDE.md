✦︎✦︎✦︎ Meta Apollo Logos //

# 🖳 OPERATE // POST-APOLLO WORKING GUIDE

![](../BUILD/assets/design/chassis/agency-rail.svg)

> **STATE //** active \~\~ **VIEW //** Post-Apollo development policy

This document defines the default working policy for AI agents, collaborators, and operator-facing tools modifying Post-Apollo systems.

It is user-approved policy.

The technical implementation details remain canonical in the repositories that own them. This document defines how to approach that work.

## 1 // PREFLIGHT BEFORE MEANINGFUL EDITS

Before a meaningful Post-Apollo code change, inspect enough current state to know:

- repository
- branch
- exact HEAD
- relevant architecture / contracts
- current ownership
- concurrent work that may collide
- the immediate requested scope

Tiny isolated fixes may use a lightweight preflight, but they do not skip knowing what state they are touching.

Do not assume an earlier branch, handoff, or chat context is still current.

## 2 // REUSE BEFORE INVENTION

Before creating a new:

- component
- service
- provider
- visual primitive
- store
- workflow
- control surface
- architectural abstraction

inspect the relevant project for an existing one.

Reuse existing machinery when it actually fits.

Do **not** force reuse when doing so would corrupt the abstraction, blur ownership, or make the architecture worse.

The rule is:

> **Look first. Reuse when the relationship is actually the same.**

## 3 // SCOPE EXPANSION MUST BE REPORTED

If a requested local fix exposes a broader problem in:

- a shared component
- a shared service
- a provider
- architecture
- ownership
- a shared seam
- another subsystem

do not silently widen the implementation scope.

Report:

- what was discovered
- why the broader change appears necessary
- what would be affected
- what options exist

Then wait for the user to decide whether the broader work becomes part of the task.

## 4 // OWNED OR SHARED COLLISIONS

If another doctor, chat, room, or active workstream owns the file or seam you need:

- do not interfere with that owned tissue
- continue only genuinely isolated adjacent work
- leave the shared seam untouched
- report the collision
- report what remains blocked by it

Do not overwrite active work merely because your change is also valid.

## 5 // HOSPITAL IS THE DEFAULT COORDINATION LAYER

Post-Apollo work should remain Hospital-compatible by default unless the user explicitly says otherwise.

Hospital is not reserved only for large surgery.

A chat may be organized as:

- a numbered doctor
- a numbered team
- a named room
- a room named after the file being worked on
- a room named after the patient / subsystem / task

These forms are all allowed to participate in the Hospital coordination model.

A room should remain able to:

- communicate with Hospital
- report state
- hand off evidence
- transfer work
- expose ownership
- surface collisions
- escalate into larger or mass surgery when necessary

The room naming scheme does not determine whether the work is Hospital-compatible.

## 6 // TEST EACH STEP

Each implementation step should automatically run the relevant test or check appropriate to that step when such verification is available.

Intermediate states may truthfully be described as:

- implemented
- automated checks passing
- verified by automation
- landed
- ready for operator review

Do not collapse those states into final acceptance.

## 7 // FINAL DONE BELONGS TO THE USER

Final **DONE** is a human acceptance state.

A task is not finally closed until the user confirms it, commonly through:

- a screenshot
- runtime observation
- direct testing
- an explicit "okay"
- another clear statement of acceptance

If the implementation is technically working and the user stops discussing it, assume one of these possibilities instead of inventing final acceptance:

- they forgot about it
- attention moved elsewhere
- it is done enough for now
- they intend to return later

Keep the task recoverable.

Do not silently convert inactivity into permanent completion.

## 8 // RELATIONSHIP ACCOUNTING IS NORMAL DEVELOPMENT BEHAVIOR

While working on Post-Apollo, keep track of:

- what relationship changed
- what was preserved
- what was gained
- what was lost or traded
- how the result was verified

This is not only PR ceremony.

The amount of reporting may scale with the size of the change, but the conceptual check is part of normal development.

## 9 // TECHNICAL FACTS REMAIN OWNED BY THEIR SYSTEMS

This working guide does not replace canonical project contracts.

Current important relationships include:

- **Meta Apollo Logos** owns governing principles and repository design grammar.
- **Taskbars // Post-Apollo** owns the live desktop implementation, components, services, modules, widgets, and runtime-sensitive paths.
- **Git / GitHub providers** report repository and automation facts.
- **Hospital** decides surgical meaning, readiness, certification, and coordination policy.
- **PX / Dev Experience** performs the operations assigned to its control-plane role.

When a technical contract and this guide appear to disagree, inspect the current canonical implementation / contract and report the conflict rather than silently choosing one.

## 10 // DEFAULT WORKING LOOP

```text
reconstruct current state
→ check ownership / collisions
→ inspect existing components / services
→ implement only approved scope
→ auto-test the step
→ report broader discoveries instead of silently expanding
→ preserve Hospital compatibility
→ report relationship change + evidence
→ await operator acceptance for final DONE
```

## SOURCE RELATIONSHIP

This policy was assembled from:

- user-approved rules defined during current How I Think operator-interface work
- Meta Apollo governing principles
- Meta Apollo repository design language
- Taskbars runtime architecture
- Hospital certification and operating-authority contracts
- Git / GitHub evidence boundaries
- existing Post-Apollo PR / verification practices

The user-approved policy in this document governs collaboration behavior. Technical implementation details remain canonical in their owning repositories.
