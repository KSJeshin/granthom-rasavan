# Contributing to Granthom Rasavan

Thank you for your interest in contributing. The project is currently in active design phase — contributions are welcome in the areas below.

---

## What We Need Most Right Now

### 1. Layout Testing
The most valuable contribution at this stage is **typing feedback**.
- Use the web simulator and type real Malayalam text
- Report which key positions feel uncomfortable or counterintuitive
- Report any issues with conjunct formation or chillu access
- Open an issue with your findings

### 2. Corpus Contributions
- If you have access to Malayalam text corpora not represented in the SMC corpus (colloquial, dialectal, social media, technical) — contact us
- Help verify the character frequency counts

### 3. OS Keyboard Configuration

The layout needs configuration files for all three platforms.
Each platform uses a different tool — pick the one you know:

| Platform | Tool | Folder | Issue |
|----------|------|--------|-------|
| Linux | XKB symbols file | `layout/config/linux/` | Issue 09 |
| Windows | MSKLC `.klc` or Keyman | `layout/config/windows/` | Issue 10 |
| macOS | Ukelele `.keylayout` bundle | `layout/config/macos/` | Issue 11 |

The complete four-layer key map to implement is in
[`docs/paper/appendix_b_key_assignment.md`](docs/paper/appendix_b_key_assignment.md).

Each platform folder has a `README.md` with tool download links,
installation instructions, and implementation notes.
If you want to work on any platform, open an issue referencing the
issue number above to coordinate before starting.

### 4. Documentation
- Translation of documentation into Malayalam
- Corrections to Malayalam script usage in any file
- Improvements to the web simulator UI

---

## How to Contribute

1. **Fork** the repository
2. **Create a branch** — `git checkout -b your-feature-name`
3. **Make your changes**
4. **Commit** — `git commit -m "clear description of change"`
5. **Push** — `git push origin your-feature-name`
6. **Open a Pull Request** — describe what you changed and why

---

## Reporting Issues

Use GitHub Issues for:
- Layout design feedback
- Bug reports in the simulator
- Incorrect Unicode codepoints
- Corpus data questions

Please check [issues/open_issues.md](issues/open_issues.md) before opening a new issue — your question may already be tracked.

---

## Code of Conduct

- Be respectful and constructive
- Feedback on the layout is welcome — disagreement is fine, personal criticism is not
- This project serves the Malayalam-speaking community; keep that goal central

---

## Contact

Open a GitHub Issue for all project-related communication.
