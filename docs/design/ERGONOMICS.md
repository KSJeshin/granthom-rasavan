# Ergonomic Analysis

This document explains the ergonomic measurements behind the layout in plain language — what was measured, how, and what the numbers mean.

---

## What Is the Weighted Effort Score?

The Weighted Effort Score (WES) measures the average ergonomic cost of typing one character in a given language on a given layout.

Every key on the keyboard has a difficulty score — how hard it is for your finger to reach that key from its resting position. The WES is the average of all those scores, weighted by how often each key is used in real text.

**WES = average effort per keystroke across all Malayalam typing**

Lower is better. The theoretical minimum (if every character were on the home row, index finger) is 1.0.

---

## Effort Scores — The Model

Key difficulty scores come from the **Colemak Mod-DH** model, which was built by studying how far fingers travel from their natural resting positions on a standard keyboard.

Key factors in the score:

| Factor | Effect |
|--------|--------|
| Row | Home row = lowest; number row = highest |
| Finger | Index = easiest; pinky = hardest |
| Lateral stretch | Reaching inward (G, H) or far outward costs more |

Examples:
- F key (left index, home row) = **1.0** — easiest possible
- J key (right index, home row) = **1.0** — equally easy
- B key (left index, bottom inward curl) = **3.7** — one of the hardest
- \ key (right pinky, top far) = **5.6** — hardest on the keyboard

---

## Granthom Rasavan Results

| Layout | WES | Notes |
|--------|-----|-------|
| Theoretical minimum | 1.000 | Home row only |
| Granthom Layout v1.2 | **1.93** | Current layout |
| Granthom Layout v3.0 | **1.81** | Optimised target — pending testing |
| InScript Malayalam | ~2.20 | Estimated |
| Colemak (English) | 1.84 | Best Latin layout |
| QWERTY (English) | ~3.00 | Baseline |

Granthom Layout v1.2 scores 1.93 — 12% easier per keystroke than InScript's estimated 2.20. The v3.0 optimised assignment reaches 1.81 — 18% easier — but needs user testing before being adopted.

---

## Home Row Coverage

55.5% of all Malayalam typing stays on the home row.

This means: for more than half of every keystroke in a typical Malayalam text, your fingers do not move from their resting position at all.

| Row | Coverage | Average effort |
|-----|----------|---------------|
| Home (incl. G, H stretch) | 55.5% | 1.442 |
| Bottom | 27.0% | 2.382 |
| Top | 13.6% | 2.558 |
| Number | 3.9% | 3.427 |

**Comparison:** InScript Malayalam has approximately 30% home row coverage. Granthom Layout's 55.5% is an 85% relative improvement.

**Note on G and H:** These are technically home row positions but require an inward index-finger stretch (effort 2.9 each). They carry the LA group (ല, 3.8%) and A group (ം, 3.7%). If you count only the strict eight home positions (A S D F J K L ;), coverage is 47.3% — still well above InScript.

---

## Hand Balance

Left hand: **48.6%** · Right hand: **51.4%**

Near-perfect balance. The slight right dominance comes from placing the most frequent character (ി, 9.1%) on J (right index).

The layout is vowel-dominant on the left hand and consonant-dominant on the right — which promotes natural hand alternation. Malayalam syllable structure is consonant-vowel, so consecutive keystrokes tend to alternate between hands. This is the same ergonomic principle behind Dvorak and Colemak for English.

---

## The Main Tradeoff

Malayalam has 36 consonants and 13 vowels — 49 character groups in total — on a keyboard with only 11 home row slots. Some high-frequency groups cannot be on the home row no matter what.

The layout's biggest ergonomic tradeoff:

| Key | Group | Frequency | Effort | Why not on home row |
|-----|-------|-----------|--------|---------------------|
| V | RA ര | 5.48% | 2.2 | Home row full at ranks 1–11 |
| N | YA യ | 4.46% | 2.2 | Same reason |
| B | MA മ | 2.89% | 3.7 | Worst bottom key — swap candidate |

RA and YA at effort 2.2 (bottom index) are not terrible — bottom index is a strong position. MA at B (effort 3.7) is the genuine cost. A swap (B↔U) is under consideration pending user testing.

---

## What the WES Does Not Capture

The WES measures single-keystroke effort only. Three things are not in the score but also work in the layout's favour:

1. **Virama elimination** — ~10% fewer keystrokes total means the WES advantage compounds with keystroke reduction
2. **Hand alternation** — vowels left, consonants right promotes alternating keystrokes; same-finger frequency is not yet formally measured
3. **Modifier key effort** — AltGr holds for chillus are not counted in the WES; these are real but infrequent

---

## Limitations of the Model

The Colemak Mod-DH model was built for English typing on a standard staggered keyboard. It has not been independently validated for Malayalam. The scores are useful for *comparing layouts against each other* but should not be treated as absolute predictions of typing speed. Formal user studies will provide the ground truth.
