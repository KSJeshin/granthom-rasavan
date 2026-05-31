# Granthom Rasavan — Layout Specification

**Version:** 1.2 (current implementation)
**Status:** Active development — layout not yet finalised
**JSON definition:** `granthom_rasavan_v1.2.json`

See [open issues](../issues/open_issues.md) for pending design decisions.
See [docs/paper/appendix_b_key_assignment.md](../docs/paper/appendix_b_key_assignment.md) for the complete four-layer key map.

---

## Layer Architecture

| Layer | Activation | Content |
|-------|-----------|---------|
| Normal | Unshifted | Base consonant / vowel matra / anusvara |
| Shift | Shift held | Consonant+virama / independent vowel |
| AltGr | Right Alt held | Chillu / Malayalam digit / specialist |
| AltGr+Shift | Right Alt + Shift | Rare / archaic / Grantha |
| English | Caps Lock ON | Full US QWERTY |

## Core Design Rules

1. **Normal = base form** — the most frequent form of every character group
2. **Shift = root form** — consonant+virama or independent vowel
3. **AltGr = boundary form** — chillu (word-final) or Malayalam digit
4. **One key per phoneme** — all surface forms of a sound on one key
5. **Caps Lock = English** — instant full QWERTY toggle, no IME switching

## Virama Rule

The virama (്, U+0D4D) is NOT a separate key.
It is the Shift attribute of every consonant key.

```
Shift + F  →  ന്   (NA + virama)  ← two codepoints output: U+0D28 + U+0D4D
F          →  ന    (NA base)       ← one codepoint: U+0D28
AltGr + F  →  ൻ   (NA chillu)     ← one codepoint: U+0D7B
```

## Chillu Assignments

| Chillu | Key | AltGr combination |
|--------|-----|------------------|
| ൻ U+0D7B | F | AltGr + F |
| ർ U+0D7C | V | AltGr + V |
| ൽ U+0D7D | G | AltGr + G |
| ൾ U+0D7E | R | AltGr + R |
| ൺ U+0D7A | X | AltGr + X |
| ൿ U+0D7F | D | AltGr + D |

All five high-frequency chillus on left-hand keys for right-thumb AltGr access.

## Version History

| Version | WES | Notes |
|---------|-----|-------|
| v1.2 (current) | 1.93 | Current simulator layout |
| v3.0 target | 1.806 | Analysis optimum — pending user testing |

For full ergonomic analysis see [docs/paper/appendix_c_ergonomic_model.md](../docs/paper/appendix_c_ergonomic_model.md).

## Platform Configuration Files

OS-level keyboard configuration files are in `layout/config/`:

| Platform | Folder | Tool | Status |
|----------|--------|------|--------|
| Linux | `config/linux/` | XKB symbols file | Planned |
| Windows | `config/windows/` | MSKLC `.klc` or Keyman | Planned |
| macOS | `config/macos/` | Ukelele `.keylayout` bundle | Planned |
