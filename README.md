# ഗ്രന്ഥം രസവാൻ — Granthom Rasavan

> *Type Malayalam as you learn it. Learn Malayalam as you type it.*

A Malayalam keyboard layout where virama is built into every consonant key, all forms of a sound — base, root, chillu — live on one key, and the layout follows Malayalam's own phonological structure rather than typewriter mechanics or government grids.

Built on 112 million character occurrences from the SMC corpus: **55% home row coverage**, weighted effort score **1.93** vs ~2.20 for InScript, and **10% fewer keystrokes** through pre-composed virama and single-keypress chillu access. Methodology generalises to all Brahmic scripts.

---

## Why Granthom Rasavan?

Every existing Malayalam keyboard — InScript, Remington, Mozhi — was designed around external constraints: typewriter arm lengths, government phonetic grids, Roman transliteration approximations. None were designed around how Malayalam is actually structured or which characters actually appear most in real text.

Granthom Rasavan starts from two foundations:

1. **The script's own logic** — Malayalam is an abugida. A consonant and its virama form are not two independent characters; they are one phoneme in two contexts. The keyboard should reflect that.
2. **Corpus frequency** — 112 million character occurrences tell us exactly which characters a Malayalam typist needs most. The most frequent characters belong on the easiest keys.

### Three Core Innovations

| Innovation | What it means |
|-----------|---------------|
| **Virama built in** | Every consonant key outputs base form unshifted, virama-attached form shifted. No separate virama keystroke for conjuncts. |
| **One key per sound** | Base consonant, virama root, and chillu all on one key across layers. Learn one position, access all forms. |
| **Script-aligned layers** | Normal = most common form. Shift = root/independent. AltGr = word-boundary form (chillu). Follows Malayalam's own phonological structure. |

---

## Layout at a Glance

```
┌────┬────┬────┬────┬────┬────┬────┬────┬────┬────┬────┬────┬────┐
│ ൃ  │ ഛ  │ ഴ  │ ഭ  │ ൊ  │ ധ  │ ഡ  │ ഹ  │ ൈ  │ ഖ  │ ൗ  │ ഘ  │ ഥ  │
│ `  │ 1  │ 2  │ 3  │ 4  │ 5  │ 6  │ 7  │ 8  │ 9  │ 0  │ -  │ =  │
├────┴┬───┴┬───┴┬───┴┬───┴┬───┴┬───┴┬───┴┬───┴┬───┴┬───┴┬───┴┬───┴┐
│     │ ജ  │ ശ  │ ദ  │ ള  │ ോ  │ േ  │ സ  │ ങ  │ ഷ  │ ൂ  │ ഞ  │ ഫ  │
│ Tab │ Q  │ W  │ E  │R^ൾ │ T  │ Y  │ U  │ I  │ O  │ P  │ [  │ ]  │
├─────┴─┬──┴─┬──┴─┬──┴─┬──┴─┬──┴─┬──┴─┬──┴─┬──┴─┬──┴─┬──┴─┬──┴───┤
│       │ െ  │ ാ  │ ക  │ ന  │ ല  │ ം  │ ി  │ ു  │ ത  │ പ  │ ബ   │
│ Caps  │ A  │ S  │D^ൿ │F^ൻ │G^ൽ │H^ഃ │ J  │ K  │ L  │ ;  │ '   │
├───────┴─┬──┴─┬──┴─┬──┴─┬──┴─┬──┴─┬──┴─┬──┴─┬──┴─┬──┴─┬──┴─────┤
│         │ ീ  │ ണ  │ റ  │ ര  │ മ  │ യ  │ ട  │ വ  │ ച  │ ഗ      │
│  Shift  │ Z  │X^ൺ │ C  │V^ർ │ B  │ N  │ M  │ ,  │ .  │ /      │
└─────────┴────┴────┴────┴────┴────┴────┴────┴────┴────┴─────────┘
```

`^X` = chillu accessible via AltGr + that key.
**Caps Lock** = instant toggle to full English QWERTY and back.

---

## How It Works

### Typing a syllable

```
D          →  ക    (base consonant — Normal layer)
Shift + D  →  ക്   (virama root — Shift layer)
AltGr + D  →  ൿ   (chillu — AltGr layer)
```

### Typing a conjunct — no virama key needed

```
Shift+D  Shift+L  J   →   ക്തി   (kti)
  ക്        ത്      ി
```

InScript equivalent: ക + virama-key + ത + virama-key + ി = 5 keystrokes vs 3.

### Typing a chillu

```
AltGr + F  →  ൻ   (na-chillu, most frequent)
AltGr + V  →  ർ   (ra-chillu, second most frequent)
```

---

## Key Metrics

| Metric | Granthom Rasavan | InScript |
|--------|-----------------|----------|
| Weighted effort score (WES) | **1.93** (v1.2) · **1.81** (v3.0 target) | ~2.20 |
| Home row coverage | **55.5%** | ~30% |
| Keystrokes per 23K chars | **~29,400** | ~32,800 |
| Keystroke reduction | **~10%** | baseline |
| Chillu input | **2 keys** (AltGr+key) | 4 keys (ZWJ sequence) |
| Virama for conjuncts | **0** (built into Shift) | 1 explicit keypress each |

---

## Layer Architecture

| Layer | How | Content |
|-------|-----|---------|
| Normal | Unshifted | Base consonant / vowel matra |
| Shift | Shift held | Consonant+virama / independent vowel |
| AltGr | Right Alt held | Chillu / Malayalam digit / specialist |
| AltGr+Shift | Right Alt + Shift | Rare / archaic / Grantha |
| English | Caps Lock | Full US QWERTY |

---

## Live Simulator

Try the layout in your browser — no installation needed:

**[▶ Open Simulator](https://ksjeshin.github.io/granthom-rasavan/)**

- For custom layout, drag keys from the palette onto the keyboard rows to 
- Click any placed key to type that character
- Enable **Physical keyboard** toggle to type using your actual keyboard
- Click a placed key to edit its four layers (Normal / Shift / Symbl / Symbl+Shift)
- **Caps Lock** switches to full English QWERTY and back
- Save and load layouts as JSON to local system

---

## Project Status

| Component | Status |
|-----------|--------|
| Layout design | v1.2 — active |
| Web simulator | Working |
| Corpus analysis | Complete (112M chars) |
| Linux XKB driver | Planned |
| Windows MSKLC | Planned |
| macOS / mobile | Planned |
| User study | Planned |
| arXiv paper | Draft ready |

**Layout is not yet finalised.** Three ergonomic swaps are pending user testing confirmation. See [open issues](issues/open_issues.md).

---

## Repository Structure

```
granthom-rasavan/
├── README.md                     ← this file
├── LICENSE                       ← MIT (code) + CC-BY-4.0 (docs)
├── COPYRIGHT                     ← copyright notice
├── CONTRIBUTING.md               ← how to contribute
├── CHANGELOG.md                  ← version history
├── docs/
│   ├── arxiv/                    ← arXiv academic paper suite
│   │   ├── INDEX.md              ← submission overview and checklist
│   │   ├── paper_main.md         ← full academic paper
│   │   ├── appendix_a_frequency_tables.md
│   │   ├── appendix_b_key_assignment.md
│   │   ├── appendix_c_ergonomic_model.md
│   │   └── appendix_d_keystroke_analysis.md
│   └── design/                   ← project design documentation
│       ├── DESIGN.md             ← core design rationale
│       ├── CORPUS.md             ← corpus methodology explained
│       ├── ERGONOMICS.md         ← ergonomic analysis explained
│       ├── KEYSTROKES.md         ← keystroke efficiency explained
│       └── BRAHMIC.md            ← generalisation to other scripts
├── data/
│   └── character_frequencies.csv ← raw corpus frequency data (49 groups)
├── layout/
│   ├── SPEC.md                   ← layout specification
│   ├── granthom_rasavan_v1.2.json ← current layout definition
│   └── config/                   ← OS keyboard configuration files
│       ├── linux/
│       │   └── README.md         ← XKB symbols file (planned)
│       ├── windows/
│       │   └── README.md         ← MSKLC / Keyman (planned)
│       └── macos/
│           └── README.md         ← Ukelele .keylayout (planned)
├── simulator/
│   └── index.html                ← web simulator (GitHub Pages)
└── issues/
    └── open_issues.md            ← known open design questions
```

---

## Corpus

Character frequency analysis based on the **SMC Malayalam corpus**
(https://github.com/smc/corpus) — approximately 1.7 billion word tokens,
~112 million Malayalam character occurrences analysed.

Raw frequency data: [`data/character_frequencies.csv`](data/character_frequencies.csv)

---

## Generalisation to Other Brahmic Scripts

The phonological grouping principle — Normal=base, Shift=virama form, AltGr=special boundary form — applies without architectural change to any Brahmic script. Tamil, Kannada, Devanagari, and Bengali are identified as immediate candidates. See [`docs/arxiv/paper_main.md §9`](docs/arxiv/paper_main.md) for the framework.

---

## Planned Standardisation Submissions

Post user testing:
- CDAC (InScript standardisation authority)
- Kerala IT Mission
- BIS (Bureau of Indian Standards)
- TDIL (Technology Development for Indian Languages)

---

## License

Code and layout files: [MIT License](LICENSE)
Documentation, paper, and data: [CC-BY-4.0](https://creativecommons.org/licenses/by/4.0/)

Copyright (c) 2025 KSJeshin. All rights reserved.

---

## Acknowledgements

Character frequency analysis based on the SMC Malayalam corpus maintained by
[Swathanthra Malayalam Computing](https://smc.org.in).
Ergonomic model based on [Colemak Mod-DH](https://colemakmods.github.io/mod-dh/)
by stevep99.
