# QN-MHP + Replicator Dynamics Research

Research archive for the integration of **Replicator Dynamics (RD)** with a **Queueing Network–Model Human Processor (QN-MHP)** architecture for human multitasking.

**Scientific status:** exploratory. Do not interpret the current results as proof that RD improves response-time prediction.

## Frozen validation snapshot (8 November 2026)

- Behavioral task: COG-BCI MATB Easy, concurrent TRACK and SYSMON.
- Archived validation: Subjects 02–09, 93 matched warning-response events.
- Pooled fixed-attention MAE: **0.960738 s**.
- Pooled RD-radius-attention MAE: **1.063586 s**.
- Proposed warning-responsive RD mechanism: **not implemented or tested**.

The historical archive reportedly contains 50 Python files across 12 development/diagnostic stages, plus nine MATB Easy file pairs. **Those original source files and raw data are not yet committed here.** Do not treat the present scaffold as a reproducible experiment.

## Navigation

- [Research status](docs/RESEARCH_STATUS.md)
- [Historical stages](docs/MODEL_HISTORY.md)
- [Reproduction checklist](docs/REPRODUCIBILITY.md)
- [Data policy](data/README.md)
- [Validation record](results/README.md)
- [Research integrity and novelty](docs/NOVELTY_AND_LIMITATIONS.md)

## Integrity rules

1. Preserve original historical scripts unchanged when importing them.
2. Record the exact dataset, parameters, event matching, and model version for each result.
3. Distinguish queueing-network models from competitive-queuing accounts of action selection.
4. Do not claim independent reproduction until the code and datasets are actually available and run.
5. Do not commit sensitive participant data without confirming redistribution rights.

## Source of this scaffold

Prepared from the pre-existing `QNMHP_RD_Research_Documentation` and `QNMHP_RD_FULL_SOURCE_CODE` records; not a replacement for the original archive.
