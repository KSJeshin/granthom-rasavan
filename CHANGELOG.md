# Changelog

All notable changes to Granthom Rasavan are documented here.

Format: `[version] — date — summary`

---

## [v1.2] — 2025 — Current

### Layout
- Layer architecture locked: Normal=base, Shift=virama, AltGr=chillu/digit, Caps=English, Shift on Caps=Capital English
- 47 character groups assigned to main keys
- 2 groups pending placement (DDHA, JHA)
- SA↔LLA swap applied to separate lateral-consonant chillus across rows
- Virama exception documented: ണ and ഞ retain Normal=base despite virama-dominant corpus profile

### Analysis
- Corpus: SMC Malayalam corpus, ~112M character occurrences
- 49 character groups defined by phonological family
- WES calculated: 1.93 (v1.2 layout) · 1.806 (v3.0 analysis optimum, not yet implemented)
- Home row coverage: 55.5% (inclusive) · 47.3% (strict eight)
- Keystroke comparison vs InScript: ~10% reduction on 23,333-char benchmark

### Documentation
- arXiv paper suite: 5 documents (paper + 4 appendices)
- Supplementary data: character_frequencies.csv
- GitHub repository initialised

### Pending
- Three ergonomic swaps under review: N↔I, B↔U, .↔W
- DDHA (ഢ) and JHA (ഝ) key placement unresolved
- ZWJ (U+200D) and ZWNJ (U+200C) placement deferred
- Num Lock / Caps Lock numeral mode conflict unresolved
- OS Configuration files: not started
- User study: not started

---

## [v1.1] — Earlier session

- Virama decision reversed: Normal=base (was Normal=virama+consonant)
- Caps Lock assigned to English QWERTY toggle
- AltGr layer assigned to chillus
- Symbol layer designed with mnemonic anchoring
- AU group corrected: ൗ recategorised from "Other" into AU group
- A group corrected: ഃ added to phonological family

---

## [v1.0] — Initial design

- Pre-composed virama concept introduced
- Four-quadrant key system defined
- Three extra center keys (★1 ★2 ★3) specified for custom hardware (later removed)
- Symbl+Space toggle system designed
- Chillu auto-promotion rules drafted (later removed)
- Initial corpus analysis completed
