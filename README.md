# PHAROS preprint

**Many Tools, One Ledger: Wall-Clock Supremacy for STEM PDF OCR on a Single 12 GB GPU**

Marcus Whitfill · 16 September 2026 · Fort Collins, Colorado

This repository is the public preprint for a one-day STEM-PDF lake drain on a single NVIDIA GA102 3080 Ti (12 288 MiB) plus a 12-core Zen 3 host.

## Claim, scoped

Wall-clock supremacy is versus **naive full-book MinerU 3.4.5 on this lake, this card, these books**. It is not a quality bakeoff against Marker, olmOCR, Docling, or OmniDocBench.

Kickoff IR: `3,360,474` pages, `393,232` dirty → skip `1 − 393232/3360474 = 88.30%`.

Lab operating estimate (P07): ~94 h naive full-book GPU → ~25 h dirty-only (~69 h / 2.9 days). Energy model, not a PDU: `350 W × 69 h = 24.15 kWh` avoided at nameplate TGP; `309 W × 69 h = 21.32 kWh` at the 6-worker median.

Stable topology: **6 workers + adaptive caps 48→24→16**. 10-worker CUDA-unknown and 12-worker preload OOM are documented negative results. Failures stay in the paper: `fail=1157`, `gpu_fix=640` at freeze.

## Files

| path | what |
|---|---|
| `PHAROS-preprint.tex` | manuscript |
| `PHAROS-preprint.pdf` | compiled preprint (also attached in the originating chat) |
| `fig/` | receipt-exact figures |
| `receipts_snapshot.json` | freeze 2026-09-16T17:00:40−06:00 |
| `chronicle/` | operator record P00–P10 + appendices |

```
pdflatex PHAROS-preprint.tex
```

## How to put this on arXiv

This repo has no arXiv identifier. As of 21 January 2026, first-time CS submitters need an endorser in the category. Intended primary: `cs.DC`. Secondary: `cs.IR`, `cs.CV`. Same-day DOI: mint Zenodo from this repository.

1. Download `PHAROS-preprint.pdf` + `.tex` + `fig/`.
2. [arxiv.org/submit](https://arxiv.org/submit) → cs.DC.
3. Or [zenodo.org](https://zenodo.org) → New upload → this GitHub repo.

## Throughline

No, I will not use one tool. CPU prefill + page ledger + surgical MinerU on dirty spans. GPU joules scale with dirty pages, not with books.
