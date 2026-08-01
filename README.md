# CeramTec client report

`main.tex` is the single report source. The external data register appendix is embedded between `% <<REGISTER_BEGIN>>` and `% <<REGISTER_END>>`.

## Guidelines for the report

The final project report should be a maximum of 3,000 words in length (not including appendices, 
references or Executive Summary). Students will summarise the analysis undertaken and provide 
concise and targeted insights and recommendations to the client.

To exclude specific sections from the word count, wrap them inside these wraps: (`%TC:ignore` and `%TC:endignore`)

'''
%TC:ignore

/section{...}
....

%TC:endignore
'''



## Refresh appendix from Google Sheet

The team master register lives on Google Drive as **External Data Register** (sheet). Pull into the repo (updates `data/external/External Data.md` and patches `main.tex`):

```bash
# WSL + One CLI (recommended)
wsl -d Ubuntu -- bash scripts/phase1/scraping/sync_external_doc_wsl.sh

# Or directly
python scripts/phase1/scraping/sync_external_data_register.py
```

Options: `--dry-run`, `--skip-tex` (markdown only), `--local-export path/to.tsv` (offline patch).

Compile locally when ready: `cd docs/report && pdflatex main.tex` (twice for TOC / longtable).

Phase~2/3 figures live in `docs/report/phase2_phase3/`; Phase~4 figures in `docs/report/phase4/`.
