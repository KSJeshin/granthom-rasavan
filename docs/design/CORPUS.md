# Corpus Methodology

This document explains how character frequencies were measured and how they were used to design the layout. Written for contributors and anyone who wants to understand or reproduce the analysis.

For the academic treatment see [`docs/arxiv/paper_main.md §3`](../arxiv/paper_main.md).
Raw frequency data: [`data/character_frequencies.csv`](../../data/character_frequencies.csv)

---

## The Corpus

**Source:** SMC Malayalam corpus — https://github.com/smc/corpus
**Size:** ~1.7 billion word tokens (SMC-reported)
**Characters analysed:** ~112 million Malayalam codepoint occurrences
**Genre:** Wikipedia, news archives, literature — primarily formal written Malayalam
**Period:** Approximately 2010–2020

The SMC corpus is the largest publicly available Malayalam text collection and has been used in previous Malayalam computational linguistics work.

**Known limitation:** The corpus is weighted toward formal written register. Colloquial, dialectal, and social media Malayalam may have different frequency distributions. The layout is optimised for formal written Malayalam — how well it generalises to other registers is an open question for user testing.

---

## What Was Counted

Every Unicode codepoint in the Malayalam block (U+0D00–U+0D7F) was counted individually. This gives raw counts like:

- ി (U+0D3F, I-matra): 9,746,850 occurrences
- ന (U+0D28, NA base): 4,427,472 occurrences
- ന് (U+0D28 + U+0D4D, NA virama): 3,073,118 occurrences
- ൻ (U+0D7B, NA chillu): 842,921 occurrences

---

## The Grouping Principle

Raw codepoint counts are not sufficient for keyboard design because phonologically related forms are not independent choices.

When a typist types the word *nalla* (നല്ല), they do not independently choose ന and then ല — they choose the phoneme /na/ in a context where it is followed by /la/. The base form ന and the virama form ന് are both /na/; the surface form depends on what follows.

**The grouping rule:** all phonologically related surface forms of one sound are combined into one **character group** and assigned to one key:

- **Consonant group:** base consonant + virama-attached root + chillu (if it exists)
- **Vowel group:** vowel matra + independent vowel form

The combined frequency of all members of a group determines which key it gets.

### Example: NA group

| Form | Unicode | Count | Role |
|------|---------|-------|------|
| ന | U+0D28 | 4,427,472 | Base — Normal layer |
| ന് | U+0D28+U+0D4D | 3,073,118 | Root — Shift layer |
| ൻ | U+0D7B | 842,921 | Chillu — AltGr layer |
| **Total** | | **8,343,511** | → Key F (rank 2) |

---

## Layer Assignment from Frequency

Within each group, the layer assignment follows frequency:

**Consonants:** Base form is more frequent than virama form in 32 of 34 consonants. Combined corpus-wide: 73.2% of consonant occurrences are base form. So Normal=base, Shift=virama is data-supported for almost every consonant.

**Two exceptions:** ണ (NNA) and ഞ (NYA) have more virama occurrences than base. Both retain Normal=base for layout-wide consistency — one rule, no exceptions.

**Vowels:** Matra form is more frequent than independent vowel in all 13 vowel groups (78%–96%). Normal=matra, Shift=independent is unambiguous.

---

## How Groups Were Ranked

All 49 groups were sorted by combined frequency — highest to lowest. This ranking determines key placement: rank 1 gets the easiest key, rank 2 gets the second easiest, and so on.

The top 11 groups (covering 55.5% of corpus frequency) all land on home row keys. See [`data/character_frequencies.csv`](../../data/character_frequencies.csv) for the complete ranked list.

---

## Reproducing the Analysis

The raw frequency data is in `data/character_frequencies.csv`. Columns:

| Column | Description |
|--------|-------------|
| rank | Frequency rank (1 = most frequent) |
| group_id | Group name |
| group_type | consonant or vowel |
| normal_layer | Character on Normal layer |
| normal_unicode | Unicode codepoint |
| shift_layer | Character on Shift layer |
| shift_unicode | Unicode codepoint |
| altgr_layer | Character on AltGr layer |
| altgr_unicode | Unicode codepoint |
| raw_count | Combined raw count from corpus |
| frequency_pct | Percentage of total Malayalam characters |
| key | Assigned key in v1.2 layout |
| effort | Colemak Mod-DH effort score |
| hand | L or R |
| row | home / top / bottom / num |
| finger | Finger assignment |

To reproduce the WES calculation:
```
WES = sum(effort × raw_count) / sum(raw_count)
    = 216,335,392 / 112,340,913
    = 1.9257
```

---

## Contributing to Corpus Work

If you have access to Malayalam text corpora not in the SMC collection — particularly colloquial, social media, or technical register text — please open an issue. A multi-register frequency analysis would strengthen the layout's claim to general Malayalam optimisation.
