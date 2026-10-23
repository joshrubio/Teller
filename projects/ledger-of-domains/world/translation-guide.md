---
id: translation-guide
type: world
project: ledger-of-domains
module: world
tags: [translation, english, glossary, terminology, prose-conventions]
load-with: [world/odem, world/amat, system/domains, voice/style, themes/writing-rules]
updated: 2026-10-16
---

# Translation Guide — Spanish → English

**Purpose:** single operational reference for translating the manuscript into English. Covers three layers: (1) prose mechanics, (2) voice and style, (3) term glossary. Check all three before translating a chapter.

**Master rule:** one term, one translation, always. If a new term comes up while translating, it gets decided here first — never left loose in the translated chapter.

**Paths:** Spanish original in `D:\Writting\Teller\manuscript\spanish\`. Translation in `D:\Writting\Teller\manuscript\english\`. One file per chapter, same number: `Capitulo 5.md` → `Chapter 5.md`.

---

# PART 1 — Prose mechanics

## 1.1 Dialogue — em-dash to quotation marks

Spanish uses the em-dash (—). English uses double quotation marks. **Convention chosen: US style** (commas and periods inside the quotes, closed em-dash with no spaces). The Spanish manuscript is inconsistent about spacing around the dialogue dash (`—texto` and `— texto` coexist) — that inconsistency disappears on its own once converted to quotes; no need to replicate it.

| Case | Spanish | English |
|---|---|---|
| Dialogue with attribution | `—Casi me matas del susto —dijo Oliver.` | `"You almost killed me," Oliver said.` |
| Dialogue without attribution | `—Tomaré el tren de las once.` | `"I'll take the eleven o'clock train."` |
| Attribution + action | `—Y tú a mí. —Park dejó caer los hombros—. ¿Dónde vives?` | `"You too." Park let his shoulders drop. "Where do you live?"` |
| Mid-line attribution | `—texto —dijo X— continuación.` | `"Text," X said, "continuation."` |
| Interrupted dialogue | `—Kessler, no tengo idea de...` | `"Kessler, I have no idea what—"` |
| Question/exclamation | `—¿Dónde carajo estás?` | `"Where the hell are you?"` |

**Hard rules:**
- Opening marks `¿` `¡` disappear — English doesn't use them.
- Attribution verb lowercase after comma: `," he said`, never `," He said`.
- Prefer `said` / `asked` / `answered`. The original already avoids fancy dialogue tags (`voice/style.md`) — keep that discipline.
- Action between dialogue lines = period and new sentence, not comma: `"Text." He turned. "More text."`
- If the original ends a dialogue line with a cutoff dash (`—texto —`), English closes with an em-dash inside the quotes: `"text—"`.

## 1.2 Em-dash in narration

Narration uses the spaced em-dash (`texto — texto`) heavily — 22 instances in Chapter 1 alone.

**Convention (revised 2026-08-06): spaced em-dash, ` — `, space before and after.** Originally this guide called for the closed US-style dash (`text—text`), but that caused real reading errors: when the word right before the dash and the word right after it can plausibly modify each other (e.g. `warning—before, Park calculated...`), a closed dash lets the eye read across it as one unbroken clause. The space breaks that false read. Confirmed on Ch0 (`"...shouted a warning — before, Park calculated afterward, there was..."`).

- ES: `Un adulto que ha memorizado el vocabulario completo —Odem, Domain, Potestad— y que sigue esperando.`
- EN: `An adult who has memorized the complete vocabulary — Odem, Domain, Authority — and is still waiting.`

**Watch out:** the original leans on the dash a bit hard. If three or more em-dashes land in the same English paragraph, consider converting one into a comma, parenthesis, or period. English prose tolerates less dash density than Spanish before it starts to sound mannered. **This is not license to rewrite** — only to let the punctuation breathe where English calls for it.

**Note:** this only applies to em-dashes in narration. Dialogue punctuation (§1.1) is unaffected — quoted cutoff dashes stay closed inside the quotes (`"text—"`), no space, since that's a different mark (a voice cut off mid-word) not a narrative aside.

## 1.3 Verb tense — the pluperfect problem

**Discovered in the test translation (Ch1). The most important point in this guide after dialogue.**

Spanish sustains the pluperfect (*había dicho*, *había mirado*, *había tardado*) across entire flashback scenes without it feeling heavy. English **doesn't**: keeping *had said / had looked / had taken* going for twenty paragraphs straight turns the prose leaden and amateurish.

**Rule:** establish the flashback with past perfect in the first 2-3 sentences, then **drop to simple past** for the body of the scene. Return to past perfect only to close, to return the reader to the narrative present.

Real example (Ch1, motorcycle flashback):

> ES: `—Casi me matas del susto —le **había dicho** Oliver... Park **había ladeado** apenas la cabeza... El trayecto **había empezado** sin palabras... Park **había tardado** unos segundos.`
>
> EN: `"You almost killed me," Oliver **had told** him...` *(establishes)* → `Park **tilted** his head, barely... The ride **started** without words... Park **took** a few seconds.` *(body in simple past)* → `He **had disappeared** at the next intersection...` *(closes)*

Apply the same logic to any extended memory scene. The Spanish original isn't "wrong" — the two languages just have different tolerances for that tense.

## 1.4 Hard interruption vs. trailing-off voice

The original uses two distinct marks, and the difference has to be preserved:

| ES | Meaning | EN |
|---|---|---|
| `—Kessler, no tengo idea de...` | The voice trails off on its own | `"Kessler, I have no idea what—"` if cut off by someone/something else; `"...I have no idea."` if it trails off |
| `— ¿Qué—?` | Hard interruption, cut off by an event | `"What—"` |
| `—No te voy a dejar—` | Cut off by another speaker | `"I'm not going to leave you—"` |

Practical rule: **em-dash = someone/something cuts it off**. **Ellipsis = the voice trails off on its own.**

## 1.5 Numbers and measurements

- **Numbers under a hundred: spelled out** (`twenty-six missed calls`, `forty-two square meters`), same as the original. Standard literary convention in English.
- **Extended 2026-08-06 (Ch107-111, Final Exam arc):** the Board uses recurring tallies well above a hundred (213, 187, 156...) as a running narrative motif. Same convention applies with **no ceiling — spell everything out** (`two hundred thirteen`, `a hundred fifty-six`), never switch to numerals just because the number is large. This will keep coming up through the rest of the arc.
- **Times: spelled out** (`eleven forty-five`), as in the original.
- **Measurements: keep the metric system.** The original is metric even in scenes set in the US (Grayhaven). Converting to feet/miles would break consistency with the European scenes, which are the majority. *Decided 2026-08-06 — revisit only if a US-market editor requires it.*

## 1.6 File format

| Element | Spanish | English |
|---|---|---|
| Chapter header | `# Capítulo 5 — Umbral` | `# Chapter 5 — Threshold` |
| Prologue | `# Prólogo — Vigilancia` | `# Prologue — Surveillance` |
| Scene break | `---` | `---` (unchanged) |
| Emphasis | `*texto*` | `*text*` (unchanged) |
| Spacing | One blank line between paragraphs | Same (unchanged) |

## 1.7 Terms already in English inside the original

**Critical rule: do not re-translate or "improve" these.** They're the English the author already chose; they stay identical in the English version.

- ~~`BLANK NODE RESOLVED` — the on-screen system line~~ **Retired 2026-09-29 by the "El Cobro" retcon** — see §3.0. Replaced by `REGISTRY SETTLED`, handwritten in a notebook, not a screen. Only correct now inside `_backup-pre-retcon-el-cobro/`.
- ~~`blank node` — lowercase, Oliver's general perceptual vocabulary for an Odem-signature anomaly~~ **Also retired 2026-09-29, author's call (reversing the earlier "not retired" note below).** Replaced by **`gap`** (ES: `hueco`) everywhere — `world/odem.md`, `characters/oliver.md`, `system/registro.md`, and Ch60/Ch71 (the only two chapters that used it) all fixed in place. Don't reintroduce "blank node"/"nodo vacío" in any new prose or node file.
- ~~`el Ledger` → `the Ledger` — the device~~ **Retired 2026-09-29** — the device no longer exists. See §3.0 for the new object (`la libreta` → "the notebook," lowercase).
- `Domain` — when the original already uses the English word.
- `EM Boxing` — Riku/Iker's style.
- Any Anglo proper noun (Grayhaven, Breakwater, Shelter 9, Hartford, Elm Creek, Halloway, Georgetown).
- **Whole passages the Spanish original already wrote in English** — e.g. Kaspar's letter at the end of Ch75 (the Anke reveal; was Ch71 before the retcon's +4 shift). Preserve verbatim, word for word, no re-translation. This is the same rule as the single-term cases above, just applied to a block of prose instead of a word — if you hit a passage like this, don't treat "it's a full paragraph, not a term" as a reason to touch it.

## 1.8 Language references — "Spanish" becomes "English" (added 2026-10-16)

**Rule.** In the Spanish manuscript the characters' working language is Spanish; in the English version it is English. Any in-text reference to a character speaking, hearing, repeating, thinking or writing *in Spanish* (`en español`, `en castellano`, `un castellano antiguo y torpe`) is replaced by the English equivalent. Other languages (Korean, Japanese, Portuguese, Hungarian, te reo…) stay as they are.

**Why it comes up (Ch146).** Riku says something in Japanese and then repeats it to himself in Spanish: `Lo dijo en japonés y se lo repitió a sí mismo en español`. In the English version he repeats it in English.

| ES | EN |
|---|---|
| `Lo dijo en japonés y se lo repitió a sí mismo en español.` (Ch146) | `He said it in Japanese and repeated it to himself in English.` |
| `una frase en castellano, seca, sin entonación` (Ch144, El Familiar) | `a sentence in English, dry, flat` |
| `en un castellano antiguo y torpe, la lengua de quien la ha aprendido por casualidad` (Ch144, Rūaumoko) | `in an archaic, clumsy English, the speech of someone who has picked it up by accident` |

Add any new instance to this section. Search every chapter for `español` and `castellano` before closing it (§4.2, item 9).

---

# PART 2 — Voice and style

## 2.1 General register

`voice/style.md` sets the Spanish register as "contemporary neutral — not markedly Latin American, not markedly Peninsular." English equivalent: **contemporary neutral, no markedly British or markedly American idiom in the lexicon**, but with **US punctuation** (see 1.1). Avoid lexical britishisms (*whilst*, *amongst*, *lorry*) and strong Americanisms (*gotten* is fine, *y'all* is not).

Rules from `voice/style.md` that carry over as-is:
- Short sentences under tension; long paragraphs in observation.
- Tone: contemplative-unsettling in setup → cinematic-kinetic in action.
- Never soften the cost of power.
- The cost is **specific and physical** — never "he felt tired." The text names the exact point where the body pays.
- Don't underline the weight of irreversible decisions with extra internal narration. The reader already sees it.
- Oblique affect — don't name what characters feel; show what they do.

## 2.2 Patterns to eliminate (inherited from `voice/style.md`)

These were already cut from the Spanish during editorial revision. **Do not let them back in through the English side door:**

| Prohibited pattern | Alternative |
|---|---|
| `X paused` / `There was a pause` as an attribution crutch | Concrete physical action, ellipsis, or direct connection |
| `with the attention of someone who...` | Direct verb or concrete description |
| Stacked Oliver analogies | **One per scene**, max |
| `Oliver processed that` as a transition | Vary it or cut it |
| Performative cleverness | The narrator doesn't try to be funny or impressive — restraint is the text's defense |

## 2.3 Character voices

| Character | Voice mark in English |
|---|---|
| **Park** | Dry, economical. Warnings without explaining the reason. Dark humor only to close out high tension. Doesn't fill silences. Short sentences, no unnecessary subordination. |
| **Oliver** | Analytical before emotional. Technical vocabulary (nodes, logs, contrast, signature). One analogy per scene, max. |
| **Voss** | Precise, no unnecessary warmth. Never raises his voice. Closes conversations with no sign-off formula. Numbers only when the figure matters narratively. |
| **Pier** | Teaching mode: proposition → implication → close, no filler. "The body" as a frequent subject. Calls Oliver by name before information that matters. |
| **Asha** | Closes arguments without inviting a reply. Process language (variables, inputs, outputs). Adds no emotional context to technical observations. |
| **Riku** | `O sea` as a lead-in to elaborating something she's unsure about saying → **`I mean`**. Corrects terminology for accuracy, not pedantry. |
| **Anke** | Dry, oblique. Tests rather than answers. Half-finished fragments, never a full explanation. |

**Do not confuse with Anka (Training Arc, §3.1b below) — near-identical spelling, different character.**

## 2.4 The "ledger" echo — a deliberate gain in English

**Partially retired 2026-09-29 by the "El Cobro" retcon.** The table below describes old, now-retired canon (Kessler, the device "el Ledger" — see §3.0). Rows 1 and 3 no longer apply to any live chapter. Row 4 ("el libro de día / el libro de noche," Oliver's double-life metaphor) may or may not survive in the new canon's own version of that duality (Yamal's bookkeeping by day, the secret debt payments underneath) — not verified, flag if it comes up. Row 2 (the Hartford substation's own "libro mayor," unrelated to Kessler/Yamal) is untouched by the retcon and still applies as originally written. The underlying decision — lowercase `ledger` for ordinary accounting language — still holds and is restated for the new canon in §3.0 (`los libros` → "the books"/"the accounts", `la libreta` → "the notebook," never capitalized "the Ledger").

**Discovered in the test translation (Ch1).** Spanish lexically distinguishes what English merges:

| ES | EN | Referent |
|---|---|---|
| el Ledger | the Ledger | The device stolen from Kessler |
| libro mayor | ledger | The substation's accounting record |
| las hojas / los libros de Kessler | Kessler's books / sheets | The loan shark's accounting |
| el libro de día / el libro de noche | the day ledger / the night ledger | Oliver's two lives |

In Spanish, *Ledger* (proper noun) and *libro mayor* (accounting term) are different words. In English they collapse into the same one: **ledger**. That makes the book's title — *Ledger of Domains* — resonate harder in the English version than in the original.

**Decision: lean into it, don't avoid it.** Translate *libro mayor* as `ledger` (lowercase) and the device as `the Ledger` (capitalized). The typographic distinction is enough for the reader; the echo is a gain, not a confusion. Don't substitute synonyms (*account book*, *register*) to "fix" the repetition.

## 2.5 Canonical lines — fixed translation

These recur throughout the book. **Fixed translation, identical every time they appear.**

| Spanish | Fixed English | Origin |
|---|---|---|
| Lo que lleva Odem existe; lo que lo suelta vuelve al polvo. | **What carries Odem exists; what releases it returns to dust.** | `world/odem.md` |
| Nombrar = activar. | **To name is to activate.** | World rule |
| Todo se arregla con código. | **Everything can be fixed with code.** | Oliver's defining line |
| El Odem no empieza en la piel — empieza más adentro. | **Odem doesn't start at the skin—it starts further in.** | Pier, Ch62 (was Ch58 pre-retcon +4 shift) |
| Lo que ocurrió en esos veinticuatro minutos en Grayhaven no es algo que yo pueda devolverte. | **What happened in those twenty-four minutes in Grayhaven isn't something I can give back to you.** | Park, `Capitulo 58 - Libro 2.md` (was "Ch54" pre-retcon; text confirmed 2026-09-29 to include "en Grayhaven," not in the guide's older transcription — corrected here) |
| No fue una falla de seguridad. Fue una falla de velocidad. | **It wasn't a security failure. It was a speed failure.** | Voss, Ch75 (was Ch71 pre-retcon +4 shift) |

**Retired 2026-09-29 (confirmed via full-corpus grep — none of these three appear anywhere in the live manuscript anymore, only inside `spanish/_backup-pre-retcon-el-cobro/`):**
- `El fallo no aparece. El fallo se comporta.` (was "Ch1, Oliver's notes") — lived in the old, now-retired Cap1 (Kessler canon).
- `No borra por odio. Borra por equilibrio.` (was "Ch3-4") — same, old Cap4 only. **Note:** `bestiary/grh-094.md` § Key phrases still lists this line as canonical to case GRH-094 — that bestiary entry is now stale too and should be reconciled or retired the next time that file is touched; out of scope for this pass.
- `Como un archivo borrado sin dejar rastro.` (was "Ch4") — same file, same fate.

**Flagged, not fixed 2026-09-29 — a pre-existing drift, unrelated to the retcon:** the "copied the threat/curiosity" canonical line no longer appears verbatim anywhere in the manuscript. `Capitulo 28.md` (old Ch24, Voss's scene) currently reads "Los tres casos copiaron lo que los amenazaba... El señor Webb copió lo que encontró interesante" — a paraphrase, not the fixed line this guide documents. This predates and is unrelated to the "El Cobro" retcon (the only retcon-driven edit made to that chapter was the nearby "leyó una pantalla"→"abrió una libreta ajena" fix and the BLANK NODE RESOLVED restructure, logged in `plot/retcon-cleanup-log.md`). Worth the author's own look — either restore the canonical phrasing in the Spanish source or update this table to match the paraphrase as the new canonical line. Left untouched here since it's a content judgment call, not a renumbering fix.

## 2.6 Anti-calque — rewrite at the sentence level, don't translate clause by clause

**Detected 2026-08-06, reviewing the translated Ch0.** The first-pass translations sounded "translated" — Spanish syntax dragged into English nearly intact. A human translator doesn't convert clause by clause; **they reread the whole Spanish sentence, understand what it's doing, and rewrite it as if English were the original language.** This is a sentence-level rewrite rule, not a paragraph-level one — content, event order, and total chapter length don't change.

**Calque symptoms to hunt down and fix:**

| Calque (symptom) | Detected example | Fix |
|---|---|---|
| Subject-verb inversion like "It was, Park thought..." | `It was, Park thought, the kind of exercise...` | Normal English order: `Park thought it was the kind of exercise...` |
| Very long sentences with stacked subordinate clauses (one whole-paragraph sentence) | The German-scholar paragraph, a single 150+ word sentence | Split into 2-4 English sentences. Spanish tolerates cascading subordination; literary English doesn't — it loses tension. |
| `in order to X` when the bare infinitive is enough | `in order to line up, side by side` | `to line up, side by side` |
| Comma-spliced fragment with no connector (calque of Spanish apposition) | `...gray brightness, no sharp shadows, which suited Park` | Connect with `with`: `...gray brightness, with no sharp shadows—the kind that suited Park` or split into a new sentence |
| Adverb calqued in Spanish position (`desconfiar exactamente de` → `distrust exactly`) | `trained... to distrust exactly the patterns` | Reorder to English habit: `trained to distrust precisely the kind of pattern that...` |
| Repeated pivot word that doesn't tire in Spanish but does in English (`nadie...nadie`) | `nobody watches closely the man doing the work nobody wants to look at` | Break the symmetry: `no one looks twice at the man stuck doing the job everyone else avoids` |

**Operational rule:** after translating a paragraph, reread it (mentally, out loud) without looking at the Spanish. If a sentence only makes sense "because that's how it was in Spanish," rewrite it from scratch in English — same information, native sentence structure.

## 2.7 Target register — Sanderson flavor

**Decided 2026-08-06, after comparing author samples on a Ch0 fragment.** The English should lean toward Brandon Sanderson's register: clean, propulsive, aware of the mechanism it's describing.

Traits to imitate:
- **Concrete, active verbs** over abstract or passive constructions. "The stapler fell," not "The stapler was falling toward him."
- **Rhythm varied with intent**: a short, direct sentence after a longer one, for emphasis — especially closing out an observation or revealing an implication.
- **Clarity above all**, even in introspective passages. Sanderson doesn't trade comprehension for ornament; a dense idea gets explained with precision, not "literary" vagueness.
- **Short declarative sentences for closers** on a paragraph or scene: the last sentence of a tense paragraph is usually the shortest.
- **Visible mechanism**: when the text describes an ability, reflex, or process (Odem, a Domain, Oliver's perception), treat it with the same near-technical precision Sanderson uses to describe a magic system — the reader should be able to follow the logic, not just feel the awe.
- Avoid the Latinate/ornamented register (long sentences with connectors like "however," "nevertheless," dense subordination). Prefer short connectors and juxtaposition.

This doesn't replace the per-character voice rules (§2.3) or the contemporary-neutral register (§2.1) — it's the prose texture wrapping around them. Apply it mainly to narration; dialogue already follows the established character voices.

---

# PART 3 — Glossary

## 3.0 "El Cobro" retcon (2026-09-28) — supersedes old Ch0-7 opening arc

The opening arc was fully rewritten in Spanish (`plot/retcon-el-cobro.md`, `plot/retcon-cleanup-log.md`). Old `Capitulo 0.md`–`Capitulo 7.md` (loanshark "Kessler," Grayhaven electrical-infrastructure internship, the device "the Ledger," system line "BLANK NODE RESOLVED") are retired — backed up in `spanish/_backup-pre-retcon-el-cobro/`, replaced by 11 new chapters (`Capitulo 1.md`–`Capitulo 11.md`), with everything from old Cap8 on renumbered +4. **Same restructuring applies to `english/`:** old `Chapter 0.md`–`Chapter 7.md` back up to `english/_backup-pre-retcon-el-cobro/`, replaced by fresh translations of the new `Capitulo 1.md`–`Capitulo 11.md` as `Chapter 1.md`–`Chapter 11.md`, and old `Chapter 8.md` onward renumbers +4 to match the Spanish side file-for-file.

**Retired — do not use in any newly translated or fixed chapter:**
- `BLANK NODE RESOLVED` (uppercase, the exact old system-line) — retired. Still correct, unchanged, inside the backed-up pre-retcon files only.
- `the Ledger` (capitalized, the electronic device) — the device no longer exists. Don't reuse this exact capitalized phrase for the new object (see below) — it was fixed to a different referent and reusing it would misdescribe the new canon, not create the intended echo.
- `blank node` / `nodo vacío` (lowercase, Oliver's general perceptual vocabulary for an Odem-signature anomaly) — **retired 2026-09-29, author's call.** Was flagged as a false positive earlier the same day (it's independent of the old device and correctly survived the retcon on its own), but the author decided to rename it anyway. Replaced by **`gap`** (ES: `hueco`) — already fixed in `world/odem.md`, `characters/oliver.md`, `system/registro.md`, and the only two chapters that used it, Ch60 and Ch71. Don't reintroduce either the English or Spanish old term anywhere.

**New terms:**

| Spanish | English | Note |
|---|---|---|
| Farid Yamal | **Farid Yamal** | Unchanged, proper noun. Loanshark, replaces Kessler. |
| Reynard Kaneshiro | **Reynard Kaneshiro** | Unchanged. Con man from `_ideas/ledger-of-domains/con-man.md`; sold Yamal the lie that crystallized into the Authority. Not named in the arc's own prose (lives in the bible only, same treatment as Daniel Ashworth in Ch118) — translate faithfully if a future chapter ever does name him. |
| Silas / Dennis / Walter Doyle / Rosa Anselmi / Marisol Cotto / Fenwick / Delvecchio | Unchanged | Already English-compatible names. |
| Tobías Wren | **Tobias Wren** | Drop the accent — English orthography, same person. |
| Empeños Yamal / la casa de empeños / el negocio de Yamal | **Yamal's pawnshop** / **Yamal's** | Lowercase common noun + possessive proper name. No literal signage text is ever quoted in the Spanish source (unlike `GARY'S REPAIR`, which the original explicitly renders in English capitals) — so there's no fixed all-caps business name to preserve, just the plain descriptive phrase. |
| Dunmore (calle) | **Dunmore** | Unchanged, already-English street name (Breakwater neighborhood). |
| la libreta (the black leather notebook — the Authority's physical anchor) | **the notebook** | **Not** "the Ledger" — that capitalized term is retired (see above); reusing it for a different object would confuse readers/editors tracking the term across drafts. Keep this one lowercase, uncapitalized, a plain object — the "ledger" echo from §2.4 still applies separately to Farid's ordinary account books. |
| los libros (de Yamal) / las cuentas | **the books** / **the accounts** | Farid's ordinary bookkeeping — distinct from "the notebook" above. Follow §2.4: "libro mayor" as an accounting term still renders as lowercase **ledger** where that specific word fits naturally; "the books"/"the accounts" otherwise. |
| REGISTRO SALDADO (escrito a mano en la libreta) | **REGISTRY SETTLED** | Fixed translation, uppercase/italic, same treatment §1.7 gave `BLANK NODE RESOLVED`. Only Oliver ever sees it written, alone — if a later chapter has someone else "read" it directly on-page, that's a continuity bug in the Spanish source, not a translation call; flag it, don't silently fix it in translation. |
| El Cobrador / la Potestad del Cobro (AMAT operational name, case GRH-094) | **The Collector** | Doesn't appear in the arc's own prose (confirmed by full-text search) — logged here only so a future chapter that does name it renders it consistently. |
| GRH-094 / GRH094-S | Unchanged | Case codes, already alphanumeric. |
| Desvinculación | **Unbinding** | Matches the existing entry at §3.1 below — just confirming it holds for this arc's usage too. |

## 3.1 Core terms

| Spanish | English | Note |
|---|---|---|
| **Odem** | **Odem** | Untranslated, in any language. Root from archaic German (Luther, Genesis 2:7). A proper noun within the fiction, not a common word. |
| **Potestad / Potestades** | **Authority / Authorities** | Cataloged anomalous entity. |
| **Principado / Principados** | **Ruler / Rulers** | Larger-scale, regional/historical Authority. |
| **Dominio** (human power) | **Domain** | Already bilingual by design. |
| **Dominio** (an entity's space) | **Domain** | Same term, different referent — deliberate ambiguity from the original. Don't invent two different words: it would lose the echo. |
| Desvinculación | **Unbinding** | The act of separating an Authority from its anchor. |
| Ancla (of an Authority) | **Anchor** | Don't confuse with Sabine's Domain (also Anchor) — context separates them. |
| Despertado | **Awakened** | A person with an Odem reserve and perception. |
| Reserva basal elevada | **Elevated baseline reserve** | AMAT classification (Johanna). |
| Firma | **Signature** | A person's/entity's Odem signature. |
| Contornos | **Contours** | Oliver's perception. |

**Ephesians 6:12 (decided 2026-08-06):** the English quotes the **NIV** — *"against the rulers, against the authorities, against the powers of this dark world"* — because its vocabulary (rulers/authorities) matches the Potestad→Authority / Principado→Ruler mapping. `world/odem.md` already updated.

## 3.1b Training Arc names — added while translating Ch77-81

- **Anka** — new character, blind instructor at El Reducto, introduced Ch79. Turns toward where Odem activity *happened*, not toward voices; teaches the four universal techniques by name. **Not the same person as Anke** (§2.3) — near-identical spelling is coincidental (or deliberate on the author's part), keep them distinct in translation regardless.
- **Reber** — gray-uniformed orientation instructor, introduced unnamed Ch77, named Ch78-79. Proper noun, no translation.
- **Iker Zabala** — full name given Ch80 (Board reveal). **Confirmed the same "Iker" already in the glossary** (§3.3, "Iker / Riku — EM Boxing") — verified against Ch102-104, where this Iker uses Static (Riku's Domain) and the same closed EM Boxing stance Riku learned from him. Not a coincidental namesake; it's a deliberate payoff.
- **Noa Shapira** — full name given Ch80 (Board reveal), Johanna's group. Recurs in Ch102 (Riku's rivalry — lost clean to Noa, unlike the older unresolved history with Iker).
- **Combat / Knowledge / Field Evaluation** (Combate / Conocimiento / Evaluación de campo) — the three tracked categories feeding the Board (§3.2). Capitalized as category names.
- **la consigna** (Ch85, Swiss train-station left-luggage office) → **"the luggage lockers"** (not "left luggage," which reads British — stays consistent with §2.1's neutral register).
- Historical terms (Ch84, Johanna's backstory — standard English names for real groups, not invented): hermanos moravos → **Moravian Brethren**; Valdenses → **Waldensians**; Sajonia → **Saxony**.
- **Lukas** and **Rasmus** — Dax's group / Yegor's storeroom clique, introduced Ch91. Recur through Ch111-114 (confirmed by grep) — established recurring characters, not one-offs.
- **Active Reception** (Ch110, Riku) — named counter-technique: catching an incoming strike and reflecting the charge back through the same contact point. Capitalized like Mantle/Void/Pressure/Focus.
- **Echo** (Ch110, one-off candidate ability, ground-vibration attack) — capitalized as a named technique in the source; likely a one-off, not a recurring Domain, but logged in case it recurs.
- **Instinct** — EM Boxing mode name (Iker/Riku/Dax's style, §1.7). First appears Ch82, recurs Ch104 — both correctly rendered "Instinct," no fix needed, confirming consistency.
- **vereda** (Ch99, Ch106 — retcon 2026-09-22: setting moved from Colombia to the Sorte hillside, Yaracuy, Venezuela, where "vereda"/rural hamlet terms are used the same way) → rendered contextually as **"the village"** both times. Flag if a more literal "hamlet"/"district" rendering is ever preferred instead.
- **Camilo** — Kaspar's scout/tracker in the Sorte/Venezuela thread (Ch106), reads terrain rather than Domain-signatures. New recurring name.
- **Milán/Milan ambiguity (unavoidable):** Spanish distinguishes the city "Milán" (accented) from the candidate character "Milan" (unaccented). English collapses both to "Milan" — no fix available, context always disambiguates. Noting so it's not mistaken for a translation error on review.
- **Fondo Meridiano → "Meridian Fund"** (Ch96) — Luxembourg-registered nonprofit shell tied to Kaspar's recruitment network. Likely a recurring named organization.
- **Anke/Anka mix-up — known risk, keep checking.** The pre-v4 English files for Ch87-90 had systematically written "Anke" (the earlier, different character) where the Spanish said "Anka" (the Training Arc blind instructor) — caught and fixed during the Ch87-91 revision pass, except one instance in Ch87 line 73 that the revision agent missed and had to be caught separately (`grep -n "Anke" *.md` and cross-check against the Spanish before trusting any pre-v4 file that mentions either name). Ch101 (Training Arc close, still pending its own revision pass) is a likely place for the same error — check it specifically when that batch runs.

## 3.2 AMAT — institution

| Spanish | English |
|---|---|
| AMAT | **AMAT** (already-English acronym: Agency for the Monitoring of Anomalous Threats) |
| All Myths Are True | **All Myths Are True** |
| AMAT-EU / -NA / -KR / -PT / -HU / -Caribe | Unchanged |
| AMAT-Suiza | **AMAT-Switzerland** |
| Ginebra | **Geneva** |
| Rango 4 / 3 / 2 / 1 / S | **Rank 4 / 3 / 2 / 1 / S** |
| Agente de Campo | **Field Agent** |
| Agente Senior | **Senior Agent** |
| Especialista Operativo | **Operations Specialist** |
| Agente de Élite | **Elite Agent** |
| Agente Primordial | **Primordial Agent** |
| Nivel 4 / 3 / 2 / 1 (entities) | **Level 4 / 3 / 2 / 1** |
| Protocolo de Evaluación Compartida | **Shared Evaluation Protocol** |
| Puerta Franca | **Free Gate** |
| Tablero (general) | **The Board** |
| Sala de clasificación | **Classification Room** |
| Wardogs | **Wardogs** (already English) |

## 3.3 Domains

| Character | Spanish | English |
|---|---|---|
| Oliver | Registro | **Registry** |
| Park | Strength | **Strength** (already English) |
| Voss | Arquitectura/Espacio | **Architecture/Space** |
| Pier | Peso | **Weight** |
| Asha | Tensión | **Tension** |
| Riku | Estática | **Static** |
| Sisi | Mente | **Mind** |
| Dara | Doble | **Double** |
| Nadia | Impulso | **Impulse** |
| Sabine | Ancla | **Anchor** |
| Petra | Canje | **Swap** |
| Tomás | Tránsito | **Transit** |
| Yusuf | Densidad | **Density** |
| Lev | Calor | **Heat** |
| Kaspar (copied) | Sustento | **Sustenance** |
| Yegor | Arsenal | **Arsenal** |
| Milan Kovač | Hilo | **Thread** |
| Padre Conti | Omnipresencia | **Omnipresence** |
| Dax | Vampirismo | **Vampirism** |
| Iker / Riku | EM Boxing | **EM Boxing** (already English) |
| Pier | Lastre | **Ballast** |
| Dax | Caza | **The Hunt** |
| Elena Krauss | Rastro | **Trail** |

## 3.4 The four universal techniques

| Spanish | English |
|---|---|
| Manto | **Mantle** |
| Vacío | **Void** |
| Presión | **Pressure** |
| Foco | **Focus** |

## 3.4a The fifth technique and its variants (decided 2026-10-20)

| Spanish | English |
|---|---|
| Presión Inversa | **Reverse Pressure** |
| Presión Inversa de Odem | **Reverse Odem Pressure** (ROP) |
| Presión Inversa ajena | **Reverse Pressure (Other)** |
| Odem inverso | **Reverse Odem** |
| el reverso (jerga) | **the reverse** (slang) |
| Cierre / Recomposición / Restitución | **Closure / Recomposition / Restitution** |
| Deformación / Proliferación / Residuo | **Deformation / Proliferation / Residue** |

## 3.4a2 SRD-1 and Arc 3 Domains (decided 2026-10-20)

| Spanish | English |
|---|---|
| SRD-1 (Special Response Detachment 1) | **SRD-1** ("Uno" / "One") |
| Coro | **Chorus** |
| Detonación | **Detonation** |
| Resonancia | **Resonance** |
| Brote | **Sprout** |
| Pulso | **Pulse** |
| Temperatura | **Temperature** |
| Quietud | **Stillness** |

## 3.4c Wardog nicknames for the Isla del Coco fauna (Cap155-156; decided 2026-10-20)

Larkin and Salcedo (AMAT-NA, English-speaking) coin these on the spot; in the Spanish text they read as Spanish words because the whole text is a rendering of their English.

| Spanish | English | Note |
|---|---|---|
| Tractores | **Tractors** | Larkin, farm-raised near Dayton, Ohio, names them after the tractors he grew up around ("My old man had one just as stubborn"). Renamed from *Carros* on 2026-10-20. |
| Faroles | **Lanterns** | Glow-green translucent discs. |
| Pasto | **Turf** | Drier, more soldierly than *grass*. |
| Segadores | **Reapers** | Scythe-edged forelimbs. |

## 3.4b Park's Strength sub-techniques

**Decided 2026-08-06.** Park's Domain (Strength) runs on two named sub-techniques, both capitalized as proper nouns whenever they refer to the technique itself (not when the underlying word is used generically/descriptively in prose — see note below).

| Spanish | English | Note |
|---|---|---|
| Masa | **Mass** | Concentrating Odem-as-mass into a small point of contact. |
| Inercia | **Momentum** | **Not "Inertia."** In-context (Ch51: `inercia acumulada`, `cargó con Inercia`, `la inercia del propio giro amplificando`) the technique is force that gets *built up through absorbed impacts and released/transferred* — that's momentum (p=mv, accumulates and discharges), not inertia (resistance to a change in state). "Charged with Inertia" or "accumulated inertia" read wrong in English; "charged with Momentum" / "built momentum" read right and land better in the Sanderson register (§2.7) besides being the physically correct term. |

**Capitalization rule:** capitalize only when Spanish capitalizes it as the named technique (`Masa`, `Inercia` — proper noun, same pattern as `Manto`/`Vacío`/`Presión`/`Foco`). When the Spanish text uses the lowercase common noun (`inercia`, `masa`) as ordinary descriptive language — not naming the technique — translate with the ordinary lowercase English word and use whichever of *inertia* / *momentum* fits the physics of that specific sentence; don't force "Momentum" onto every lowercase instance. Check the Spanish source capitalization, not the English draft, when in doubt.

**Chapters confirmed using `Inercia` as the named technique in the Spanish source (relevant when translating or auditing):** 19, 28, 38, 40, 41, 51, 63, 82, 91, 92, 94, 95, 97, 98, 102, 104, 108, 109, 110, 112. (92 and 94 independently confirmed correct — rendered as Momentum — while translating the Training Arc.) Ch102 and Ch104 (translated before this decision) had already independently landed on "Momentum" — no fix needed there. Ch19, 28, 38, 51 had used "Inertia" and were corrected to "Momentum" on 2026-08-06.

## 3.4c Named objects/events (Budapest thread)

**Decided 2026-08-06, confirmed while translating Ch41-42.**

| Spanish | English | Note |
|---|---|---|
| el Grillete | **the Shackle** | The iron bound to Zoltán's/the Báthory line's wrist, anchoring the Lidérc. Capitalized, proper-noun treatment like `the Ledger`. |
| la Saturación (de Hartford) | **the Saturation** | The Hartford event referenced retrospectively from later chapters (Budapest, Seoul). Capitalized. |
| el Vínculo | **the Bond** | Ch69 — the mechanic that lets Kaspar's colony silently reconstitute over weeks with no signature the Registry can catch. Capitalized, likely recurs given it's tied to a recurring character ability. |
| la Irrupción | **the Incursion** | The event that closes the Valais arc (Ch69-71) — Sisi/Lev/Sabine's disappearance. Capitalized, named event, recurs by reference through Training Arc. |

**Oliver's father — name confirmed 2026-08-06:** **Gary** (Webb). Appears unexplained in Ch69's Spanish (Oliver's interior monologue: `"Irse implicaba muchas cosas, Sisi, Gary, él mismo"`) — confirmed by the author to be the father, not a draft leftover. No translation needed (proper noun), just noting it here so future chapters don't re-flag it as an unexplained name.

## 3.5 Places

| Spanish | English |
|---|---|
| Grayhaven / Breakwater / Hartford | Unchanged (already English) |
| Centro Valais | **Valais Center** |
| San Gotardo | **St. Gotthard** |
| El Reducto | **The Redoubt** | The book's training facility (Training Arc setting). **Not the same as** `Réduit` below — keep them distinct. |
| Réduit (historical, Ch72) | **Réduit** — leave untranslated | Real-world term: the actual WWII-era Swiss National Redoubt bunker network, cited by Pier as historical background. French term, not the fictional facility above. Don't translate to "Redoubt" and don't confuse with El Reducto — they're related by inspiration, not identical. |
| El Quai | **The Quay** |
| Centro Lemán | **Lake Léman Center** |
| Milán | **Milan** |
| Ginebra | **Geneva** |
| Val Bedretto / Val Tremola | Unchanged (real Swiss place names) |
| Sorte / Yaracuy / Caracas | Unchanged |
| Alfama / Mouraria | Unchanged |

## 3.6 Arcs

| Spanish | English |
|---|---|
| El Cobro | **The Toll** |
| El Aprendiz y el Agente | **The Apprentice and the Agent** |
| Valais | **Valais** |
| Entrenamiento | **Training Arc** |
| Examen Final | **Final Exam** |
| La Oferta (antes "Cierre de líneas") | **The Offer** (antes "Loose Ends") |
| El Origen de Kaspar | **Kaspar's Origin** |
| Evento Cataclísmico | **Cataclysm Event** |
| Secuelas | **Aftermath** |
| Hesperia | **Hesperia** |

---

# PART 4 — Quality control

## 4.1 Compression ratio — quick check

Spanish→English usually compresses by 10-15%. **In this book it shouldn't.** The original prose is dense and economical; if a translated chapter comes out well below the original, it's a sign something got trimmed.

**Target band: 95-102% of the Spanish word count.**

| Chapter | ES | EN | Ratio |
|---|---|---|---|
| Prologue / 0 | 2171 | 2062 | 95% |
| 1 | 3583 | 3606 | 101% |
| 2 | 3013 | 2974 | 99% |
| **Test total** | **8767** | **8642** | **98.6%** |

- **Below 92%:** review — subordinate clauses or observations were probably lost.
- **Above 108%:** review — explanatory padding not in the original was probably added.

## 4.2 Per-chapter checklist

Before calling a chapter translated:

1. All dialogue in quotes, attributions lowercase, punctuation inside the quotes.
2. Spaced em-dashes in narration (`text — text`), space before and after (§1.2). No paragraph with more than 2-3. Dialogue cutoff dashes inside quotes stay closed (`"text—"`).
3. Flashbacks: past perfect only to open and close, simple past in the body (§1.3).
4. Already-English terms intact: `Domain`, `EM Boxing` (§1.7). `BLANK NODE RESOLVED`, `the Ledger`, and `blank node` are retired — use `REGISTRY SETTLED`, "the notebook," and `gap` instead (§3.0).
5. Canonical lines identical to the §2.5 table.
6. Glossary applied: Potestad→Authority, Principado→Ruler, Odem untranslated.
7. Compression ratio within band (§4.1).
8. No prohibited pattern reintroduced (§2.2) — especially `X paused`.
9. Language references checked (§1.8): `español` / `castellano` → `English`.

---

## Status and log

**2026-08-06 — guide v1:** glossary closed.
**2026-08-06 — guide v2:** added Parts 1 and 2 (mechanics and voice) after finding v1 only worked as a glossary.
**2026-08-06 — test translation (Ch 0, 1, 2)** and guide v3 based on what was learned:
- Added §1.3 (pluperfect) — the most important finding; Spanish sustains *había+participle* through long flashbacks, English doesn't.
- Added §1.4 (hard interruption vs. trailing-off voice), §1.5 (numbers and measurements — stays metric), §2.4 (the *ledger* echo, a deliberate gain).
- Added Part 4 (quality control) with the ratio band and checklist.
**2026-08-06 — guide v4:** after reviewing the retranslated Ch0 sample against author-style comparisons:
- Added §2.6 (anti-calque) — the first-pass translations were mirroring Spanish clause structure too closely; this section catalogs the symptoms and fixes.
- Added §2.7 (target register: Sanderson flavor) — clean, propulsive, mechanism-aware prose, chosen by the user after comparing samples across five authors on a Ch0 fragment.
- Translated the entire guide to English per the project's documentation-language rule (Spanish prose examples kept as-is — they're source corpus, not documentation).

**2026-08-06 — guide v5, arc-by-arc workflow adopted:** translating in arc order now (see `plot/structure.md` for arc boundaries), mixing a revision pass (chapters already translated pre-v4) with fresh translation (chapters not yet touched) within each arc, one arc at a time, across multiple sessions.

- **Arc "El Cobro" (Ch0-6): COMPLETE.** All revised to v4 standard (spaced em-dash, anti-calque, Sanderson register).
- **Arc "El Aprendiz y el Agente" (Ch7-53): COMPLETE.** All 47 chapters done — mix of revision (7, 17-20, 31-35, 45-48) and fresh translation (the rest). Includes the BSA line's five internal legs (Hartford 8-13, Seoul/Jeollanam-do 16-22, Lisboa 25-31, Budapest 35-42, Venezuela 46-52) plus the interleaved Valais-line chapters.
- Decided during this arc: §3.4b (Park's Strength sub-techniques, Mass/Momentum — **not** "Inertia", see below), §3.4c (Grillete→Shackle, Saturación→Saturation).
- **Momentum vs. Inertia correction (2026-08-06):** four instances of the Park Strength sub-technique had been translated as "Inertia" (capitalized, proper-noun usage) before the Mass/Momentum decision was made — Ch19, Ch28, Ch38, Ch51 (×2). All corrected to "Momentum" in place. Ch102 and Ch104 (translated earlier, before this arc) had already independently landed on "Momentum" — no fix needed there. See §3.4b for the full list of chapters (up to Ch112) confirmed to use this technique in the Spanish source — relevant for future arcs.
- Minor source-typo fixes made silently during translation (spelling normalized to the established form, not a meaning change): "Vanconcelos" → Vasconcelos (Ch25 Spanish typo), "gwishin" → gwisin (Ch16 Spanish typo, one-off vs. the term used everywhere else from Ch18 on).
- Flagged, not fixed (translated faithfully — these are Spanish-source issues, not translation errors): Ch6 and Ch28 each contain a near-duplicated beat back-to-back (looks like a leftover draft artifact); Ch51 has an unclosed em-dash at a line ending (likely a stray typo). Worth the author's own look at the Spanish files.

- **Arc "Valais" (Ch54-71): COMPLETE.** All 18 chapters fresh-translated (54-62, then 63-71, two sequential batches). Ratios 92.6-98%, all in band.
- Decided during this arc: el Vínculo → **the Bond** (Ch69, Kaspar's colony-reconstitution mechanic — added to §3.4c). Confirmed Gary = Oliver's father's name (not a draft leftover). Extended §1.7 with the "whole passage already in English" case (Kaspar's letter, end of Ch71 — preserved verbatim). Fixed 5 Spanish-source typos in Ch69 directly (Rápido, una mancha, en cientos, aliviado, ¡Oliver!) at the author's request.
- **Note on Ch59-62:** these already had old pre-v4 English files on disk when the Valais batch started (leftover from an earlier, since-superseded translation pass — not tracked in this log at the time). They were overwritten with fresh v5-standard translations per the active task instructions; content/scene coverage was spot-checked as matching, nothing appears lost. Flagging here so the log stays the source of truth going forward — **always check the `english/` folder's actual current state before assuming a chapter is untouched, don't rely solely on this log.**
- Flagged, not fixed (Spanish-source issues, translated faithfully): Ch56 has a near-duplicated sentence about the Center's stonework across two consecutive paragraphs (same pattern as Ch6/Ch28); Ch55 files case folder GRH-094 "between GRH-094 and CVA-LOG" (self-referential, possibly a typo for a third folder name); Ch61 uses lowercase "la masa"/"el vector de aceleración" for what may be the same Mass/Momentum sub-techniques under different phrasing, or a genuinely separate framing — kept lowercase per literal-capitalization rule, worth the author's eye.

- **Arc "Training Arc" (Ch72-101): COMPLETE.** All 30 chapters done across six sequential single-agent batches (72-76, 77-81, 82-86, 87-91, 92-96, 97-101). Ratios 94.1-99.6%, all in band. New names/terms logged in §3.1b and §3.4c above (Anka, Reber, Iker Zabala, Noa Shapira, Lukas, Rasmus, Fondo Meridiano→Meridian Fund, historical terms from Ch84, la consigna→the luggage lockers). Caught and fixed a systemic Anke/Anka mix-up in the pre-v4 Ch87-90 files (one instance slipped through the revision pass and had to be hand-fixed afterward — see the flagged risk note above, worth remembering for any future pre-v4 file audit).

- **Arc "Final Exam" (Ch102-114): COMPLETE.** All 13 chapters done across three sequential batches (102-106, 107-111, 112-114). Ratios 95-99.6%, all in band. New terms logged above (Active Reception, Echo, vereda, Camilo, Milán/Milan collapse, numbers-no-ceiling rule). **Ch114's Spanish source itself had the Anke/Anka bug** (5 instances, genuine author typo — not a translator error like the Ch87-90 case) — fixed directly in the Spanish file 2026-08-06. Full-corpus grep confirms only Ch71 and Ch72 still say "Anke," both legitimately (the real earlier character) — the mix-up appears fully resolved now, but keep the risk in mind for any as-yet-untranslated chapter that mentions either name.

**2026-08-07 — full-corpus Riku gender audit.** Riku is male (author-confirmed). Translation had inconsistently gendered him female in scattered chapters across the whole corpus (a side effect of many different agents/passes translating over a long session, each independently guessing from context since Spanish is pro-drop). Audited every chapter mentioning Riku (~52 files). Fixed: Ch87 (1 instance, missed during an earlier revision pass), Ch92 (1, disambiguated via Spanish "lo miró"), Ch107, Ch108, Ch110 (multiple), Ch112 (8 — including a real mistranslation, not just pronoun: Spanish "el joven de cabellos negros" had been rendered "the dark-haired girl"), Ch114 (1). Everything else checked clean (false positives where a nearby female pronoun correctly referred to Asha/Dara/Nadia/Sisi/Sabine/Petra/Noa/Johanna/Anka/Maren, not Riku). Ch115 has no English translation yet (unrelated gap, see arc note below). Also confirmed while auditing: Ji-ho (BSA line) was already consistently male across all 18 chapters mentioning him — no fix needed there.

**2026-09-28 — "El Cobro" retcon, English side complete.** Old `Chapter 0.md`-`Chapter 7.md` (Kessler/electrical-intern/BLANK NODE RESOLVED canon) backed up to `english/_backup-pre-retcon-el-cobro/`; `Chapter 8.md` onward renumbered +4 to match the Spanish side (see §3.0 above); the new opening arc translated fresh as `Chapter 1.md`-`Chapter 11.md`, all within the 95-102% compression band. Nine downstream chapters with leftover old-canon references (old numbering 10, 14, 15, 23, 24, 28, 32, 33, 34 → new 14, 18, 19, 27, 28, 32, 36, 37, 38) fixed in place to match the Spanish equivalents logged in `plot/retcon-cleanup-log.md`. New §3.0 glossary section added for this arc's terms; clarified afterward that lowercase `blank node`/`empty node` (Oliver's general Odem-anomaly vocabulary, `system/registro.md`) is **not** retired and correctly still appears in Ch60/71 — only the exact `BLANK NODE RESOLVED` system-line and `the Ledger` as a device name are gone. Full details and per-chapter edit log in `plot/retcon-cleanup-log.md` § "Pase en inglés."

**Next:** Book 2's next arc per `plot/structure.md` is **"Cierre de líneas" / "Loose Ends" (Ch115-119)** — Ch115 ("El Quai"/"The Quay") is already written in Spanish and closed per the session log at the top of this project; Ch116-119 are still only planned, not written, in the Spanish source (check before attempting). Confirm scope with the user before starting this arc, since it crosses from "translate what exists" into "the source material may not exist yet" territory. Log any new term or rule that comes up — never leave it loose only inside a translated chapter.

**2026-10-16 — guide v6:** added §1.8 (language references: characters speak English in the English version) and checklist item 9, after Ch146 (Riku says it in Japanese and repeats it to himself in Spanish).
