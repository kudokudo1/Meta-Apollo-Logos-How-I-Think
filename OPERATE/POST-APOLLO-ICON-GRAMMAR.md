✦︎✦︎✦︎ Meta Apollo Logos //

# 🖳 OPERATE // POST-APOLLO ICON AND SYMBOL GRAMMAR

![](../BUILD/assets/design/chassis/focus-rail.svg)

> **STATE //** operator-reviewed / living ~ **VIEW //** icon semantics, construction, interaction and provenance

This is the operator-approved **symbol-language contract** for Post-Apollo. It is a permanent external reference for humans and agents, written in the same **semantic recipes / exceptions / rollout boundaries** spirit as the [Post-Apollo color and visual-language recipes](https://github.com/kudokudo1/The-Post-Apollo-Project/blob/main/MODEL/components/visual-language-recipes.md).

**Authority split:** The operator owns meaning and exceptions. This document owns the *record of those decisions*. The [Post-Apollo Project](https://github.com/kudokudo1/The-Post-Apollo-Project) owns QML implementation and actual runtime behavior. Do not infer that a selected glyph is already in production, that the text below overrides a live font/layout, or that this documentation authorizes a mass migration.

**Continuity:** Nurse 3a (Apollo) remains the standing icon/symbol-grammar nurse. Head Nurse .C coordinates Hospital reporting and inter-worker ownership. The first inventory pass is a baseline, not a discharge or a claim of exhaustive coverage.

## 1 // NON-NEGOTIABLE DISTINCTIONS

**An icon is a relationship, not necessarily one character.**

| Layer | What to preserve | Example |
| --- | --- | --- |
| Core | Recognizable semantic identity | Media `𝄞` |
| Decorated / full | Deliberately composed ornamentation | Media `‧₊˚ 𝄞˖` |
| Compact / contextual | Same family in a smaller or different slot | Thermal `🌡` beside full `₊˚⊹🌡 ๋࣭⭑` |
| Multi-element construction | Independent text items, sizes, offsets and effects | Unavailable Volume face: left `ᓬ(｡•́︿•̀｡)`, right `ᕒ` |
| Reactive / animated | Meaningful expression stages and their triggers | Favorites: default, blink, hover/click |
| Action / status | What the control *does*, separately from how a glyph looks | Kill action vs Close/Remove vs warning |
| Identity / state | Semantic foreground/glow and interaction fill are separate | Specialized icon may retain its own color while selected |

Do **not** flatten decorated glyphs, individually sized pieces, relative anchors, glow layers, Unicode combining marks, or animated variants into one generic symbol. A compact glyph remaining in source is **not** evidence that its larger family was rejected.

Source text is not a visual proof. GohuFont, NotoText, fallback fonts, zero-width/combining characters, Markdown escaping, animation, spacing and clipping can change the rendered image. Verify the **original QML construction and live screen** before declaring a glyph corrupt. Preserve literal code points when recorded; do not normalize lookalikes by eye.

## 2 // CORE AND DECORATED IDENTITY RECIPES

| Family / surface | Operator-reviewed identity | Context and boundary |
| --- | --- | --- |
| Applications | `-⋆♱⋆-` | AppControl / launcher |
| Favorites | `(˵✧ᴗ✧˵)` | Default face only; animation below |
| Files | `🗄` | Intentionally reused for GitHub Library |
| RUN / command | `⌯✎﹏﹏` | RUN action may add `RUN COMMAND` |
| Windows | `🃁🂡🂱🃑` | Windows → Tabs selector separately `♤ ⚄` |
| Remote / SSH | `⌁⋆˚☾⭒` | Full icon for REMOTE main, Config selector, selected detail identity, and Connect action; preserve `⌁` only for the unavailable-tab fallback |
| Thermal | `₊˚⊹🌡 ๋࣭⭑` | Compact `🌡` retained; Weather may reuse `🌡` |
| Process / main Kill | `(-_•)︻デ═一` | Long gun; three reactive stages required |
| System | `🖳` | AppControl / CPU++ |
| CPU / Memory / GPU / Disk | `` / `` / `󰢮` / `` | CPU++ metrics |
| SWAP | `⇄` | CPU++ compact **retained**; GitHub PR use has different replacement |
| Network | `🛰` | Satellite is the core of staged Wi-Fi compositions |
| Fan | `✇` | Compact, `【✇】` or a composed fan identity |
| Taskbar Hospital / CPU++ / Notifications | `⚚` / `🖥` / `-⋆🗒⋆-` | Different dock purposes |
| Power / Clock | `⏻` / `🕰` | Clock may be reused as age metric |
| Calendar | `⌯⌲ 🗓 ⋆˙⟡` | Full composition; `🗓` is valid compact core |
| Media | `‧₊˚ 𝄞˖` | Decorated full icon; core `𝄞` is not the whole source artwork |
| Bluetooth | `(˓✟˒)` | Taskbar |
| Hospital phone / intercom / reports / attention | `☎︎` / `🎙︎` / `🗒︎` / `⚠︎` | Distinct functions |
| Combi / Search / Display | `°⋆ꙮ๋࣭⭑.` / `🔎︎` / `󰍹` | Their specific contexts |
| Close / Remove | `×` | **U+00D7**, not `x`, `X`, `✕` or `✖` |

Shared characters can have **intentionally different contextual meanings**: `🗄` (Files/Library), `🛠` (Toolbox/Local Control), `🌡` (Thermal/Weather), `⚠︎` (attention/protected/risky), and `⇄` (CPU++ SWAP versus old PR artwork). Do not treat these as automatic collisions.

## 3 // SELECTED GIT / GITHUB AND SSH MAPPINGS

The following are **operator-chosen target identities, not proof of implementation**. Preserve Git's main cat `≽(•⩊•マ≼` as a separate identity from Kitty `≽(^•⩊•^)≼`. Branch decoration can sit beside the Git cat without replacing it.

| Function | Target icon | Previous / note |
| --- | --- | --- |
| Local Control | `🛠` | `◎` |
| Branches | `` | `⇶`; also branch decoration |
| Changes / Diff | `⚖` | `Δ` |
| History | `࣪⋅˚🕮‧₊˚` | `◴` |
| Repository | `ﮩ٨✮ﮩ٨ـ` | `◇` |
| Operations | `🏗` | `↶` |
| GitHub Profile | `✮˙๋࣭⭑` | `◇` |
| GitHub Library | `🗄` | `▤` |
| GitHub Control / Workflows | `🖨` | New separate semantic assignment |
| GitHub Projects | `🗠` | `⌗` |
| GitHub Pull Requests | `◀~~~~~~~~▶` | `⇄`; **no literal backslashes** from Markdown transfer |
| GitHub Issues | `⭒˗ˏˋ๋࣭⚠︎๋࣭⭑ˊ˗` | `!` |
| AppControl SSH / Remote | `⌁⋆˚☾⭒` | `⌁ ssh` |

The eight visible tildes in the recorded PR design are the preserved decision-register transcription; verify the final font rendering and operator's intended width before implementation. **Operator clarification (2026-10-11):** All four SSH-specific placements use the **full** `⌁⋆˚☾⭒`: main REMOTE icon, `⌁⋆˚☾⭒ CONFIG` selector, selected Remote detail artwork, and CONNECT action. Retain exactly `⌁` for the **unavailable-tab fallback**, which is not an SSH control. Leave distinct Remote actions such as SFTP/Copy SSH Command unchanged. [Post-Apollo PR #181](https://github.com/kudokudo1/The-Post-Apollo-Project/pull/181) proposes the QML migration; source and runtime acceptance remain separate.

## 4 // APPCONTROL CONTEXTUAL ACTION RECIPES

Different surfaces can deliberately express the same verb with different artwork.

| Role | Verified source identity or composition | Distinction |
| --- | --- | --- |
| Normal Launch selector | `⌯♱ ๋࣭⭑` | Selector, also used with `LAUNCH` action |
| Flatpak source selector | `⋆˙⟡ ⌯⛟` | Different from launch action; icon-only in Favorites |
| Launch Flatpak action | `⌯✉︎ ๋࣭⭑` | QML label currently spells `FLATPACK`; don't silently rename the art |
| RUN user/cursor / terminal | `﹏݁˖✍︎๋࣭⭑₊` / `⌨` | RUN source selectors |
| Open Terminal Here | `༘⋆ ๋࣭⭑` | FILES action; `` may be a terminal fallback |
| Toolbox | `🛠` inside an outlined box | Outline and placement are part of composition |
| Bottles | Three separately sized `⚱` glyphs | Source sizes 11 / 18 / 11; not one spaced string |
| Enter Directory / Browse | `⌯🗁๋࣭⭑` | Both FILES selector and directory action |
| Open / Copy Path / Reveal | `↗` / `⋆˙🗐⋆˙` / `‧₊🔎︎˚⋆˙` | FILES actions |
| Freeze / Thaw | `₊°｡❆ ๋࣭⭑` / `⋆˙♨⋆˚.` | Action states, not indiscriminate replacements |
| MUTE / UNMUTE action faces | `* (ˊᗜˋو)و︎︎♬*` / `⊹ ࣪ (ᴗ˳ᴗ)ᶻ𝗓 ࣪ ` | App/Window/Tab actions, distinct from dock volume |
| Focus / Move Here | `(╭ರ_•́)` / `જ⁀➴` | Window actions |
| Float / Fullscreen | `⊹ ࣪ ˖🕊⋆₊⊹` / `🂡🂱🃑🂭🂽` | Window modes |
| Favorites star overlay | `✧` not favored / `✦` favored | Separately interactive overlay on rows and action buttons |

Windows → Tabs selector is exactly `♤ ⚄` (literal space separating symbols). Its ordinary application-tab icons and fallback icons (such as `▣`, ``, `󰛦`) are **not** replacements for that selector.

## 5 // REACTIVE CHARACTER AND VOLUME RECIPES

| Family | Default | Secondary stage | Activated / click stage |
| --- | --- | --- | --- |
| Favorites | `(˵✧ᴗ✧˵)` | Blink `(˵-ᴗ-˵)` | Hover/click `(˶ˆᗜˆ˵)` |
| Kitty | `≽(^•⩊•^)≼` | Blink `≽(^-⩊-^)≼` | Hover/click `≽(^≧⩊≦^)≼` |
| Kill / Hunter compact | `(-_•)デ╾━` | Thumbs up `ദ്ദി(-_•)デ╾━` | Fire `(=ᗜ=)デ╾━ ๋࣭⭑` |

**Hidden (separate contextual face):** Default `|ω-ς)`; blink/hover/selected ``|ω･`ς)``. Pressed styling exists, but a third distinct face glyph has **not** been verified.

Favorites, Kitty, and Hidden have appropriate blink/attention behavior. **Kill/Hunter does not have an automatic face-blink cycle.** Do not add one to achieve apparent uniformity.

The Kill family also includes main long-gun `(-_•)︻デ═一`, rifle component `▄︻デ══━一`, no-target face `(•_•)`, split Run face/gun/spray elements, and Hogs/Mice targets (normal versus hit), which remain contextual.

**Volume is not the same family as AppControl's MUTE/UNMUTE action faces.**

- Dock muted face `⊹˖(ᴗ˳ᴗ)ᶻ𝗓` and level bars `░░░░░░░` through `███████` are retained.
- Dock unavailable face uses **two separate text items**, left `ᓬ(｡•́︿•̀｡)` and right `ᕒ`. Source Row `spacing: 8` is layout/sizing, **not** an intended literal character space.
- The displayed percentage and right-hand muted decoration are separate elements. Respect their individual font/position/glow geometry.

## 6 // HUNTER / KILL MENU-OWNER STATE MACHINE

**Operator decision (2026-10-10):** Every clickable Hunter/Kill icon fires on click. When that icon **opens or holds a menu/window**, its visible sequence is:

1. **Idle (closed)** — the appropriate resting face and contextual gun.
2. **Hover/selected** — its thumbs-up/armed expression as appropriate.
3. **Opening click** — **one visible firing animation cycle** (for a compact control: `(=ᗜ=)デ╾━ ๋࣭⭑`).
4. **After firing while the associated menu/window remains open** — **thumbs-up persists**, even when the pointer leaves.
5. **After closing that associated surface** — return to the ordinary idle/hover state.

**Menu-open is not the same as hunting-in-progress.** A hunt can run while its status window is hidden. Do not latch the gun to continuous firing merely because a background operation is active; conversely do not return to neutral merely because the pointer left an open menu.

This applies to main AppControl KILL rail, Normal/Hunter mode selection and its Favorites copies, mini Kill category controls, Kill All/Hogs/Mice and their contextual menu-owning triggers, and the related App/Window/Tab/Run/Hidden/task actions **where the interaction has an associated open surface**. One-shot action controls still need their first click firing expression; don't invent a persistent menu state where none exists. Keep each gun/rifle/animal composition and the operator-approved expressive `"CLOSE" TAB` Kill gun **instead of replacing it with `×`**.

**Safety boundary:** Visual gun firing is not process termination authority. All destructive confirmations, protected-process checks, favorites protections, SIGTERM behavior and background hunting lifecycles must remain unchanged by presentation fixes.

**Source audit checkpoint:** Current inspected code did not fully implement the main KILL rail's expressive states; Normal/Hunter selector lacked a firing frame; copied Favorites Kill selectors/filter were static; Hogs/Mice actions and confirm controls had three source-state expressions but may only display firing during mouse-down. The existing Hogs/Mice launcher's `firing = pressed || operationFiring` can stay firing for a hidden background operation and can go neutral during an open confirmation. Runtime timing is **not verified**. The future special Hunter animation and loading screen are **planned, not specified or implemented by this contract**.

A non-clickable **running-hunt status title** remains a separate pending design question. The menu-owner rule alone does not authorize rewriting status-title artwork.

## 7 // ATTENTION, PUNCTUATION AND CROSS CONTROLS

- Intentional **warning / attention / exclamation-sign artwork** in AppControl should use the exact text-style `⚠︎`, including places where different exclamation glyphs currently appear in one menu.
- **Ordinary sentence-ending `!` is allowed**, including `Run Command, Run!` and `All Your Favorites!`. This later operator clarification **supersedes** an earlier overly broad "replace all visible !" transcription.
- Do not rewrite QML logical `!`, shell/Python syntax, data, logs or third-party strings in pursuit of a visual sign rule.
- `×` (U+00D7) is approved for **both Close/Dismiss and Remove-from-list**. Neither meaning forces generic `×` into the intentionally gun-themed AppControl Close Tab action.
- A shared operation name does not justify flattening its contextual visual identity. Examples: GitHub Library versus Files; Flatpak selector versus launch action; action face versus volume status face.

## 8 // COLOR AND INTERACTION ARE INDEPENDENT AXES

This shared operator-level rule governs relational color meaning; the [Post-Apollo visual-language recipes](https://github.com/kudokudo1/The-Post-Apollo-Project/blob/main/MODEL/components/visual-language-recipes.md) govern project-specific QML effects, numerical recipes and recorded exceptions. Specialized icon/glow identity can remain stable through interaction while a yellow selected fill or red destructive treatment communicates state. Do not convert every selected character to orange or homogenize deliberate magenta/green/cyan contrast.

Preserve front/back glow order, separate text shadows, font-size differences, transparent positioning and stage-specific color treatment. If the glyph appears wrong, test the rendering instead of assuming its Unicode or decoration was mistaken.

### 8.1 // RELATIONAL COLOR CLASSIFICATION

Color identifies a **relationship in context**, not a fixed noun, selector depth, or obligation that adjacent buttons differ. First classify the referent, scope (whole, subsystem, action, display), emphasized relationship, persistence through interaction, and established precedent. Related terms need not share colors; different controls expressing the same relationship may share them.

- **Relational equivalence:** siblings need not use unique colors. No one-color-per-button, one-color-per-section, or required alternation.
- **Container independence:** a heading's color is context, not automatic inheritance. In AppControl, destructive Killing Actions may be red while Limit is yellow, Freeze cyan, and Kill red; multiple actions elsewhere may legitimately share cyan or orange.
- **Layer independence:** icon/text foreground, fill, border, sampled content glow, chassis/perimeter glow, punctuation and keyboard/selection emphasis can carry distinct but compatible meanings. Changing one state does not mandate recoloring every layer.
- **Identity and state:** persistent specialized identity can survive selection or hover alongside a contrasting yellow selected fill or magenta glow. Existing documented open-state precedence remains valid; this does not repeal DockButton's open-magenta treatment or intentional layer order.

These are **relational defaults**, not exclusive assignments of nouns to hex values:

| Color family | Typical relational role; always qualify by context |
| --- | --- |
| White/off-white | broad undifferentiated whole, neutral/default information, universal glanceable utility, or whole-system entry |
| Cyan | ordinary observation/presence, signals, connection/data exchange, passive information and common baseline |
| Blue | related cyan-family distinction when scope, density, or composition calls for a secondary role |
| Orange/Yellow | agency family: active operation, energy/heat, user intervention; yellow may express limiting, secondary or adjacent agency |
| Omnitrix/sub-Omnitrix green | systems, audio/screens, automation, AI and confirmation through existing specific family recipes; do not flatten layered green glows |
| Magenta | focus, meaningful selection, expression, human/personal choice, or established specialized identity |
| Red | destructive/critical action, danger, actual error, extreme telemetry or explicit high-consequence identity |
| Dark/Black | related structural/chassis treatments, not competing foreground identities |

Precedent and real-world associations matter. Kill's destructive red is not freely assignable to unrelated nearby actions. Thermal heat may be orange while Kill remains red. Domain growth, renaming and icon changes do not automatically erase persistent identity.

**Cross-layer example:** audio subsystem controls may use Omnitrix-green identity and a distinct magenta interaction glow. Music may have its own cyan/magenta personal, authored, ongoing-signal identity, including when paused; it need not inherit the broader audio-system green. Exact media allocations remain under their specific contracts.

### 8.2 // NUMERICAL RANGE AND INTERPOLATION GRAMMAR

The default ordered relational range palette is:

**White → Yellow → (Green) → [Omnitrix] → [Cyan] → (Blue) → Orange → Magenta → Red**

Parentheses indicate optional related-family stops (Green and Blue); bracketed Omnitrix and Cyan identify their principal green/cyan family representatives, not universal mandatory stops. Family variants may be omitted or substituted according to the represented relationship.

**Orange may occupy either of two positions:** beside Yellow *or* after the cyan/blue family. This is relocation, **not duplication**: a single ramp must not include Orange in both places. Moving Orange earlier can avoid undesired greenish blended intermediate colors when interpolating from cyan toward orange; such blends are not forbidden if they work in context.

- Place **Cyan** at a sensible normal, likely, or expected operating region when the phenomenon has one; this is not necessarily the numeric midpoint.
- For ranges without a universal normal reference (temperature is an example), **White** can serve as the default reference, and ordering may adapt to the phenomenon.
- Smooth interpolation is normally preferred for continuous quantities where useful; stepped colors suit discrete categories or meaningful thresholds.
- RGB/interpolated colors outside the named palette are not automatically violations. Judge the rendered path, not only endpoints.
- Mute, unavailable, disconnected and actual fault states are **categorical conditions**, separate from numerical intensity, and may have independent foreground/glow recipes.
- Thresholds, punctuation whiteness, sampled glow and perimeter glow may differ intentionally; do not force them to agree.

**Reference implementations:** Post-Apollo's Volume module blends cyan→orange→magenta→red above initial white/cyan stages; Network currently uses stepped Wi-Fi signal tiers. Preserve the existing Wi-Fi thresholds, disconnected treatment and independent glows. A new red Wi-Fi error treatment remains **explicitly deferred**, not approved by this section.

### 8.3 // COLOR RELATIONSHIPS ACROSS A COMPOSITION

A module's color affects the *whole dock*, including plausible dynamic states, not just an idle screenshot. Stable cyan-family elements can balance variable telemetry. Weather's stable orange, Social's green-family position, Volume's changing range and Clock's cyan/orange choice contribute to the right-side composition. The relatively stable left side includes established Hospital magenta and Git yellow/orange relationships without requiring forced alternation.

Semantically plausible recoloring or relocation may still break layout, glow density or color rhythm. Check the whole local neighbor chain before changing one item; preserve justified exceptions and don't flatten independent layers.

## 9 // MAINTENANCE, IMPLEMENTATION AND VERIFICATION

- **Rule provenance:** operator icon review (23 Pass-1 and 28 Pass-2 approved entries), subsequent Windows → Tabs and Close decisions, Git/GitHub and SSH replacement selections, source inventory and consistency checks, and 2026-10-10 Hunter/exception clarifications. These are *review entries*, not unique glyph counts. The full working inventory remains a living Nurse 3a artifact.
- **Decision versus implementation:** approved mappings and animation rules are authoritative **targets**. Existing QML discrepancies are implementation backlog until corrected and runtime-tested; don't label this document a successful rollout.
- **Nurse 3a:** keep reviewing missing glyphs, exact code points, sizes, compositional geometry, state transitions and exceptions, and update the living record. Report to Head Nurse .C at meaningful boundaries; do not silently convert read-only audit into edits of another worker's files.
- **Before migration:** re-check current `main`, file ownership, source glyphs, font choice, button geometry, input and menu ownership. Change only assigned surfaces. Preserve keyboard navigation, destructive safeguards and preexisting component behavior.
- **Verify separately:** Unicode/source literal; constructed QML; hover/selected/press/click pulse; menu-open hold after firing; return on close; rendering at actual user font and scale; pointer-release timing; background hunt with hidden window; GitHub branch/PR versus merged `main`.
- **Operator final acceptance:** screenshots or live observation decide whether the visual grammar has truly been preserved. Exceptions and new icons are incremental amendments, not reasons to restart the entire inventory.

## SOURCE AND RELATED CONTRACTS

- [Post-Apollo Project](https://github.com/kudokudo1/The-Post-Apollo-Project): implementation/source truth (especially `widgets/AppControlW.qml`, `widgets/appcontrol/HunterControls.qml`, `widgets/appcontrol/DestructiveConfirmOverlay.qml`, `widgets/CpuPlusW.qml`, `modules/Mediaplayer.qml`, `modules/Volumebar.qml`, `modules/Network.qml`).
- [Visual-language recipes and green-family roles](https://github.com/kudokudo1/The-Post-Apollo-Project/blob/main/MODEL/components/visual-language-recipes.md): implementation-specific effect and component recipes; shared operator color semantics remain governed here.
- [OPERATE // Post-Apollo Working Guide](./POST-APOLLO-WORKING-GUIDE.md): ownership, authority, testing and human acceptance.
- [OPERATE // Hospital Report Protocol](./HOSPITAL-REPORT-PROTOCOL.md): report boundaries and external handoffs.

> **Preserve the family, the relationship and the operator's decision—not just the default glyph.**
