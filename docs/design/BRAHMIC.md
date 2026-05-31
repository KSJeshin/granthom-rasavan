# Generalisation to Other Brahmic Scripts

Granthom Rasavan's design methodology applies to all Brahmic scripts — not just Malayalam. This document explains how and gives starting points for each major Indian language.

For the academic treatment see [`docs/arxiv/paper_main.md §9`](../arxiv/paper_main.md).

---

## Why It Generalises

All major Indian scripts share the same abugida structure:

- Every consonant carries an inherent vowel /a/
- A virama/halant/pulli suppresses the inherent vowel to give a pure consonant
- Dependent vowel signs (matras) modify the inherent vowel
- Conjuncts form by consonant + virama + consonant
- Independent vowels appear at word beginnings or after other vowels

This means the three-layer design rule applies identically to every Brahmic script:

```
Normal  →  base consonant / vowel matra
Shift   →  consonant + virama form / independent vowel
AltGr   →  special word-boundary form / language digit
```

Only the Unicode codepoints, the corpus, and the character group definitions change. The architecture is the same.

---

## Cross-Script Equivalences

| Feature | Malayalam | Tamil | Kannada | Devanagari | Bengali |
|---------|-----------|-------|---------|------------|---------|
| Virama name | chandrakkala | pulli | virama | halant | hasanta |
| Virama codepoint | U+0D4D | U+0BCD | U+0CCD | U+094D | U+09CD |
| Special forms | chillus | word-final pulli | — | half-forms | ya-phala, ra-phala |
| Unicode block | 0D00–0D7F | 0B80–0BFF | 0C80–0CFF | 0900–097F | 0980–09FF |
| Digits | ൦–൯ 0D66–0D6F | ௦–௯ 0BE6–0BEF | ೦–೯ 0CE6–0CEF | ०–९ 0966–096F | ০–৯ 09E6–09EF |

---

## How to Create a Layout for Another Script

**Steps 1–3 are language-specific. Steps 4–7 are identical for every Brahmic script.**

### Step 1 — Build a corpus
Find the largest available text corpus for the target language. The SMC corpus model works well — Wikipedia dumps, news archives, and literary sources combined give a representative formal register.

### Step 2 — Extract character frequencies
Count every Unicode codepoint in the script's block. Group phonologically related forms (base + virama + special form) into character groups. Sum the group frequencies.

### Step 3 — Rank groups by frequency
Sort all groups highest to lowest. This ranking drives all key placement decisions.

### Step 4 — Assign keys by frequency rank (universal)
Match groups to keys in frequency order: most frequent group → lowest effort key (home row, strong finger). Use the Colemak Mod-DH effort scores or your own validated model.

### Step 5 — Apply the layer rule (universal)
```
Normal  =  base consonant / vowel matra
Shift   =  consonant + virama / independent vowel
AltGr   =  special word-boundary form / language digit
```

### Step 6 — Place language digits on AltGr number row (universal)
AltGr + 1 through 0 = language-specific digits. No Shift required.

### Step 7 — Caps Lock = English QWERTY (universal)
Same bilingual toggle model works for every Indian language.

---

## Language-Specific Notes

### Tamil
- The pulli (் U+0BCD) is the virama equivalent
- Tamil uses fewer conjuncts in pure Tamil vocabulary but word-final pulli forms are frequent — AltGr access to common word-final forms would replicate the chillu saving
- Tamil99 already applied frequency-based placement for Tamil; the Granthom framework extends it with the grouping principle
- Reference corpus: Tamil Wikipedia + news

### Kannada
- Closest structural sibling to Malayalam — 49 consonants, near-identical mechanics
- The virama is ್ (U+0CCD)
- A Kannada Rasavan variant requires substituting Kannada Unicode ranges (U+0C80–U+0CFF) and Kannada corpus frequencies — minimal structural change
- Reference corpus: Kannada Wikipedia + news

### Devanagari / Hindi
- The halant is ् (U+094D)
- Hindi formal register is heavy with Sanskrit-origin conjunct clusters — the virama-on-Shift advantage is particularly large
- Devanagari half-forms (visual rendering of consonant + halant) are handled by the shaping engine (HarfBuzz, Uniscribe) — the keyboard outputs canonical Unicode and the renderer does the visual work
- Reference corpus: Hindi Wikipedia + news

### Bengali
- The hasanta is ্ (U+09CD)
- Ya-phala (য-ফলা) and ra-phala (র-ফলা) are functionally equivalent to Malayalam chillus — highly frequent special forms of ya and ra
- These would be placed on AltGr of their base consonant keys, exactly as Malayalam chillus are
- Reference corpus: Bengali Wikipedia + Anandabazar Patrika archive

---

## Contributing a Brahmic Script Variant

If you want to create a Granthom Rasavan variant for another script:

1. Open an issue with the target language
2. Share your corpus source
3. We will help with the grouping methodology and key assignment
4. The resulting layout will be added to this repository under `layout/variants/`

The core architecture, layer rules, and ergonomic model are reusable. The language-specific work is the corpus analysis — typically 2–3 days of data processing.
