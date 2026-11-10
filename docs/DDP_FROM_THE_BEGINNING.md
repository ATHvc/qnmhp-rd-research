# DDP Research From the Beginning — Source and Evidence Guide

This page addresses a previous documentation failure: a short model table cannot substitute for the full research record. Start with the actual source materials rather than the final V3 score.

## How the research progressed

**1. Scientific framing:** QN-MHP literature (Liu, Feyen & Tsimhoni; Feyen & Liu), Threaded Cognition (Salvucci & Taatgen) and Multiple Resources (Wickens) provided different accounts of resource sharing and interference. The project chose a simplified QN-MHP-inspired queue model; it did **not** implement a full cognitive architecture.

**2. Empirical task/data choice:** COG-BCI / MATB recordings. Easy has TRACK + SYSMON; Medium/Difficult include additional RESMAN/COMM. Extracted warning onsets and responses and TRACK channels. Later audit found nine unique Easy recordings, 105 matched of 108 warnings, 3 unmatched in S03; one duplicate S01 upload. There is no direct measured check-time/gaze series in the current model.

**3. Why initial FCFS failed:** queueing alone predicted response latency far too quickly (S01 MAE 1.482475 s). Introduced periodic attention checks to model delayed alarm observation, with retrospective fit improvements.

**4. Why RD scheduling failed:** applying RD only at shared-server dispatch made no difference when there were zero contested dispatches. Moved RD to the *attention/checking* mechanism.

**5. Why payoffs became central:** early constant and numeric TRACK utility variants were weak. Radius-based RD looked promising on four retrospectively inspected S01 events, then failed to beat fixed checks on the frozen S02–S09 evaluation (RD 1.063586 vs fixed 0.960738 MAE). The replicator equation by itself cannot identify scientifically meaningful utilities.

**6. Probabilistic turn:** motivated by visual sampling and strategic attention papers, compared fixed periodic, constant-p Bernoulli and RD-dependent Bernoulli checks. In the S02–S09 stochastic comparison, constant-p 0.856 vs RD-p 0.886 MAE. This is a distinct experiment from the frozen fixed-vs-RD comparison.

**7. Utility and attention studies:** warning history and hazard beliefs, SYSMON alternative urgency, TRACK sudden deterioration, TRACK demand, learned utility difference, 36-event comparisons, LOCO/LOSO checks, queue feasibility and counterfactual loss prototypes. Some approaches were only tested for software feasibility, not RT predictive accuracy. Earlier warning-rate proxy analysis used all S01 onset data and should not be treated as clean held-out evidence.

**8. Expected-loss redesign:** Utility V1 proposed avoided loss if attended vs deferred and passed seven software tests. Utility V2 integrated it; on all unique Easy, combined model MAE 1.058 vs constant-p 0.827. A SYSMON-belief-only model had MAE 1.036.

**9. Checking-policy redesign:** Utility V3 compared hazard and refractory mappings; refractory 1.2 s improved V2 to MAE 0.925 but still failed to beat constant-p 0.827. RD original rerun 0.850. S07 was a strong outlier.

**10. TRACK semantic audit and pause:** 5,250 X/Y observations but no verified original MATLAB `Update_TRACK.m` or target-relative error. Radius and expected-loss TRACK assumptions cannot be claimed as validated. Research paused with no final model locked.

## Source inventory — what exists and what does not

- The companion ZIP `QNMHP_DDP_Complete_Documentation_2026-11-10.zip` has **32 files**: original 30,189-character historical report, 187,665-character historical source-code listing, code index, dataset provenance, Stage2–Stage4 notes, Utility V1/V2/V3 reports, six chapters and aggregate result CSVs.
- Separate local PDFs: 10 research files, audited in [paper register](DDP_RESEARCH_PAPERS_AUDITED.md).
- Separate raw archive and experimental ZIPs were generated earlier; not all are in this GitHub repository.
- **Do not claim this GitHub repository is yet a complete source-code-and-data reproduction archive.** Existing documentation has the methodology and results, not all executable code and participant data.

## Navigation

- [All model families](DDP_MODEL_CATALOGUE.md)
- [Probabilistic attention models](DDP_PROBABILISTIC_MODELS.md)
- [Full experiment matrix](DDP_EXPERIMENT_MATRIX.md)
- [Audited research papers](DDP_RESEARCH_PAPERS_AUDITED.md)
- [Master research record](DDP_MASTER_DOCUMENTATION_2026-11-10.md)

## What would make it genuinely complete?

Import the full original historical source listings and stage reports as versioned text, link every experimental CSV to its producing script/seed/dataset, audit the chronology against the original conversation, and verify reuse rights before publishing raw recordings or copyrighted PDFs. Missing original source code and direct check-time data should remain marked missing, not silently reconstructed.
