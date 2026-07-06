# CeramTec client report

`main.tex` is the single report source. The external data register appendix is embedded between `% <<REGISTER_BEGIN>>` and `% <<REGISTER_END>>`.

## Refresh appendix from Google Sheet

The team master register lives on Google Drive as **External Data Register** (sheet). Pull into the repo (updates `data/external/External Data.md` and patches `main.tex`):

```bash
# WSL + One CLI (recommended)
wsl -d Ubuntu -- bash scripts/scraping/sync_external_doc_wsl.sh

# Or directly
python scripts/scraping/sync_external_data_register.py
```

Options: `--dry-run`, `--skip-tex` (markdown only), `--local-export path/to.tsv` (offline patch).

Compile locally when ready: `cd docs/report && pdflatex main.tex` (twice for TOC / longtable).
