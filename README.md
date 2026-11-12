# Enveda CASMI 2026 — Results

Results log for my entry in the Kaggle competition
[Enveda CASMI 2026 – Molecule ID From Mass Spectra](https://www.kaggle.com/competitions/enveda-CASMI26-molecule-id-mass-spectra):
predict 2D chemical structures (SMILES) from LC-MS/MS spectra, scored by MRR@25.

**Results only.** Code, models and method write-ups stay private until the competition ends
(final submission deadline: 2026-12-14). They'll be published after that.

## Leaderboard

| Date | Submission | Public LB (MRR@25) |
| :--- | :--- | :--- |
| 2026-10-05 | Pipeline v1 | 0.130 |
| 2026-10-11 | Transformer v1 | 0.199 |
| 2026-10-11 | Transformer v2 | 0.221 |
| 2026-10-11 | Transformer v3 | 0.239 |
| 2026-10-12 | Transformer v4 | 0.267 |
| 2026-10-13 | Transformer v5 (ensemble) | 0.279 |
| 2026-10-13 | Transformer v6 (larger ensemble) | 0.278 |
| 2026-10-17 | System v2 #1 | 0.242 |
| 2026-10-18 | System v2 #2 | 0.280 |
| 2026-10-19 | System v2 #3 | 0.254 |
| 2026-10-20 | System v2 #4 | 0.285 |
| 2026-10-20 | System v2 #5 | 0.268 |
| 2026-10-21 | System v2 #6 | 0.284 |
| 2026-10-21 | System v2 #7 | 0.316 |
| 2026-10-21 | System v2 #8 | **0.329** |
| 2026-10-21 | System v2 #9 | 0.308 |
| 2026-10-21 | System v2 #10 | 0.324 |
| 2026-10-22 | System v2 #11 | 0.237 |
| 2026-10-30 | System v2 #12 (retrained models) | **0.330** |
| 2026-10-31 | System v2 #13 (diagnostic probe) | 0.307 |
| 2026-10-31 | System v2 #14 | 0.335 |
| 2026-11-01 | Public baseline reproduction (track B, #1) | 0.478 |
| 2026-11-01 | Public baseline + rerank layer (track B, #2) | 0.476 |
| 2026-11-02 | Public baseline + joint cross-encoder layer (track B, #3) | 0.470 |
| 2026-11-09 | Public baseline, compliance check C4a (own ranker) | 0.431 |
| 2026-11-09 | Public baseline, compliance check C4b (own ranker + own fingerprint model) | 0.429 |
| 2026-11-10 | Public baseline, compliance check C4c (own ranker v2 + own fingerprint model) | 0.415 |
| 2026-11-10 | Public baseline, compliance check C4d (own fingerprint model only) | 0.448 |
| 2026-11-10 | Public baseline + wider structure generation (C8) | 0.459 |
| 2026-11-11 | Public SOTA notebook, verbatim fork (S001) | 0.487 |
| 2026-11-11 | Public SOTA pipeline, two components removed (G0) | 0.445 |
| 2026-11-11 | Public SOTA pipeline, main engine replaced by own models (G1) | 0.417 |
| 2026-11-11 | Public SOTA pipeline, own main engine + open fold-safe fingerprint models (G2) | 0.415 |
| 2026-11-11 | Public SOTA pipeline, all non-reproducible models removed (G3) | 0.409 |
| 2026-11-12 | Compliant pipeline + external-library rank-2 rule (G4) | 0.407 |
| 2026-11-12 | Public SOTA pipeline, G3 without the second candidate engine (G5) | 0.353 |
| 2026-11-12 | Compliant pipeline, second engine rebuilt from own training rows (G6) | 0.369 |
| 2026-11-12 | Compliant pipeline + own external spectral libraries (G7) | 0.373 |
| 2026-11-12 | Compliant pipeline + re-tuned PubChem merge thresholds (G8) | 0.373 |

Public LB uses ~31% of the hidden test set; final ranking uses the remaining 69%.

Two parallel tracks since 2026-11-02: System v2 (own original pipeline, kept reproducible) and a public-baseline track (being audited and rebuilt for eligibility — see note below). Final submission choice is not locked.

## Offline validation

MRR@25 on held-out structures that never appear in training. "Random" = expected MRR@25 of a random ordering of the same candidate lists (the floor a model must beat).

| ID | Date | Model | Held-out set A | Random A | Held-out set B | Random B | Status |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| E001 | 2026-10-11 | Transformer v0 (small, CPU smoke test) | 0.393 | 0.447 | 0.331 | 0.336 | Pipeline check only |
| E002 | 2026-10-11 | Transformer v1 (full data, GPU, 2.8 h) | **0.690** | 0.447 | **0.676** | 0.299 | Done |
| E003 | 2026-10-11 | Transformer v2 (full data, GPU, 2.8 h; harder held-out sets) | **0.798** | 0.447 | **0.825** | 0.178 | Done |
| E006 | 2026-10-29 | Transformer v2, longer training (+4 epochs) | **0.816** | 0.447 | **0.848** | 0.178 | Done |

## Timeline

- **2026-09-14** Competition start
- **2026-10-05** First leaderboard submission (0.130)
- **2026-10-11** Transformer workstream started
- **2026-10-17** Own end-to-end system (v2): first submission
- **2026-10-30** Best public LB, own system: 0.330 (later 0.335 on 2026-10-31)
- **2026-11-01** Started a second track: reproducing and auditing a strong public baseline pipeline for competition-eligibility compliance (host requires original training code for every model weight used)
- **2026-12-14** Final submission deadline → code and write-ups published here
