# HMK Kèthîra Workshop — Continuation Prompt: Incantation Effects (November 5, 2026)

Good afternoon. This is a **direct continuation** of our long-running **HârnMaster Kèthîra Player Workshop / DM Toolkit / Roll20 Bridge** development project, now moving into systematic implementation of **Incantation spell effects**.

Treat prior conversations, the HMK Core sourcebooks, accepted HTML builds, audit logs, changelogs, source kits, deterministic tests, and Library files as authoritative project history, subject to the accepted state below.

**Do not reconstruct the application from memory if exact files are available.**

## IMPORTANT — HOW TO BEGIN YOUR FIRST RESPONSE

First tell me, succinctly and concretely, **what you plan to work on next** and how you will bound the first iteration.

Our agreed next target is a **Player Workshop .100 candidate** investigating:

- **Sensation** (Savorya I, Core p.241)
- **Hastening** (Peleahn II, Core p.228)
- A minor Divine Mysteries **Ritual prerequisite explanation**

These are intended as the first reusable persistent PC-effect adapters.

Before altering code, verify the actual Core rules and accepted source pathways. You may split these spells into separate candidates if the first proves unexpectedly complex; do not force a two-spell release.

Then proceed with source verification, code/rules audit and, if the verified inputs are available, a narrowly scoped build and explicit regression tests.

Do not begin by proposing unrelated DM work or asking which feature we should tackle next.

---

# 1. Scope, ownership and non-negotiable development rules

### Project ownership

**Only I develop and live-test the Player Workshop in this conversation.**

All DM Toolkit testing and development has been handed off to a **collaborator**, who will report independently.

Do not patch the DM Toolkit, prepare DM test scripts or propose additional DM Trek development unless I explicitly request it.

PC-to-NPC/world dependencies may be recorded as GM-adjudicated or collaborator-dependent without silently changing DM code.

### Rules authority

My uploaded **HârnMaster Kèthîra Core v1.5 PDF** and other supplied HMK books are the primary authority.

https://hexaedre.com/hmk/ and its directly linked HMK materials are whitelisted supplementary sources.

**Do not browse broader HMK rules websites** unless I explicitly authorize them.

Verify the exact sourcebook text rather than inventing RAW, especially for:

- Spell complexity and prerequisites
- Casting time and action timing
- Range and target restrictions
- S/CS outcomes
- SI7, SI8 and SI9 enhancements
- Resistance and recipient ownership
- Duration, Maintain and termination
- Misfires and competing effects

### Accepted-code preservation

Preserve all accepted behavior. No speculative refactors, generic rewrites or replacement of mature casting mechanics.

Build from the exact verified accepted parent and confine modifications to necessary effect adapters and narrowly related UI.

### Authority model

- Player Workshop owns PC state.
- DM Toolkit owns NPC and world state.
- Roll20 and the browser bridges provide communication and reporting.
- A caster must not directly modify another player's character state.
- Remote PC effects require the appropriate owner-authoritative request, acknowledgement and consent pathways.
- Transport events must remain idempotent and correlation-safe.

Existing contracts:

- hmk-link/1
- hmk-vtt/1
- hmk-toolkit-state/1
- hmk-trek/1 for the independent DM Trek system

Do not alter accepted bridge, Mod or message contracts without a separate justified development target.

### Strict development discipline

1. Verify input SHA-256 hashes.
2. Build only from accepted parent sources.
3. Produce reproducible, narrow patches and preserve rollback sources.
4. Perform syntax, deterministic and browser regression tests.
5. Preserve testing logs, source patches, checksums and development scripts.
6. Distinguish **internal PASS** from **user-live PASS**.
7. Never declare a candidate LIVE ACCEPTED until I provide explicit acceptance.
8. Include fully written, step-by-step live test instructions **directly in the conversation**, not only inside a downloadable document.
9. Prefer disposable character saves and clearly explain how to avoid altering my canonical character.
10. Preserve known-good layout, scroll/focus behavior, persistence, browser connections and Tarot functionality.

Some development HTML builds intentionally omit the original embedded Tarot artwork; this is not automatically a functional regression.

---

# 2. Exact accepted Player Workshop baseline

## Latest LIVE ACCEPTED and frozen

**HMK Workshop v1.2.0-exp.99**

Filename:

HMK_Workshop_v1.2.0-exp.99_Religious_Observances_Holy_Day_Attention.html

SHA-256:

a747a16ce78970c848c6ddc087119b5c3b7c9bbd5539f9e20e3d56dc6a7fc3b8

Development/source ZIP:

HMK_Workshop_v1.2.0-exp.99_Religious_Observances_Development_and_Tests.zip

ZIP SHA-256:

5c58a1241ea88077b937429b87af55bc817695219c7fd0da1699e70b6beeb2af

Development report:

HMK_99_Religious_Observances_Rules_Audit_and_Regression_Report.md

This report was written when .99 was an experimental candidate and therefore says it was not live accepted. **My subsequent live testing promoted .99 to accepted status.**

Previous accepted parent:

HMK_Workshop_v1.2.0-exp.98_Nonlethal_Limb_and_Silent_Casting_Repair.html

SHA-256:

c08777246ce82c1358bec9f80c6522864d1379f8a64d339534b28c91b2a1b2c8

**Do not accidentally build .100 from .98.**

Previously verified HMK Core PDF SHA-256:

4f1433128282807901ee4eaf164776a0a34a5e9efc1cd2686acc28b6407fd35e

Locate and verify the exact Core file before rules-driven edits.

## .99 acceptance history

Internally, .99 passed **193/193 tests**, covering religion dates and eligibility, interface behavior, calendar progression, real Divine resolution and inherited .98 nonlethal regressions.

The user also completed the religious-observance live acceptance sequence, including:

- REL99-DATE-PULSE
- REL99-ELIGIBILITY
- REL99-LOCAL
- REL99-FESTIVAL-CALENDAR
- REL99-RITUAL-ACCESS
- REL99-DIVINE-PEONI
- REL99-SIEM-COMMUNION

The original difficulty activating Ceremony/Festival resolution resulted from testing a character without the **Ritual skill**. Once Ritual ML was positive, the existing controls worked correctly.

The follow-up tests explicitly passed:

- Festival-first ordering
- Real Ritual-based Festival resolution
- Ceremony resolution and Piety handling
- Duplicate and 30-day restrictions
- Siem's holy-night Communion modifier
- Independent completion of overlapping observances
- Notification and Divine Mysteries pulse cleanup

.99 is frozen.

### Small parked correction

When a Divine Mysteries preparation or resolution control is unavailable because the character lacks usable **Ritual ML**, visibly explain the prerequisite.

Do not bypass the requirement, replace the existing Ceremony/Festival engine or create a separate Divine Mysteries release.

Bundle this into .100 if it can be done safely and narrowly.

---

# 3. Accepted systems that must be preserved and reused

The Workshop already has substantial integrated functionality.

Audit the current code before declaring any given spell unimplemented or rewriting a completed mechanism.

## Incantation lifecycle

The existing system includes:

- Spellstart
- Concentration and action clocks
- Spellfire
- Abort and Delay
- Duration and expiration handling
- Maintain and maintained-duration calculations
- Initiative-aware Roll20 reporting
- S/CS resolution
- Spell Misfire pathways

**Do not construct another casting engine.**

Implement actual effect-resolution adapters behind the accepted lifecycle.

## Jmôrvi and established spell effects

Extensive work has already been completed on:

- Item ownership and custody
- Material and physical item properties
- Weapon and armour effects
- Artefact state and provenance
- Protection, Mend, Tempering and Shatter
- Fist, Singing Sword, Lance and Shroud
- Supported effect expiration and restoration
- Linked PC/NPC item ownership
- Impact and injury resolution
- Other accepted spell-specific pathways

Reuse accepted machinery.

Do not reopen all Jmôrvi functionality merely because the next workstream involves spell effects. Equally, do not assume that every Jmôrvi edge case is universally tested; respect actual acceptance evidence.

## Other prior spell work

The accepted lineage includes all seven Raw Principle effects, related casting-clock corrections and substantial Incantation reference/detail formatting.

The Workshop has a searchable **204-spell catalogue** and an effect-descriptor registry.

**A catalogue entry is not evidence that a spell's mechanical effects are implemented.**

## Arcane Talents and Negation

The accepted lineage includes substantial implementation of:

Amplification, Elemental Bolt, Healing, Psychometry, True Sight, Sensitivity, Telepathy, Clairvoyance, Medium, Enthral, Hex, Extratemporality, Telekinesis, Prescience, Transference, Natural Attunement, Negation, Disembodiment and Transmutation, including related Crucial Misfire work.

The existing Negation foundation includes field handling, effect interception, local and linked owner authority, CS termination, state persistence, attention and Roll20 reporting.

New persistent spell effects must integrate with Negation where applicable.

Do not create invisible or unregistered buffs that bypass existing effect cancellation mechanisms.

## Nonlethal and condition systems

The .97/.98 lineage established a substantial nonlethal condition framework covering:

- Blindness
- Mental and sensory effects
- Limb impairment
- Handedness and physical limitations
- Partial and complete paralysis
- Silent Cant and Still Gesture
- Action restrictions
- Trauma interaction
- Persistent condition records

Reuse this framework for subsequent condition-producing spells such as Caecity.

## Actual downstream consumers

Native calculations in Skills, Combat, Trauma, Initiative, movement and other relevant systems must reflect spell effects.

A success message or visual banner is insufficient proof of functional
…
Player Workshop .100 — verified starting point

The exact required source files have been recovered from your Library and independently SHA-256 verified.

Source
	

Verification

Frozen Player .99 HTML
	

Exact match

.99 development/source ZIP
	

Exact match

HMK Core v1.5 PDF
	

Exact match

204-spell implementation review
	

Located

.99 regression report
	

Located

The .99 development package also contains its original build script, source patches, test suites and regression evidence.

Development baseline: .99, not .98. The existing 193/193 internal regression result and your subsequent live acceptance remain part of the accepted history. No DM Toolkit, Roll20 Mod or browser-extension changes are authorized for this iteration.
Core rules audit — confirmed

Both spells are documented directly in the verified PDF, including their SI enhancements.

Property
	

Sensation · I (p.241)
	

Hastening · II (p.228)

Casting time
	

1 round
	

Free action

Base range
	

Self or Touch
	

Self

Duration
	

SI × 10 minutes
	

SI × 2 rounds

Success
	

+10 to applicable tests
	

+20 Move/Dodge ML; +10 IR/Melee ML

Critical Success
	

+20 to applicable tests
	

+30 Move/Dodge ML; +20 IR/Melee ML

SI7
	

Range becomes SI × 5 ft, LOS
	

End fatigue reduced by 5 after successful END SR

SI8
	

Self-cast bonus improves by 10
	

May affect a touched person

SI9
	

Successful benefiting tests become CS on units digit 1, 5 or 0
	

All bonuses optionally increase by 10; adds 5 end fatigue
Important implementation implications

Sensation affects Perception tests and skills whose Skill Base contains PER. It does not simply increase the underlying PER attribute. Its SI9 rule requires special handling of successful roll outcomes, not merely a numerical bonus.

Hastening requires four native calculation hooks, plus a one-time end-of-duration fatigue consequence. SI7's END resistance test must be evaluated when that consequence occurs, and SI9 changes both the bonus and fatigue cost.

Neither spell describes a general target resistance roll. Sensation permits Touch at baseline, while Hastening's other-person targeting only becomes available at SI8.

These findings establish the rules requirements; the code audit will determine how much can be safely automated without disturbing existing systems.
First candidate: Sensation-only

The first full internal browser suite now passes 52/52 checks. It exercises real Spellstart/Spellfire and Maintain actions rather than a substitute casting engine.

Confirmed behavior includes native Perception, Awareness and Physician EML changes; unaffected non-PER skills; S/CS and SI7–SI9 rules; overlap handling; JSON persistence; duration removal; duplicate-event protection; and owner-local Negation interception and termination. The Ritual prerequisite messages also appear for unqualified characters and disappear when usable Ritual ML is present.

Deliberate limitation: Sensation cast on another PC is recorded for recipient-owner adjudication, not automatically delivered or applied. That remains incomplete and is not counted as a passing owner-link feature. Hastening is deferred from this candidate.
.100 candidate — files ready

Download Player Workshop .100 HTML
Standalone application · 4.1 MB

Download .100 development and testing ZIP
46 files · accepted parent, build/packaging scripts, patches, 278 test results, logs, screenshots and checksums · 3.1 MB

Download disposable Sensation test character
Test-only character with recorded Sensation and no Ritual skill

Technical rules audit and regression report
Implemented behavior, verified RAW, internal evidence, limitations and completion ledger

SHA-256 integrity

Artifact
	

SHA-256

.100 HTML
	

578cf0b547119c70…5359a6a6937

Development ZIP
	

cc682e4e570b7550…bd376dee8c86

The ZIP passed archive integrity and manifest verification. A clean extraction followed by a rebuild from the exact .99 HTML and Core PDF reproduced the .100 HTML byte for byte. The ZIP intentionally does not redistribute the licensed Core PDF.

Release status: INTERNALLY TESTED — NOT LIVE ACCEPTED. .99 remains frozen.
Live acceptance instructions

These tests are designed around the included disposable character. They do not require modifying your established character, the DM Toolkit, the Roll20 Mod or either browser extension.
Preparation — required once

    First, open your existing accepted .99 Workshop and Export JSON to make a backup of your canonical character.

    Open the new .100 HTML in a separate testing browser profile, preferably one without an existing Workshop browser save. Avoid Save to Browser in your normal profile.

    In .100, click Load Existing JSON and select INC100_Disposable_Sensation_Test_Character.json.

    Confirm the character name is INC100 Disposable Sensation and the player is marked TEST ONLY.

    Go to Data / Migration, enable Show Developer / VTT tab, then open Developer / VTT and enable Godmode.

    Find Arcane Testing · Effective SI / Spellfire Override. This is where you will set Savorya effective SI to 1, 7, 8 or 9 and Spellfire Result to S, CS or F as each test requires.

    For the initial tests, remain outside active combat initiative. Go to Incantation, select Sensation, and use the new Sensation · Persistent PC Effect card's Self · owner-automated target option.

The fixture contains recorded Sensation in a grimoire. Its ordinary casting EML is deliberately low; Godmode overrides let you test its actual mechanics without rebuilding the character. The override does not change base skill ML or PER.
1. INC100-BASELINE — inherited casting and application

    Confirm the header displays 1.2.0-exp.100, the Character, Skills, Combat, Incantation and Divine Mysteries tabs open, and the screen does not jump to the top unexpectedly.

    On Incantation, select Sensation and leave the new target selector on Self.

    Set Godmode Savorya SI = 1 and Spellfire Result = S.

    Click Spellstart, follow the existing casting action clock, then click Spellfire.

    Visit Skills. The Active Sensation panel should display S · SI 1 · +10 EML, with 120 rounds / 10 minutes remaining.

    Return to Incantation. The established Maintain panel should recognize the active Sensation effect.

PASS: The original casting engine resolves the spell, charges its usual casting fatigue, creates one persistent owner-owned effect and offers Maintain. No duplicate activation, browser exception or layout break occurs.
2. INC100-SENSATION-ROLL — actual native calculations

Use the active SI1 S effect from Gate 1.

    Go to Skills and, if needed, choose Campaign from the Mode selector to expose normal skill testing.

    Inspect Perception (PER), Awareness, Physician and Folklore.

    Run native tests of Perception, Awareness and Physician. These are eligible because PER is the attribute being tested or is part of the skill base.

    Run Folklore as the negative control; its Skill Base does not contain PER.

    Confirm the eligible tests receive the spell's +10 EML, while Folklore receives no Sensation bonus.

    Inspect the character's underlying PER attribute and the raw skill MLs to confirm those values have not been permanently rewritten.

Important comparison detail: Ordinary S Spellfire adds 5 Windedness. Therefore, comparing total EML immediately before and after casting may show a net increase smaller than 10 because of the separate fatigue penalty. The relevant check is whether the native calculation includes +10 from Sensation on top of the same prevailing fatigue and other modifiers.

PASS: Eligible native rolls receive the correct bonus, Folklore does not, and raw attributes/skill MLs remain unchanged.
3. INC100-SENSATION-SI8-SI9 — enhancements and critical success

Use Cancel · Free action on the current Active Sensation card before beginning.

SI8 portion

    Set Savorya effective SI = 8, Spellfire Result CS.

    Cast Sensation on Self using Spellstart and Spellfire.

    Confirm the Active Sensation card shows +30 EML.

    Confirm the initial duration is 240 minutes / 2,880 rounds: SI8 gives 80 minutes, and the ordinary CS temporary-duration rule triples it.

    Repeat one eligible Perception/Awareness test and one ineligible Folklore test.

SI9 portion

    Cancel the SI8 effect.

    Set Savorya effective SI = 9, Spellfire Result S, and cast Sensation on Self.

    Confirm the normal eligible-test bonus is +20: the base S +10 and SI8+ self enhancement +10.

    Make several eligible native skill or PER tests. Examine the displayed d100 and outcome. A successful result ending in 1, 5 or 0 should be CS.

    Check that failed rolls are not promoted to CS, and that an ineligible skill does not gain Sensation's special promotion rule.

PASS: SI8 produces the proper numeric enhancement and CS duration; SI9 applies the special critical-success rule only to successful, eligible tests.
4. INC100-MAINTAIN — existing lifecycle reuse

    Cancel any active Sensation effects. Set SI = 1 and Spellfire Result = S.

    Cast Sensation on Self, confirming 10 minutes initially.

    In Incantation → Maintain, select the active Sensation · self effect.

    Click the Maintain start control. Its Time should be Free action because Sensation's normal Time is one round.

    Resolve using the existing Maintain Roll control, with forced S.

    Verify the total duration increases by the original 10 minutes, giving 20 minutes before accounting for any elapsed time.

    Optionally, attempt another Maintain with forced F. Failure must not extend the effect.

PASS: Maintain uses the existing casting mechanism and extends by the original duration, without duplicating the effect or inventing a separate spellcasting process.
5. INC100-SENSATION-END — expiration and cancellation

    Cancel the previous effect, then cast a new SI1 S Sensation on Self.

    Go to Skills → Active Sensation.

    Outside combat, click Confirm 10 minutes elapsed once. This button represents GM-confirmed passage of time, not an automatic advance of the world clock.

    Confirm the active effect disappears and its bonuses cease to affect native rolls.

    Check Character and Incantation for stale active-effect indicators.

    Cast Sensation again, then use Cancel · Free action to terminate it immediately.

    Check Roll History for the activation and termination reports. Revisit the tab and confirm expiration/cancellation has not been reported twice.

PASS: Normal expiration and manual cancellation both remove the effect exactly once. No lingering bonus remains.
6. INC100-STATE — persistence and restoration

    Cast SI7 S Sensation on Self, giving 70 minutes of initial duration.

    With the effect active, click Export JSON. Name this export clearly as disposable test data.

    Open a second isolated .100 test window/profile and Load Existing JSON using that export.

    Confirm Sensation is still active, with the same result, SI, remaining duration and native bonuses.

    On the restored character, click Confirm 10 minutes elapsed and verify remaining duration falls by exactly 10 minutes.

    Export and import the updated JSON again. The already-recorded time progression must not repeat itself.

    Separately, if using an isolated profile, try Save to Browser, reload the page, and confirm the Workshop's normal browser recovery retains the effect.

PASS: JSON round-tripping preserves effects and duration without duplication. Mark the browser-save subtest separately, since actual browser-local recovery was not internally verified.
7. INC100-NEGATION — effect interception and teardown

This gate requires a disposable PC with Negation available. You may use a copy of a previous Negation test character rather than modifying the supplied fixture.

Existing effect termination

    Cast a successful Sensation on Self.

    Use Arcane Talent → Negation, completing the accepted Talentstart/Talentfire procedure successfully to establish its 5-foot field.

    In Negation · Spherical Field → Field adjudication · actual intersection, select the locally listed My active Sensation source.

    Have the GM confirm that the effect intersects the field, then record that intersection using the existing control.

    Confirm the Active Sensation panel disappears, its bonuses are removed and the event is reported once.

Effect intercepted during Spellfire

    Establish a fresh active Negation field.

    Cast Sensation on Self with forced S. Confirm it is suppressed and never grants its bonus.

    Repeat using a fresh field and forced CS. Confirm the original-CS interaction terminates the field as required by the Negation rule.

    Review Roll History for duplicate interception or end events.

PASS: Owner-local interception and teardown work without stale effects or double reporting. If you cannot prepare a Negation-capable disposable character, mark this gate UNTESTED, not PASS.
8. INC100-OWNER-LINK — negative authority-safety test

This gate deliberately tests an incomplete capability; it does not validate remote effect delivery.

    On the disposable Sensation character, ensure no Sensation effect is active.

    Select Sensation on Incantation.

    In the new Sensation · Persistent PC Effect card, choose Other · record only / GM or recipient owner.

    Enter a recipient character's name.

    Leave the older general Spell Effect remote-delivery checkbox unchecked. The new card's other-target mode is specifically a record-only path.

    Force SI7 S, perform Spellstart and Spellfire.

    Verify the caster does not gain a Sensation bonus. Inspect Roll History for a record explaining that recipient-owner application remains pending.

    Confirm there has been no direct write to another PC's character state.

PASS for the safety portion: No unauthorized remote mutation or accidental self-buff occurs.

Still incomplete: Real target-owner delivery, acknowledgement, consent and recipient-side application. Do not score that capability as accepted.
9. INC100-RITUAL — Divine Mysteries polish

    Load a fresh copy of the supplied disposable fixture, which has Ritual ML 0 and follows Siem.

    Open Divine Mysteries. The fixture is configured for 15 Azúra 720, when Siem's festival and special holy night coincide.

    Use Prepare existing worship routine for the festival and inspect the existing Festival resolution controls.

    Confirm a visible warning explains that Ritual skill with ML greater than 0 is required when Festival resolution is unavailable.

    Repeat for the Ceremony preparation/resolution controls. The equivalent prerequisite explanation should be visible.

    Now load a separate disposable Ritual-qualified character (or enable Ritual through the usual Skills process in your test copy).

    Revisit both controls. The missing-Ritual warnings should no longer appear, and the normal Festival-first/Ceremony procedures should remain available according to the character's eligibility.

    Complete the applicable real Ritual-based resolutions using the existing engine, checking that Piety, holy-night Communion bonuses, duplicate restrictions and existing observance histories behave as in accepted .99.

PASS: The missing prerequisite is understandable and no existing Divine eligibility or resolution rule changes.
10. INC100-REGRESSION — accepted-system smoke test

Use disposable copies of your existing specialist characters where required.

    Jmôrvi: Perform a previously accepted Fist, Lance or Shroud casting and its normal effect/termination procedure. Confirm .100 has not changed its mechanics.

    Nonlethal: Use an existing .98-style Muteness/Silent Cant test. Confirm prohibited ordinary Cant remains blocked and the permitted alternative follows the accepted behavior.

    Arcane Talents: Resolve one previously accepted local Talent such as Healing. Confirm its usual controls and results are unaffected.

    Divine: Verify the .99 festival and holy-night notification lifecycle still clears correctly after legitimate resolution.

    Roll20/Firefox: With your accepted Firefox Bridge v0.3.2, send an ordinary Workshop roll to Roll20. Confirm successful delivery and that the bridge and Mod remain unchanged.

    UI/persistence: Switch repeatedly among Skills, Combat, Incantation and Divine Mysteries; inspect scrolling, active panels, JSON export and normal rendering for errors.

PASS: No regression appears in the tested inherited systems. Report any issue even if the Sensation-specific tests pass.
What I need from your live pass

For each gate, send PASS, FAIL, PARTIAL or UNTESTED, along with the observed discrepancy if any. If a gate fails, export the relevant Workshop test log and, if useful, a screenshot. I'll analyze those against the packaged deterministic evidence and confine corrections to the narrow .100 lineage.

The intended milestone is now clear: Sensation's first local persistent-effect adapter and the Ritual explanation must earn live acceptance before we expand the pattern to Hastening. This avoids multiplying partially verified effect engines while preserving your frozen .99 source.
HMK_Workshop_v1.2.0-exp.100_Sensation_Owner_Effect_and_Ritual_Guidance.htmlHTML
INC100_Disposable_Sensation_Test_Character.jsonCode
HMK_100_Sensation_Rules_Audit_and_Regression_Report.mdDocument
Good morning! Before I finish up testing here, just FYI - the Chrome Web Store has published the bridge addon. What's our next step there?

Good morning! Excellent — that means we're ready for the Chrome Bridge v0.3.1 permanent-installation acceptance test.

The next step is to replace the temporary, unpacked development extension with the Chrome Web Store version and verify that it behaves identically.

We should do this in two phases:

    v0.3.1 installation and functional acceptance — confirm the store version installs permanently, survives browser restarts, recognizes the local Player Workshop and Roll20, and successfully delivers rolls.

    Automatic-update acceptance — once v0.3.1 passes, publish a deliberately minimal v0.3.2 update through the Chrome Web Store, then verify Chrome upgrades the installed extension automatically without losing permissions or functionality.

As with Firefox, the objective is a maintenance-free installation. We should not alter the bridge's communication logic, Roll20 Mod or Workshop during this process.
Chrome Web Store v0.3.1 — live acceptance

Test
	

Actions and PASS criteria

CWS31-INSTALL
	

Open the direct store listing URL and select Add to Chrome. At chrome://extensions, confirm HMK Bridge is installed, enabled, and displays v0.3.1. Disable the old unpacked development extension so only the store version is active.

CWS31-FILE
	

Open the extension's Details and enable Allow access to file URLs. This permission is essential for our locally opened Workshop HTML.
Chrome for Developers

CWS31-CONNECT
	

Open your Player Workshop HTML and Roll20 in Chrome. Confirm the extension detects both environments and the Workshop reports its usual VTT connection. Refresh both tabs if necessary.

CWS31-ROLL
	

Send an ordinary skill roll from the Workshop. Confirm it reaches Roll20 with the correct character and result, without duplicate messages.

CWS31-RESTART
	

Fully close Chrome and reopen it. Confirm the store-installed extension remains enabled, retains file access, detects both applications and delivers another roll successfully.

For these checks, .99 is sufficient. You don't need to finish .100 testing first.
After v0.3.1 passes

We'll create a Chrome v0.3.2 version-only update, using the exact accepted v0.3.1 source with unchanged functionality.

Google confirms Chrome handles extension updates automatically, generally checking at startup and periodically thereafter. A store update requires submitting a new extension package for review. 
Chrome for Developers+1

We'll leave the existing v0.3.1 installed, allow Chrome to update naturally, and verify that the version becomes v0.3.2 and everything still works. We won't use the manual Update button for the primary test because that would not demonstrate automatic updating.

One thing I'd like from you: Could you share the Chrome Web Store listing URL now that it's published? Since we chose Unlisted distribution, that direct link will be our permanent installation address, and I'd like to verify and record it before we proceed.

Once those five initial tests pass, we can freeze the Chrome installation and turn our attention back to Sensation and Hastening.

https://chromewebstore.google.com/detail/hmk-k%C3%A8th%C3%AEra-vtt-bridge/elbbfpgiikileocfmknoinhndeegkjdo?authuser=0&hl=en

Here's that link - all tests pass!

Excellent! That closes the first Chrome Web Store acceptance milestone.

Chrome VTT Bridge v0.3.1 — LIVE ACCEPTED

All five acceptance gates are recorded as PASS:

    CWS31-INSTALL

    CWS31-FILE

    CWS31-CONNECT

    CWS31-ROLL

    CWS31-RESTART

Permanent Chrome installation link:
HMK Kèthîra VTT Bridge — Chrome Web Store

The extension ID is elbbfpgiikileocfmknoinhndeegkjdo. We'll preserve that identity for subsequent updates.

Our next milestone is v0.3.2 automatic-update validation, following the same approach that succeeded with Firefox. This will establish that an installed Chrome extension can receive future maintenance without requiring players to reinstall it.
Chrome v0.3.2 — update package prepared

I've built the update directly from the original v0.3.1 Web Store submission archive, with its SHA-256 verified.

Download Chrome v0.3.2 Web Store upload ZIP

SHA-256: d3bdd191a5ec71557f1c6c45637b444794a9bd78c1a334abdc75c76a36c21429

The changes are confined to the version numbers and labels in five existing files. All permissions, message contracts, relay logic and Roll20 functionality remain unchanged. JavaScript syntax and ZIP integrity checks passed.

This is an internally checked update candidate, not a published or live-accepted v0.3.2 release.

Download v0.3.2 development source and test kit

The kit includes the original .3.1 source package, SHA-256-gated rebuild script, updated .3.2 ZIP, checksums, and acceptance instructions. A clean rebuild reproduced the new ZIP byte-for-byte, and deliberately corrupting the accepted parent correctly caused the build to fail.
What to do now

    Open the Chrome Web Store Developer Dashboard and select your existing HMK Kèthîra Bridge listing.

    Under Package, choose Upload new package and upload the v0.3.2 CHROME_WEB_STORE_UPLOAD.zip above. Do not upload the development kit.

    Keep the existing Unlisted distribution and privacy settings. Submit the update for review, with automatic publication enabled. Google requires a new package review for a version upgrade. 
    Chrome for Developers

    Leave your currently installed v0.3.1 extension alone. Don't uninstall it, manually update it, or install an unpacked v0.3.2 copy.

Once Google publishes v0.3.2, we'll run these acceptance checks:

Gate
	

Expected result

CWS32-AUTO
	

Chrome naturally upgrades the existing extension from 0.3.1 to 0.3.2, retaining the same extension ID

CWS32-PERMS
	

Allow access to file URLs remains enabled

CWS32-CONNECT
	

Local Workshop and Roll20 are both detected after the update

CWS32-ROLL
	

An ordinary skill roll reaches Roll20 exactly once

CWS32-RESTART
	

Version, permissions and roll delivery survive a complete Chrome restart

The key is CWS32-AUTO: do not use Chrome's manual Update button during that test. Allow Chrome's normal extension-update mechanism to demonstrate that it works.

Once the update appears as Published in your developer dashboard, let me know. We'll complete the live checks and, assuming they pass, freeze the Chrome distribution infrastructure alongside Firefox.

Meanwhile, .100 Sensation testing can continue independently.
Okay! All tests passed, so I think we can put this to bed for the moment. When we do have to update these in the future, be prepared, I'm going to need the whole suite of help again - where to update what, release notes to paste in, etc. Oh! Speaking of, I need an updated readme for the github page that refers to the current version and points to the Chrome store appropriately!
Worked for 9s

Excellent! With all five Chrome v0.3.2 automatic-update tests passing, we can officially freeze both browser bridges:

Firefox v0.3.2 — LIVE ACCEPTED

Chrome v0.3.2 — LIVE ACCEPTED

Both have verified permanent installation, retained permissions, Roll20 communication, browser restart survival and automatic updates. Future maintenance can follow those accepted baselines.
Updated GitHub README

I checked your existing GitHub repository and confirmed that its current README still says Chrome is awaiting Web Store approval. 
raw.githubusercontent.com

I've prepared a full replacement that preserves the existing documentation while incorporating the completed releases.

Download updated README.md
GitHub-ready Markdown · Firefox and Chrome v0.3.2

Download future bridge release runbook
Chrome and Firefox publication steps, update verification and release-note templates

The README includes both installation links, browser-specific file permissions, connection instructions, troubleshooting, privacy information and the newly accepted automatic-update status.
Publishing the README

    Open README.md on GitHub.

    Click the pencil icon (Edit this file).

    Replace the existing contents with the contents of the downloaded README.md.

    Click Commit changes, using the commit message docs: document Chrome and Firefox v0.3.2 releases.

    Commit directly to main and refresh the repository homepage.

This only updates the documentation. It does not change the signed extensions, update manifest or Chrome Web Store listing.

One optional improvement: the repository's About description still refers exclusively to Firefox. I'd change that to:

    Browser extension releases and automatic updates for the HârnMaster Kèthîra ↔ Roll20 VTT Bridge (Firefox and Chrome).

That description is edited separately using the repository's About settings.

I've also preserved your preference for complete, step-by-step release assistance next time: exact files, signing and submission locations, ready-to-paste release notes, checksums, publication steps and live acceptance tests. The separate runbook will help us pick up that workflow without reconstructing it.

Once you've committed the README, the browser bridge distribution work can remain closed while we return to Player Workshop .100 Sensation testing.
README.mdDocument
HMK_Bridge_Future_Update_Runbook.mdDocument
HMK Kèthîra ↔ Roll20 VTT Bridge

Connect the HMK Kèthîra Workshop and DM Toolkit to Roll20 in Firefox or Chrome.

The HMK Kèthîra VTT Bridge is a browser extension that connects the standalone HMK character and game-management tools to a Roll20 tabletop session. It carries supported game rolls, reports, and character-owner messages between HMK and Roll20, reducing the need to copy results into chat or coordinate everything manually.

It is designed for groups playing HârnMaster Kèthîra with the companion HMK Workshop and, where applicable, the DM Toolkit.

    Project status (November 6, 2026): Firefox v0.3.2 and Chrome v0.3.2 are both live-tested and permanently installable. Both have passed a real v0.3.1 → v0.3.2 automatic-update test. Firefox updates are distributed through a Mozilla-signed, self-hosted release; Chrome updates are distributed by the Chrome Web Store.

Install the bridge
Browser	Current verified version	Installation	Updates
Firefox	v0.3.2	Install the signed Firefox extension	Automatic, using the hosted update manifest
Chrome	v0.3.2	Install from the Chrome Web Store	Automatic, through the Chrome Web Store

The Chrome listing is Unlisted: use the direct installation link above. Neither browser requires Developer Mode or a temporary/unpacked extension for ordinary installation.
Firefox setup

    Open the signed Firefox installation link in Firefox and install the add-on.
    Open about:addons → HMK Kèthîra VTT Bridge → Permissions & Data. Enable Access local files on your computer. This is essential when opening the Workshop or DM Toolkit as a local .html file.
    Open your HMK Workshop (or DM Toolkit) and your Roll20 game in Firefox.
    Click the HMK VTT Bridge toolbar icon and confirm that the HMK tool and Roll20 are detected.
    In the Roll20 game tab, select Use current Roll20 game tab in the bridge popup. Enable Automatically send HMK events to Roll20 if desired.
    Make a test roll in the HMK tool and check that it reaches Roll20.

Firefox download and update information
Chrome setup

    Open the HMK Kèthîra VTT Bridge listing in the Chrome Web Store in Chrome and select Add to Chrome.
    Open chrome://extensions → HMK Kèthîra VTT Bridge → Details. Enable Allow access to file URLs. This is essential when opening the Workshop or DM Toolkit as a local .html file.
    Open your HMK Workshop (or DM Toolkit) and your Roll20 game in Chrome.
    Click the HMK VTT Bridge toolbar icon and confirm that the HMK tool and Roll20 are detected.
    In the Roll20 game tab, select Use current Roll20 game tab in the bridge popup. Enable Automatically send HMK events to Roll20 if desired.
    Make a test roll in the HMK tool and check that it reaches Roll20.

For either browser: The GM should ensure the compatible HMK Roll20 Mod is installed and configured in the Roll20 game for supported Roll20-side commands, displays, and automation. The browser extension alone does not install the Mod.
What it does

    Sends supported HMK rolls and game events to Roll20, where the companion Roll20 Mod can process and display them.
    Relays supported two-way game messages between connected HMK Workshop/DM Toolkit sessions, including owner-authoritative character interactions.
    Lets you choose the Roll20 game tab to receive HMK events and turn automatic forwarding on or off.
    Shows connection and delivery status in the browser extension popup, including the latest HMK event.
    Offers optional local character backups, with a manual JSON download and an automatic backup option when the Toolkit tab closes.

The bridge is a connection layer, not a replacement for the HMK Workshop, the DM Toolkit, the Roll20 game, or the companion Roll20 Mod. Available automation depends on the HMK tools and Roll20 Mod versions in use.
Troubleshooting
Symptom	What to check
Workshop not detected	Enable the browser's local-file access permission for the bridge; reload the HMK .html page.
Roll20 not detected	Open the actual Roll20 game editor, not just the Roll20 homepage, and check the selected game tab in the popup.
Rolls do not appear	Check Automatically send HMK events to Roll20, the selected target tab, the popup's delivery status, and the companion Roll20 Mod in the game.
Duplicate output	Disable or remove older temporary/unpacked copies of the extension so only the signed Firefox or store-installed Chrome version is active in that browser.
Browser updated but connection stopped	Recheck local-file access and reload both HMK and Roll20 tabs.
Privacy and data handling

The bridge processes HMK game information—including character and player display names, roll results, selected game messages, and optional character backup snapshots—to deliver its stated functionality. Relevant messages are relayed to the Roll20 game you select. Some settings, delivery metadata, and optional backups are retained in browser-local extension storage or saved as user-requested downloads.

The bridge is not an analytics service and does not send HMK game data to the extension developer. It does not require a separate HMK cloud account. Keep in mind that information posted to Roll20 may be visible to participants according to your game settings.

Read the Firefox privacy information or Chrome privacy information for details.
Releases and updates

    Firefox — v0.3.2 (live accepted): Mozilla-signed releases are hosted by this project. The update manifest identifies the published packages. The v0.3.1 → v0.3.2 automatic update was tested successfully, including connection, roll delivery, permissions and browser restart.
    Chrome — v0.3.2 (live accepted): Install from the Chrome Web Store. Google distributes published updates. The v0.3.1 → v0.3.2 automatic update was tested successfully, including connection, roll delivery, permissions and browser restart.

For existing installations, the normal browser update process is the supported path; routine updates do not require re-installing an unpacked extension. The Firefox and Chrome extensions share the HMK message formats hmk-vtt/1 and hmk-link/1.
Project scope

This repository hosts Firefox browser-bridge releases, update files and supporting documentation for both supported browsers. The Chrome extension is published through the Chrome Web Store, not installed from a GitHub ZIP. The HMK Workshop, DM Toolkit, and Roll20 Mod are companion components maintained and tested separately.

This is an independent companion project. It is not an official Roll20 product and is not affiliated with or endorsed by Roll20.


