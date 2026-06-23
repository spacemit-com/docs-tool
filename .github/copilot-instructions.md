# docs-tool Copilot Instructions

This repository maintains parallel Chinese (`zh/`) and English (`en/`) technical documentation with identical directory structure. Every file under `zh/` has a counterpart under `en/` at the same relative path.

## Key Rules

- **Never change technical identifiers**: CPU model names (`spacemit-x60`, `spacemit-x100`, `spacemit-a100`), compiler flags (`-mcpu`, `-march`, `-fuse-ld`), toolchain binary names (`riscv64-unknown-linux-gnu-gcc`, etc.), and URLs must be reproduced verbatim in both languages.
- **Report before editing**: When reviewing, list all issues first and wait for confirmation before making any changes.
- **Frontmatter**: `sidebar_position` values must match between zh and en counterparts.
- **Headings are numbered**: e.g. `## 1. Download` / `## 1. 下载` — numbering must stay in sync.

## File Structure

```
zh/<path>  ↔  en/<path>   (always paired)
```

Current file pairs:
- `index.md`
- `studio/index.md`, `studio/intro.md`
- `user_guide/index.md`, `user_guide/cross_compiler_user_guide.md`
- `user_guide/flasher_user_guide.md`, `user_guide/jtag_debug_user_guide.md`
- `user_guide/trace_user_guide.md`

## Review Output Format

When asked to review a file pair, use this structure:

```
### zh/<file> ↔ en/<file>
**Parity**: <issues or ✅ none>
**Translation**: <issues or ✅ none>
**Markdown/Frontmatter**: <issues or ✅ none>
**Overall**: ✅ / ⚠️ / ❌
```
