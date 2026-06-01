# Granthom Layout — Linux Keyboard Configuration (XKB)

**Status:** Planned — configuration file not yet created
**Tool:** XKB (X Keyboard Extension) — built into all major Linux desktop environments

---

## What Goes Here

```
linux/
└── ml_granthom_rasavan     ← XKB symbols file (plain text)
```

The XKB symbols file defines all four layers of the layout:
- Layer 1 (Normal) — base consonant / vowel matra
- Layer 2 (Shift) — consonant+virama / independent vowel
- Layer 3 (AltGr / ISO Level 3) — chillu / Malayalam digit / specialist
- Layer 4 (AltGr+Shift) — rare / archaic / Grantha

The complete key map to implement is in:
[`docs/paper/appendix_b_key_assignment.md`](../../../docs/paper/appendix_b_key_assignment.md)

---

## How to Install (once file is available)

```bash
# Copy the symbols file to the XKB directory
sudo cp ml_granthom_rasavan /usr/share/X11/xkb/symbols/

# Activate for current session
setxkbmap ml_granthom_rasavan

# Check it is active
setxkbmap -query
```

**Permanent activation** — add to your desktop session startup or `~/.xinitrc`:
```bash
setxkbmap ml_granthom_rasavan
```

**GNOME / KDE users:** The layout will also be available through
Settings → Keyboard → Input Sources once the symbols file is installed.

---

## Caps Lock Behaviour

In this layout Caps Lock switches to full English QWERTY.
The XKB configuration will use the `ctrl:nocaps` or a custom action
to reassign Caps Lock. This does not affect system-level Caps Lock
in other applications — it is layout-local.

---

## AltGr Key

The right Alt key acts as ISO Level 3 modifier (AltGr) for chillu access.
On keyboards without a physical AltGr key, right Alt is used by default
on most Linux systems. No additional configuration needed.

---

## Contributing

If you have XKB experience and want to implement this configuration,
see [CONTRIBUTING.md](../../../CONTRIBUTING.md) and open an issue
referencing **Issue 09** in [issues/open_issues.md](../../../issues/open_issues.md).

XKB symbols file format reference:
https://www.x.org/releases/X11R7.7/doc/xorg-docs/input/XKB-Enhancing.html
