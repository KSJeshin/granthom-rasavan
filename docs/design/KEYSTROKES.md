# Keystroke Efficiency

This document explains how Granthom Rasavan reduces keystrokes compared to InScript, and what that means in practice.

For the full analysis see [`docs/arxiv/appendix_d_keystroke_analysis.md`](../arxiv/appendix_d_keystroke_analysis.md).

---

## The Bottom Line

Typing the same Malayalam text requires **~10% fewer keystrokes** on Granthom Rasavan than on InScript.

On a real 23,333-character Malayalam newspaper article:

| Layout | Keystrokes | Difference |
|--------|-----------|------------|
| InScript | 32,833 | baseline |
| Granthom Rasavan | ~29,400 | **−3,400 fewer** |

That is roughly 3,400 keystrokes saved per article — before accounting for the fact that each of those remaining keystrokes is also ergonomically easier on average.

---

## Where the Saving Comes From

### 1. Virama — saves ~2,963 keystrokes per article

In InScript, every conjunct consonant requires an explicit virama keypress. The benchmark article had 2,963 virama codepoints — meaning 2,963 extra keystrokes just for viramas.

In Granthom Rasavan, the virama is embedded in the Shift action. Pressing Shift+F produces ന് (na + virama) in one action. Zero separate virama keystrokes.

```
InScript:   ന  +  ്  +  ത  =  ന്ത   (3 keystrokes)
Granthom:   Shift+F  +  L  =  ന്ത   (2 keystrokes)
```

**This one change accounts for 9% of the total saving.**

### 2. Chillus — saves ~1,018 keystrokes per article

The benchmark article had 509 chillus. Each chillu in InScript requires 4 keystrokes (base + virama + AltGr + Space). In Granthom Rasavan, each chillu is 2 keystrokes (AltGr + key).

```
InScript:   ര  +  ്  +  AltGr  +  Space  =  ർ   (4 keystrokes)
Granthom:   AltGr  +  V                  =  ർ   (2 keystrokes)
```

Saving per article: 509 × 2 = 1,018 keystrokes.

### 3. Independent vowel overhead — adds ~495 keystrokes

This is the one cost. In InScript, independent vowels (ഇ, ഉ, ആ etc.) are on the Normal layer — 1 keypress each. In Granthom Rasavan, matras are on Normal and independent vowels are on Shift — 2 key events each.

The benchmark article had 495 independent vowels, adding 495 extra Shift events.

This is the correct tradeoff: matras (Normal) are 10–20× more frequent than independent vowels (Shift). Granthom Rasavan puts the more common form on the easier layer and accepts a minor cost for the less common form.

### Net

| Source | Saving |
|--------|--------|
| Virama eliminated | +2,963 |
| Chillus 4→2 presses | +1,018 |
| Independent vowel overhead | −495 |
| Minor misc | −41 |
| **Total** | **+3,445** |

---

## Why It Compounds with Ergonomics

The keystroke saving and the ergonomic improvement are independent effects that both apply simultaneously:

- ~10% fewer keystrokes per session
- Each remaining keystroke ~12% ergonomically easier (WES 1.93 vs ~2.20)

Fewer presses, each easier. Both effects reduce physical fatigue over a long writing session.

---

## Register Sensitivity

The saving is larger in texts with more conjuncts and chillus, smaller in texts with fewer.

| Register | Conjunct density | Expected saving |
|----------|-----------------|----------------|
| Formal / literary Malayalam | High | ~10–15% |
| Journalistic Malayalam | Moderate–high | ~10% (measured) |
| Colloquial / social media | Low | ~6–8% |
| Sanskrit-origin text | Very high | ~15%+ |

The virama saving scales directly with conjunct density — the more conjuncts in the text, the larger the advantage.

---

## This Does Not Include Learning Curve

The 10% saving is the theoretical gain once the layout is learnt. During the transition period (typically 4–8 weeks to reach baseline speed on a new layout), a typist will be slower than on their current layout. The long-term gain needs to be weighed against the short-term transition cost.
