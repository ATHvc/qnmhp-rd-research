# DDP Experiment Matrix and Reproduction Inventory

## Distinct protocols

| Protocol | Data | Comparison | Finding |
|---|---|---|---|
| Initial S01 FCFS | S01 alarms | FCFS vs observed | MAE 1.482475 s |
| Retrospective four events | S01 subset | fixed vs RD radius | RD 0.157 vs fixed 0.369; not untouched |
| Historical frozen | S02–S09; 93 matched | fixed vs RD radius | 0.960738 vs 1.063586 s MAE |
| Early stochastic check | S02–S09 | constant p vs RD p(t) | 0.856 vs 0.886 s MAE |
| TRACK LOSO feasibility | 105 events | ridge vs mean RT | 0.9538 vs 0.9269 s MAE |
| Utility V2 all Easy | S01–S09; 105 matched; 20 seeds | fixed / constant-p / original RD / belief / combined | 0.916 / **0.827** / 0.850 / 1.036 / 1.058 s MAE |
| Utility V3 all Easy | Same 105 | V2 / hazard 1s / refractory 1.2s / slower hazard | 1.058 / 0.959 / 0.925 / 1.810 s MAE |

## Participant-wise all-Easy V2 (MAE seconds)
| Recording | Constant p | Original RD | Combined V2 |
|---|---:|---:|---:|
| S01 | 0.604 | 0.570 | 0.724 |
| S02 | 0.424 | 0.485 | 0.701 |
| S03 | 0.515 | 0.570 | 0.599 |
| S04 | 0.490 | 0.662 | 0.512 |
| S05 | 0.443 | 0.536 | 0.654 |
| S06 | 0.876 | 0.783 | 1.323 |
| S07 | 2.658 | 2.608 | 2.922 |
| S08 | 0.703 | 0.716 | 1.228 |
| S09 | 0.654 | 0.647 | 0.746 |

## Participant-wise V2 → V3 refractory (MAE seconds)
S01 0.724→0.551; S02 0.701→0.577; S03 0.599→0.572; S04 0.512→0.448; S05 0.654→0.488; S06 1.323→1.120; S07 2.922→2.763; S08 1.228→1.013; S09 0.746→0.708.

## Archived scripts and tables (local research assets; not claimed uploaded to GitHub)
- `QNMHP_RD_Complete_Research_Archive.zip` with original `source/stages`, `source/validations`, `source/portable`, frozen predictions and research report.
- `S02_S09_probabilistic_results.csv`, `S02_S09_probabilistic_event_predictions.csv`.
- `LOSO_RD_vs_constant_event_results.csv`, `LOSO_RD_vs_constant_subject_results.csv`.
- `Demand_utility_36_events.csv`, `Demand_utility_36_summary.csv`.
- `SYSMON_utility_alternatives_events.csv`, `SYSMON_utility_alternatives_summary.csv`.
- `Learned_utility_LOCO_events.csv`, `Learned_utility_LOCO_summary.csv`.
- `Stage3_probabilistic_results.csv`, `Stage3_probabilistic_event_predictions.csv`, `Stage3_constant_share_ablation_*.csv`.
- `Stage2_Utility_Design`, `Stage2_Utility_Prototype`, `Stage2_Queue_Feasibility`, `Stage2_Counterfactual_Implementation`, `Stage2_Loss_Feasibility`, `Stage2_Heldout_Statistical_Check`, `Stage3_Paper_Implementation`, `Stage4_QNMHP_RD_Integrated`.
- `QNMHP_RD_Utility_V1.zip`, `QNMHP_RD_Utility_V2_results.zip`, `QNMHP_RD_All_Unique_Easy_V2_results.zip`, `QNMHP_RD_Checking_V3_results.zip`, `QNMHP_TRACK_Audit.zip`.
- `QNMHP_DDP_Complete_Documentation_2026-11-10.zip` is the separate comprehensive Markdown appendix pack.

**Reproducibility warning:** Exact commands, code versions and raw participant datasets must be kept together for a new independent rerun. Public documentation of filenames alone is not reproduction.
