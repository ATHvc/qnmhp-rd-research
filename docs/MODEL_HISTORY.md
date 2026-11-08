# Historical development map

This is an index of the previously documented model history, **not a claim that scripts have been uploaded**.

| Stage | Historical role |
|---|---|
| early_standalone | Three-server synthetic FCFS prototype (`qnmhp_track_sysmon.py`) |
| 01_synthetic_QNMHP_baseline | Discrete-event queueing-network simulator |
| 02_COGBCI_FCFS_baseline | Real event ingestion and FCFS baseline |
| 03_periodic_attention | Periodic attention-detection gate |
| 04_chronological_holdout | Retrospective 8/4 split |
| 05_RD_server_scheduling | RD scheduling at processing servers |
| 06_RD_attention_constant | RD attention with constant TRACK utility |
| 07_RD_attention_XY_fields | Coordinate-based TRACK utility variants |
| 08_RD_attention_radius | Radius-based utility and parameter selection |
| S02–S09 validations | Frozen subject-specific validation scripts |
| 09_diagnostic_pipeline | Error analysis without model changes |
| 10_multisubject_diagnostics | Pooled cross-subject analysis |

**Import rule:** Keep the original source tree and names unchanged, with hashes and provenance. New implementations belong in a separate directory rather than overwriting historical scripts.
