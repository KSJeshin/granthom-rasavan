# Granthom Rasavan — macOS Keyboard Configuration

**Status:** Planned — configuration file not yet created
**Tool:** Ukelele — Unicode Keyboard Layout Editor

---

## What Goes Here

```
macos/
└── Granthom Rasavan.bundle    ← Ukelele keyboard bundle
    ├── Contents/
    │   └── Resources/
    │       └── Granthom Rasavan.keylayout   ← XML layout definition
    └── Icon.icns                             ← optional icon
```

The complete key map to implement is in:
[`docs/paper/appendix_b_key_assignment.md`](../../../docs/paper/appendix_b_key_assignment.md)

---

## Toolchain

### Ukelele
- Free tool by SIL International
- Download: https://software.sil.org/ukelele/
- Produces a `.keylayout` file (XML) and optionally a `.bundle`
- Installs as a native macOS keyboard layout — appears in System Settings
- Supports up to 8 modifier-key combinations — more than enough for Granthom Rasavan

---

## How to Install (once file is available)

1. Copy `Granthom Rasavan.bundle` to one of:
   - `~/Library/Keyboard Layouts/` — current user only
   - `/Library/Keyboard Layouts/` — all users (requires admin password)

2. Log out and log back in (or restart)

3. Go to **System Settings → Keyboard → Input Sources → +**

4. Search for **Malayalam** — select **Granthom Rasavan**

5. Switch using the Input Sources menu in the menu bar or `Ctrl+Space`

---

## Layer Mapping on macOS

macOS modifier key terminology differs from Linux/Windows:

| Granthom Rasavan layer | macOS activation |
|------------------------|-----------------|
| Normal | Unmodified |
| Shift | Shift |
| AltGr (Layer 3) | Option (Alt) |
| AltGr+Shift (Layer 4) | Option + Shift |
| English (Caps Lock toggle) | Caps Lock |

The right Option key will be mapped as the AltGr equivalent for chillu access.
On macOS, Option key behaviour in `.keylayout` files is set via the `action` element.

---

## Caps Lock Behaviour on macOS

macOS allows Caps Lock remapping in System Settings → Keyboard → Modifier Keys.
For Granthom Rasavan, Caps Lock switching between Malayalam and English input
sources can be configured either:

- **Within the `.keylayout` file** — using Ukelele's modifier mapping
- **Via a system shortcut** — mapping Caps Lock to switch input sources in
  System Settings → Keyboard → Keyboard Shortcuts → Input Sources

This will be decided during implementation. See
**Issue 05** in [issues/open_issues.md](../../../issues/open_issues.md).

---

## Malayalam Unicode Rendering on macOS

macOS has built-in CoreText support for Malayalam Unicode since OS X 10.7.
The layout outputs standard Unicode sequences — no custom renderer required.
Recommended fonts: Noto Sans Malayalam (available via Google Fonts),
Malayalam system fonts included with macOS.

---

## Contributing

If you have Ukelele experience and want to implement this configuration,
see [CONTRIBUTING.md](../../../CONTRIBUTING.md) and open an issue
referencing **Issue 11** in [issues/open_issues.md](../../../issues/open_issues.md).

Ukelele documentation:
https://software.sil.org/ukelele/
