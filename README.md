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

Public LB uses ~31% of the hidden test set; final ranking uses the remaining 69%.

## Offline validation

MRR@25 on held-out structures that never appear in training. "Random" = expected MRR@25 of a random ordering of the same candidate lists (the floor a model must beat).

| ID | Date | Model | Held-out set A | Random A | Held-out set B | Random B | Status |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| E001 | 2026-10-11 | Transformer v0 (small, CPU smoke test) | 0.393 | 0.447 | 0.331 | 0.336 | Pipeline check only |
| E002 | 2026-10-11 | Transformer v1 (full data, GPU, 2.8 h) | **0.690** | 0.447 | **0.676** | 0.299 | Done |
| E003 | 2026-10-11 | Transformer v2 (full data, GPU, 2.8 h; harder held-out sets) | **0.798** | 0.447 | **0.825** | 0.178 | Done |

## Timeline

- **2026-09-14** Competition start
- **2026-10-05** First leaderboard submission (0.130)
- **2026-10-11** Transformer workstream started
- **2026-12-14** Final submission deadline → code and write-ups published here
