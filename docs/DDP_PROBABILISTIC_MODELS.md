# Probabilistic Attention and Checking — DDP Research

**Status:** tested stochastic checking models, exploratory; no demonstrated RD advantage.

## Why probabilistic checking was introduced
Early QN-MHP-inspired experiments assumed either immediate SYSMON detection or periodic checking. Neither assumption directly represents uncertain attention allocation. We therefore tested stochastic checks: at each allowed checking opportunity a Bernoulli draw determines whether SYSMON is inspected. If an alarm is already present, a successful check allows the warning to enter the existing processing/response queue.

## Models — distinguish carefully
| Model | Check mechanism | Empirical status |
|---|---|---|
| Fixed periodic | Deterministic check every 2 s | Tested baseline |
| Constant probabilistic | P(check)=0.25 at each eligible opportunity | Tested baseline |
| RD probabilistic | P(check at t)=x(t), RD SYSMON attention share | Tested |
| Hazard checking V3 | Converts attention into check intensity/rate, samples check events | Tested |
| Refractory checking V3 | Minimum 1.2 s between checks | Tested |
| Proposed salience-conditioned detection hazard | Probability/hazard depends on RD share and warning salience | **Proposed in historical archive; not implemented/validated as originally specified** |
| Bayesian QN-MHP | Full posterior inference over cognitive states | **Not a completed or validated model in this archive** |

RD attention is a latent allocation variable governed by
```
dx/dt = eta*x*(1-x)*(U_SYSMON - U_TRACK)
```
The original probability mapping was `P(check)=x(t)` at each opportunity. That is a modeling choice; it is not an observed empirical law.

## First probabilistic comparison (S02–S09)
| Model | MAE (s) |
|---|---:|
| Constant probability, 25% | **0.856** |
| RD probability, P(check)=x(t) | 0.886 |

A leave-one-subject-out/bootstrap comparison did not establish a reliable RD benefit; uncertainty interval included zero. These numbers use the earlier 93-event protocol, not the later all-Easy evaluation.

## Later all-unique-Easy comparison (S01–S09)
Nine unique Easy recordings, 105 matched warnings, 20 simulation seeds:
| Model | MAE (s) |
|---|---:|
| Fixed periodic | 0.916 |
| Constant probability p=0.25 | **0.827** |
| Original RD probability | 0.850 |
| New expected-loss utility V2, original check policy | 1.058 |
| V3 hazard-based checks | 0.959 |
| V3 refractory 1.2 s | 0.925 |
| V3 slower hazard | 1.810 |

**Do not pool the two protocols** or treat changes in numbers as evidence of improvement by themselves. The V3 refractory policy improves on V2 but still underperforms the simple constant-p baseline.

## What this means
The probabilistic model is a central **tested baseline**, not a side note. Its success relative to several RD policies is a major negative/diagnostic result: variable attention allocation does not yet justify its additional complexity. It does **not** prove that RD is inherently unsuitable. The stochastic observation mechanism, utility identification and unverified TRACK loss remain limitations.

## Reproducibility
Archive packages from the research conversation: `QNMHP_RD_Utility_V2_results.zip`, `QNMHP_RD_All_Unique_Easy_V2_results.zip`, `QNMHP_RD_Checking_V3_results.zip`. The earlier historical archive `QNMHP_RD_Complete_Research_Archive.zip` predates these later experiments. The public repo does not contain raw participant recordings.

See [master documentation](DDP_MASTER_DOCUMENTATION_2026-11-10.md).
