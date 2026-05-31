# Open Issues — Granthom Rasavan

Design questions and unresolved items tracked here until resolved.
Resolved items are moved to CHANGELOG.md.

Last updated: v1.2

---

## Priority 1 — Must resolve before finalising layout

### Issue 01 — DDHA key placement
- **Character:** ഢ (U+0D22), voiced retroflex stop
- **Problem:** No confirmed key in v1.2. Conflict with `` ` `` key (carries ൃ/ഋ vowel group)
- **Frequency:** 4,331 occurrences (0.004%) — rare but must be accessible
- **Candidate:** Symbl layer of TTHA key (`) — phonologically paired (voiced/unvoiced retroflex pair)
- **Status:** Pending decision

### Issue 02 — JHA key placement
- **Character:** ഝ (U+0D1D), voiced palatal stop
- **Frequency:** 896 occurrences (<0.001%) — very rare
- **Candidate:** Symbl layer of CHA key (\) — phonologically paired (voiced/unvoiced palatal pair)
- **Status:** Pending decision

### Issue 03 — ZWJ placement
- **Character:** U+200D (Zero Width Joiner)
- **Use:** Legacy chillu encoding, some conjunct control
- **Candidate:** AltGr + space, or Symbl layer of a low-frequency key
- **Status:** Deferred — evaluate actual need in user testing

### Issue 04 — ZWNJ placement
- **Character:** U+200C (Zero Width Non-Joiner)
- **Use:** Blocking unwanted conjuncts
- **Status:** Deferred — same as ZWJ

### Issue 05 — Num Lock / Caps Lock conflict
- **Problem:** Caps Lock is assigned to English QWERTY toggle. Earlier spec proposed Num Lock ON + Caps Lock ON for Malayalam numeral hardware mode — this now conflicts.
- **Current workaround:** Malayalam digits accessible via AltGr on number row (no Shift needed) — may be sufficient without a hardware numeral mode
- **Options:**
  - A) AltGr-only for Malayalam digits (current — already implemented)
  - B) Scroll Lock as Malayalam numeral toggle
  - C) IME-only toggle, no hardware mode
- **Status:** Pending decision before driver development

---

## Priority 2 — Ergonomic swaps pending user testing

### Issue 06 — N(YA) ↔ I(NGA) swap
- **YA** (rank 8, 4.46%) on N (bottom index, effort 2.2)
- **NGA** (rank 23, 1.30%) on I (top ring, effort 2.0)
- **Estimated gain:** 709,000 weighted effort units
- **Trigger:** User testing confirms improvement
- **Status:** Identified, not implemented

### Issue 07 — B(MA) ↔ U(SA) swap
- **MA** (rank 15, 2.89%) on B (bottom index-inward, effort 3.7) — worst bottom key
- **SA** (rank 16, 2.68%) on U (top middle, effort 2.2)
- **Estimated gain:** 122,000 weighted effort units
- **Status:** Identified, not implemented

### Issue 08 — .(CA) ↔ W(SHA) swap
- **CA** (rank 19, 1.92%) on . (bottom ring, effort 2.7)
- **SHA** (rank 28, 0.72%) on W (top ring, effort 2.5)
- **Estimated gain:** 135,000 weighted effort units
- **Additional benefit:** Frees period key from Malayalam character — reduces bilingual punctuation misfires
- **Status:** Identified, not implemented

---

## Priority 3 — Implementation

### Issue 09 — Linux XKB driver
- **Status:** Not started
- **Next step:** Write XKB symbols file for the v1.2 layout
- **Location:** `layout/xkb/`

### Issue 10 — Windows MSKLC layout
- **Status:** Not started

### Issue 11 — macOS Ukelele layout
- **Status:** Not started

### Issue 12 — Mobile IME
- **Status:** Not started — deferred until desktop implementations stable

### Issue 13 — GitHub Pages simulator
- **Status:** Simulator exists but not yet configured for GitHub Pages
- **Next step:** Move simulator to `simulator/index.html` and enable Pages

---

## Priority 4 — Research and validation

### Issue 14 — User study
- **Target:** 10–15 typists (journalists, students, government users)
- **Design:** WPM and error rate vs InScript baseline after 2-week learning period
- **Status:** Not started — awaiting layout finalisation

### Issue 15 — Old script (പഴയ ലിപി) scope
- **Question:** Does the layout support traditional orthography characters?
- **Status:** Not decided

### Issue 16 — Corpus re-analysis with ൗ corrected
- **Problem:** ൗ (U+0D57) was misclassified as "Other Malayalam" in the original grouped report
- **Status:** Corrected conceptually; formal re-run of corpus analysis pending

---

*To propose a resolution for any issue, open a GitHub Issue referencing the number above.*
