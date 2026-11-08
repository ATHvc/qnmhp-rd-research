# Research status — 2026-11-08

## Objective
Investigate whether replicator-dynamics-based allocation of attention and shared processing resources in a QN-MHP-inspired model predicts human multitasking warning-response times.

## Established archived results
- Dataset: COG-BCI MATB Easy, TRACK and SYSMON.
- Historical data: nine uploaded MATB Easy file pairs.
- Frozen comparison: S02–S09, 93 matched responses.
- Fixed-attention pooled MAE: 0.960738 s.
- RD-radius-attention pooled MAE: 1.063586 s.
- The downstream QN-MHP processing is the same between these two frozen variants; the difference arises from attention-check scheduling.

## Interpretation
The tested RD-attention variant did **not** outperform the fixed-attention comparator on pooled MAE. This is a result about this implementation, not a general rejection of replicator dynamics.

## Not yet established in this repository
- Source and dataset files have not been imported.
- No validation has been rerun from this repository.
- Warning-responsive RD has not been implemented or tested.
- No novelty claim has been independently verified here.
