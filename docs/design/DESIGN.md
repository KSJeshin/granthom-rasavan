# Granthom Layout — Design Rationale

This document explains the thinking behind every major design decision in the layout. It is written for contributors, researchers, and anyone who wants to understand why the layout works the way it does.

---

## The Starting Problem

Every Malayalam keyboard in use today was designed around something other than Malayalam:

- **InScript** — designed around a pan-Indian phonetic grid that must work for 12 scripts simultaneously. No single language is optimised.
- **Remington** — designed around typewriter arm lengths from the 1970s.
- **Mozhi / Manglish** — designed for people who already know Roman script. Requires you to approximate Malayalam sounds in English letters.

None of these start from the question: *what does Malayalam actually need?*

Granthom Rasavan project starts there.

---

## Two Foundations

### 1. The script's own structure

Malayalam is an abugida. The fundamental insight is:

> A consonant and its virama form are not two separate characters. They are one phoneme appearing in two different contexts.

ന (na-base) and ന് (na-virama) are both /na/. The difference is what comes after. A keyboard that puts them on different unrelated keys forces the typist to think in terms of Unicode codepoints rather than sounds.

Granthom Layout puts them on the same key — base on Normal, virama-attached on Shift. The typist thinks "na" and presses F. How much of /na/ they need (base, root, or final chillu) is handled by which modifier they hold.

### 2. Corpus frequency

112 million Malayalam character occurrences from the SMC corpus tell us which characters appear most in real text. The most frequent characters belong on the easiest keys — the home row, the strong fingers.

The two most frequent Malayalam characters are ി (9.1%) and ന (7.4%). In Granthom Layout they sit on J and F — the two strongest home-row positions. In InScript they do not.

---

## The Three Layer Rules

These rules apply without exception to every key in the layout:

| Layer | Consonant keys | Vowel keys |
|-------|---------------|------------|
| Normal | Base consonant (ക) | Vowel matra (ി) |
| Shift | Consonant + virama (ക്) | Independent vowel (ഇ) |
| AltGr | Chillu (ൿ) where it exists | Malayalam digit |

**Why Normal = base, not virama?**
73.2% of all consonant occurrences in the corpus are the base form. The most common form belongs on the unshifted layer.

**Why Shift = virama-attached?**
Because conjuncts — the most distinctive feature of Malayalam typography — form naturally without any separate virama keystroke. Shift+F gives ന്, followed by Shift+L gives ത്, giving ന്ത automatically. Three keystrokes, no explicit virama.

**Why AltGr = chillu?**
Chillus are word-final forms — they appear at word boundaries. AltGr (right thumb) + left-hand key is a deliberate two-key combination that signals "I want the boundary form of this sound." It matches the phonological reality: you only need a chillu in a specific context.

---

## The Virama Decision

This was the most consequential design decision.

**Old approach (InScript):** virama is an independent key. To type ക്ത, you press ക, then the virama key, then ത — three keystrokes.

**Granthom Rasavan approach:** virama is the Shift attribute of the consonant. To type ക്ത, you press Shift+D, then L — two keystrokes. The virama is produced by the Shift action itself.

**Why this matters:** A 23,333-character Malayalam text contains 2,963 virama codepoints. Every single one of those is a free keystroke in Granthom Layout — they cost nothing because they are embedded in the Shift action that produces the virama-attached form. This alone accounts for a 9% keystroke reduction.

**The deeper reason:** In Malayalam orthography, the virama is a modifier mark *on* the consonant — not a free-standing letter. The keyboard should reflect that. Shift is a modifier action on a key, not a separate keypress. The structure matches.

---

## The Chillu Decision

Malayalam has six dedicated Unicode codepoints for word-final pure consonants (U+0D7A–U+0D7F). Using them correctly matters for text rendering, search, and sorting.

InScript accesses chillus via a ZWJ sequence: base + virama + AltGr + Space — four keystrokes per chillu. A text with 509 chillus costs 2,036 keystrokes just for chillus in InScript.

In Granthom Layout: AltGr + the consonant key = 2 keystrokes. Same 509 chillus cost 1,018 keystrokes. Saving: 1,018 per typical article.

**Why all five frequent chillus on left-hand keys?**
Because AltGr is the right thumb. If a chillu is on a right-hand key, the right thumb and right finger must work together — awkward. All five high-frequency chillus (ൻ ർ ൽ ൾ ൺ) are on left-hand keys so the right thumb holds AltGr while a left finger presses the character key — natural and fast.

---

## The Caps Lock Decision

Caps Lock switches to full English QWERTY. This means:

- No IME menu navigation to switch languages
- No OS language switching shortcut to memorise
- One key toggles between full Malayalam and full English
- Toggle is symmetric — same key in both directions

Malayalam text routinely contains English words, technical terms, URLs, and numerals. The ability to drop into English for a word and come back instantly — without leaving the keyboard — is essential for practical everyday use.

---

## Key Assignment — Why These Positions?

Groups were ranked by corpus frequency and assigned to keys ranked by ergonomic effort (Colemak Mod-DH model). Most frequent group → easiest key. This is the core principle.

Three overrides were applied:

**Override 1 — Chillu hand constraint**
The five frequent chillus must be on left-hand keys (see above). This required swapping NA and KA between D and J — a cost of 0.1 effort units, negligible.

**Override 2 — Chillu separation**
Two lateral consonant chillus (ൽ and ൾ) were going to land on adjacent bottom-row fingers — easy to confuse during learning. Swapping SA and LLA separated them onto different rows and fingers.

**Override 3 — Virama exception**
ണ and ഞ have more virama occurrences than base occurrences in the corpus. Strict optimisation would put virama on Normal for these two keys. The layout keeps Normal=base for both — one consistent rule across all 34 consonants is worth more than marginal efficiency on two low-frequency consonants.

---

## What Is Not Yet Decided

See [`issues/open_issues.md`](../../issues/open_issues.md) for the full list. The main open questions:

- DDHA (ഢ) and JHA (ഝ) key placement
- ZWJ and ZWNJ positions
- Num Lock / Caps Lock numeral mode conflict
- Three ergonomic swaps pending user testing confirmation

The layout will be finalised after user testing. This document and all related files will be updated at that point.
