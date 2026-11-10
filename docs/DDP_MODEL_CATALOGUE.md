# DDP Model Catalogue — Every Identified Model Family

**Scope:** reconstruction from archived stage descriptions, actual CSVs and source inventories. Model names refer to distinct hypotheses; not all were independently validated. Read with [master history](DDP_MASTER_DOCUMENTATION_2026-11-10.md), [probabilistic models](DDP_PROBABILISTIC_MODELS.md) and [experiment matrix](DDP_EXPERIMENT_MATRIX.md).

## 1. Queueing architecture (pre-RD)
- **Synthetic three-server processor / Stage 00:** demonstration of simultaneous task arrival and queue processing; no human fit claimed.
- **FCFS single-task vs dual-task / Stage 01:** modeled TRACK arrivals every 0.5 s and SYSMON processing; synthetic response time increased under dual task (~0.8 to ~1.07 s).
- **Empirical FCFS / Stage 02:** S01 warning timestamps without explicit attention gating; predicted mean 0.338509 s vs observed 1.820983 s; MAE 1.482475 s. Motivated observation delay.
- **Fixed periodic attention / Stages 03–04:** SYSMON sampled on a clock; phase and period changed apparent RT fit. Development four-event MAE reduced from 1.221683 to 0.419009, not independent confirmation.

## 2. Replicator Dynamics allocation
- **RD server dispatch / Stage 05:** choose task at cognitive queue contention using RD payoff; zero contested dispatches in test, hence RD=FCFS.
- **RD attention with constant TRACK utility / Stage 06, Experiment B:** RD influences checks rather than service priority; RD MAE 0.822114 vs fixed 0.369009 in the reported development comparison.
- **Numeric TRACK-channel utilities / Stage 07, Experiment C:** separate numeric fields tested; first-field RD 1.440917, second-field RD 0.991623 MAE; physical meaning unverified.
- **Radius RD / Stage 08, Experiment D:** U_T=0.75+0.25R, U_S=min(τ/2,2), τ since last check. Promising four-event retrospective fit RD 0.157 vs fixed 0.369; frozen 93-event S02–S09 RD 1.063586 vs fixed 0.960738.
- **RD attention opportunity diagnostics / Stage 10 and later:** check frequency, utility trajectories and event-level bias; original equation alone does not specify observation times.
- **Constant-share RD ablation:** tested whether changing RD attention adds anything beyond a fixed allocation; see archived ablation CSVs. Do not claim causal identification from this ablation alone.

## 3. Probabilistic checking and monitoring
- **Constant-p Bernoulli:** each eligible check opportunity independently checked with probability 0.25. S02–S09 MAE 0.856 vs RD 0.886; all unique Easy constant-p 0.827 vs original RD 0.850.
- **RD Bernoulli:** P(check)=x(t), x from two-task RD. Distinct from deterministic periodic and continuous hazard.
- **Warning-history / temporal urgency utility:** use history of known alarms/checks to alter modeled monitoring urgency. Requires causal information restrictions.
- **Warning-arrival hazard / renewal belief:** nonhomogeneous age-dependent belief, motivated by relatively regular warning intervals; model of unobserved warning probability, **not** direct access to future warning timestamps.
- **Hazard-based check generation / V3:** attention share mapped to a check *rate*, rather than per-opportunity probability; MAE 0.959 at nominal 1 s and 1.810 with slower 2 s variant.
- **Refractory checks / V3:** enforce 1.2 s minimum between checks; MAE 0.925 vs V2 1.058, but worse than constant-p 0.827.
- **Warning-responsive/salience hazard (original proposal):** proposed mechanism, not proven to be implemented exactly as originally specified.

## 4. Utility engineering and learning
- **SYSMON alternative utility functions:** tested several urgency transformations; archived `SYSMON_utility_alternatives_*.csv`.
- **TRACK sudden deterioration utility:** attempt to react to rapid TRACK changes, rather than static radius; archived `test_track_sudden_deterioration.py`.
- **TRACK utility V2 variants:** different TRACK demand signals; archived `test_track_utility_v2.py`.
- **Demand utility / 36 events:** task-demand comparison, archived `test_demand_utility_36.py` and `Demand_utility_36_*.csv`.
- **Learned utility difference / LOCO:** learn payoff difference from data, evaluated with cross-recording controls; archived `test_learned_utility_difference.py` and `Learned_utility_LOCO_*.csv`.
- **LOSO ridge on prewarning TRACK features:** MAE 0.9538 vs mean-RT baseline 0.9269; features did not establish a useful predictive utility.
- **Utility V1 expected avoided loss:** U_i=E[L_i|defer]-E[L_i|attend]; assumed tracking correction, belief-based warning detection and exact logit RD integration. Seven code tests, no behavioral fit.
- **Utility V2 integrated expected loss:** SYSMON-only belief MAE 1.036; combined TRACK+SYSMON 1.058; baseline constant-p 0.827 on all unique Easy.
- **Loss counterfactual prototype:** test feasibility of modeled defer-vs-attend outcomes; cannot infer genuine joystick control loss from observed open-loop X/Y.
- **Scale/identifiability checks:** multiplying utilities by c and dividing η by c yields same RD trajectory; coefficients cannot be uniquely interpreted without normalization.

## 5. Evaluation and audits
- **Frozen cross-recording S02–S09**, **LOSO RD vs constant**, **36-event tests**, **attention-gate sensitivity**, **queue feasibility**, **held-out statistical checks**, **Stage3 paper implementation**, **Stage4 integrated simulator**, **all-Easy V2/V3**, **TRACK audit**.
- **Dataset verification:** nine unique Easy recordings, 108 alarms, 105 matched, S03 has three unmatched; additional MATBeasy(10).set duplicates S01. 5,250 TRACK samples. S01–S09 labels are upload order.
- **Medium/Difficult inspection:** RESMAN and COMM appear, so two-task Easy equations are not validated multi-task models for those conditions.

## Unimplemented or unverified
A complete canonical QN-MHP; a validated human warning salience model; true gaze/check events; verified original MATLAB Update_TRACK.m; target-relative TRACK scoring; closed-loop attention-dependent joystick dynamics; fully independent untouched test participants.

**Never convert an idea, an exploratory simulation, or a software unit test into an empirical model success claim.**
