# Codex Local Archive Adapter

This repository can optionally inventory a local Codex archive before extracting companion-portrait evidence. Generated inventory and evidence files can contain private thread titles, local paths, account context, and conversational previews. Treat them as private working artifacts.

## Safe Default

Run from a private checkout:

```powershell
python scripts\inventory_codex_archive.py --output-dir data
```

By default, the script reads from the current user's local Codex home:

```text
%USERPROFILE%\.codex
```

You can point it at another local archive with:

```powershell
python scripts\inventory_codex_archive.py --codex-home PATH\TO\.codex --output-dir data
```

## Outputs

- `data/codex-archive-map.md` - human-readable source map.
- `data/codex-archive-summary.json` - counts and log distribution.
- `data/codex-archive-thread-inventory.csv` - thread-level metadata for selecting evidence.

The `data/` and `evidence/` directories are ignored by git because they may include private details. Review generated files before sharing them anywhere.

## Evidence Policy

Before extracting evidence chunks, choose an evidence policy:

- `summaries-first`: use existing summaries before raw rollout bodies.
- `selected-threads`: extract only chosen rollout files by thread id.

Default recommendation: start with `summaries-first`, then use selected raw excerpts only where a pattern needs proof. Do not bulk-publish local archive outputs.
