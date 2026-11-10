# DDP Research Documentation — QN-MHP + Replicator Dynamics

Snapshot: 10 November 2026. Status: exploratory, paused; final model not locked.

## Objective
Investigate whether Replicator Dynamics (RD) can allocate attention between continuous TRACK and intermittent SYSMON within a QN-MHP-inspired queueing architecture. COG-BCI/MATB is the empirical validation dataset, not the theoretical contribution. The implementation is simplified and does not reproduce every canonical QN-MHP server.

## Complete version ledger

| Version | Intervention | Result / status |
|---|---|---|
| Historical Stage 00 | Synthetic three-server multitasking | First queueing prototype |
| Stage 01 | FCFS synthetic dual-task | SYSMON-only ~0.8 s vs dual-task ~1.07 s |
| Stage 02 | S01 warning-only FCFS | Observed mean RT 1.820983 s; predicted 0.338509 s; MAE 1.482475 s |
| Stage 03 | Periodic attention gate | Improved retrospective fit |
| Stage 04 | Period 2.0 s, phase 0.9 s | Four-event MAE 1.221683 to 0.419009; not untouched |
| Stage 05 | RD cognitive-server dispatch | Zero contested dispatches; RD identical to FCFS; MAE 0.550417 s |
| Stage 06 / Experiment B | RD attention with constant TRACK utility | RD 0.822114 vs fixed 0.369009 s MAE |
| Stage 07 / Experiment C | TRACK numeric-field modulation | First field 1.440917; second 0.991623 s RD MAE |
| Stage 08 / Experiment D | TRACK radius RD attention | Retrospective S01 last four RD 0.157 vs fixed 0.369 s; not independent |
| Stage 09 | Frozen S02–S09 test | 93 matched; fixed 0.960738 vs RD 1.063586 s MAE |
| Stage 10 | Cross-recording diagnostics | Frozen 93 event predictions reproduced exactly |
| Later Stage 1 | Raw variable and file audits | 9 unique Easy recordings, 108 warnings, 105 matched; 3 unmatched S03 |
| Later Stage 2 | Utility redesign, hazard, queue and loss feasibility | Warning timing not homogeneous Poisson-like; LOSO TRACK ridge 0.9538 vs mean baseline 0.9269 s MAE |
| Later Stage 3–4 | RD/constant-p, checking and integrated-model ablations | No robust superiority over simple checks |
| Utility V1 | Expected avoided-loss TRACK/SYSMON and exact RD update | 7 software tests; no behavioral validation |
| Utility V2 | Integrated expected-loss utilities | Nine Easy: combined MAE 1.058 vs constant-p 0.827 |
| Utility V3 | Hazard and refractory checking | 1.2 s refractory MAE 0.925, better than V2 but worse than constant-p |
| TRACK audit | Inspect X/Y records | 5,250 observations; target-relative error and MATLAB scoring unverified |

The historical Stage labels and later Stage 1–4 labels are overlapping but distinct naming systems. Other tested alternatives include warning-history utility, SYSMON alternatives, TRACK sudden deterioration, demand utility, learned utility difference, attention-gate sensitivity, queue feasibility, counterfactual prototype, constant-share ablations and held-out statistical checks. Some early warning-rate proxy results used all S01 onsets and leaked the intended development split; not confirmatory.

## Main comparable all-Easy experiment (20 seeds; 105 matched events)

| Model | MAE (s) | RMSE (s) |
|---|---:|---:|
| Fixed checks 2 s | 0.916 | 1.725 |
| Constant probability p=0.25 | **0.827** | 1.679 |
| Original RD rerun | 0.850 | **1.651** |
| SYSMON belief only | 1.036 | 1.866 |
| Combined Utility V2 | 1.058 | 1.882 |
| V3 hazard 1 s | 0.959 | 1.728 |
| V3 hazard 2 s | 1.810 | 2.343 |
| V3 refractory 1.2 s | 0.925 | 1.782 |

V3 refractory improves combined V2 on all nine recordings but does not beat constant-p. Different protocol from the historical frozen 93-event experiment: do not interpret the different historical and later numbers as a controlled one-variable comparison.

## Model and limitations

Two-task RD: dx/dt = η x(1−x)(U_SYSMON−U_TRACK), x = modeled SYSMON share. Original Experiment D: U_TRACK=0.75+0.25 R(t), U_SYSMON=min(τ/2,2) with τ time since last check. R(t) is an **unvalidated coordinate proxy**, not verified tracking error. New utilities propose expected loss avoided by attending, with assumed TRACK control dynamics and a warning-belief model. The RD share must be mapped to discrete checking. Simulated checks, attention shares, counterfactual TRACK control, and actual human gaze are not observed. Current replay is open-loop. Scale of utilities and inverse η are non-identifiable without normalization.

The new MATBeasy(10).set duplicates archived S01 byte-for-byte. S01–S09 are upload-order labels, not independently verified distinct participants. All nine Easy recordings have already been inspected and are not untouched final holdout data. Medium/Difficult include RESMAN/COMM and need an extended multi-task simulator. The original Update_TRACK.m and target-relative scoring are not verified.

## Resources

- Liu, Feyen & Tsimhoni (2006), Queueing Network–Model Human Processor, ACM TOCHI 13(1):37–70.
- Feyen & Liu (2001), Feyen (2002): earlier QN-MHP work; bibliographic details to verify.
- Cressman & Tao (2014), The Replicator Equation and Other Game Dynamics, PNAS.
- Hinss et al. (2023), COG-BCI Scientific Data 10:85: https://doi.org/10.1038/s41597-022-01898-y ; dataset https://zenodo.org/records/6923638 .
- Janssen (2010), Strategic Adaptation to Performance Objectives in a Dual-Task Setting, Cognitive Science (supplied PDF).
- Supplied PDFs: threaded coginition research.pdf; COGS-research paper.pdf; 10.1177_0018720820959956.pdf; COG-BCI_info.pdf. Full bibliographic details of filename-only PDFs not independently verified.
- OpenMATB https://github.com/juliencegarra/OpenMATB is a different Python implementation, not a verified source of original MATLAB Update_TRACK.m.

## Reproduction and source inventory

Original complete archive: QNMHP_RD_Complete_Research_Archive.zip, containing source/stages, source/validations, source/portable, nine raw Easy file pairs, full historical Markdown report, full source-code listing, source manifest and saved event predictions. Extract it and run:

    python -m pip install -r requirements.txt
    python source/portable/run_frozen_validation.py
    python -m unittest discover -s source/portable -p 'test_*.py' -v

Additional experimental packages: QNMHP_RD_Utility_V1.zip, QNMHP_RD_Utility_V2_results.zip, QNMHP_RD_All_Unique_Easy_V2_results.zip, QNMHP_RD_Checking_V3_results.zip, QNMHP_TRACK_Audit.zip and Stage1–Stage4 experiment ZIPs. A new 32-file companion documentation package contains the complete historical report, full source listing, later stage notes, aggregate CSVs and expanded six-chapter documentation. The companion package is distributed separately from this public repository; no raw participant recordings or third-party PDFs were committed.

## Final decision

Keep original RD as reference and constant-p as best pooled-MAE baseline; retain V3 refractory as candidate only. Do not lock Utility V2/V3 or retune coefficients on already-inspected recordings. First verify TRACK scoring and attention-dependent tracking performance, then use new untouched sessions and evaluate TRACK and SYSMON jointly.
