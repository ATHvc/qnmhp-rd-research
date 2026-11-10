# DDP Research Papers — Audited Reading Register

**Updated 10 November 2026.** This register is based on the title pages of the **10 PDF files actually available in the research workspace** and the previously cited QN-MHP architecture paper. It corrects the earlier incomplete list. The original PDF binaries are **not uploaded to this public repository** because they may be copyrighted; the filenames below identify the locally held research copies.

## A. Cognitive architecture and resource competition

1. **Liu, Feyen & Tsimhoni (2006)** — *Queueing Network–Model Human Processor (QN-MHP): A Computational Architecture for Multitask Performance in Human-Machine Systems*. ACM TOCHI 13(1):37–70. **Role:** foundational queueing, perceptual/cognitive/motor processing, concurrency. **Evidence:** cited in original project archive; full PDF not among these 10 files. **Does not establish:** our chosen utility coefficients or RD attention law.
2. **Salvucci & Taatgen (2008)** — *Threaded Cognition: An Integrated Theory of Concurrent Multitasking*. Psychological Review 115(1):101–130. DOI: https://doi.org/10.1037/0033-295X.115.1.101 . **Local file:** `threaded coginition research.pdf`. **Role:** competing/related architecture with concurrent threads and serial procedural resource; helps distinguish cognitive resource contention from the separate question of how attention is allocated.
3. **Wickens (2008)** — *Multiple Resources and Mental Workload*. Human Factors. **Local file:** `wickens-2008-multiple-resources-and-mental-workload.pdf`. **Role:** interference and workload across resource dimensions; motivates not assuming TRACK and SYSMON always contend at one queue.
4. **Feyen & Liu (2001)** — *The Queuing Network Model Human Processor (QNMHP): An Engineering Approach for Modeling Cognitive Performance* (title from archived discussion; complete publication metadata not reverified). **Role:** earlier QN-MHP lineage.

## B. Human attention, probabilistic sampling, and adaptation

5. **Eisma, Hancock & de Winter** — *On Senders’s Models of Visual Sampling Behavior*. **Local file:** `10.1177_0018720820959956.pdf`. DOI: https://doi.org/10.1177/0018720820959956 . **Role:** theoretical background for intermittent/uncertain visual sampling. **Does not establish:** our exact Bernoulli check probability, 1.2 s refractory period or RD-dependent hazard.
6. **Janssen & Brumby (2010)** — *Strategic Adaptation to Performance Objectives in a Dual-Task Setting*. Cognitive Science 34:1548–1560. DOI: https://doi.org/10.1111/j.1551-6709.2010.01124.x . **Local file:** `Cognitive Science - 2010 - Janssen - Strategic Adaptation to Performance Objectives in a Dual‐Task Setting.pdf`. **Role:** task priorities, objectives and human adaptation.
7. **Farmer, Janssen, Nguyen & Brumby (2018)** — *Dividing Attention Between Tasks: Testing Whether Explicit Payoff Functions Elicit Optimal Dual-Task Performance*. Cognitive Science 42:820–849. DOI: https://doi.org/10.1111/cogs.12513 . **Local file:** `COGS-research paper.pdf`. **Role:** empirical study of payoff functions and dual-task allocation; particularly relevant to questioning whether designed RD utilities reflect human decisions.
8. **Janssen & Brumby (2015)** — *Strategic Adaptation to Task Characteristics, Incentives, and Individual Differences in Dual-Tasking*. PLOS ONE. DOI: https://doi.org/10.1371/journal.pone.0130009 . **Local file:** `pone.0130009.pdf`. **Role:** task-characteristic and incentive effects; cautions against a one-size-fits-all attention rule.
9. **Karpinsky, Chancey, Palmer & Yamani (2018)** — *Automation Trust and Attention Allocation in Multitasking Workspace*. Applied Ergonomics 70:194–201. **Local file:** `attention allocation paper.pdf`. **Role:** trust and context influence on monitoring allocation; not a validation of the DDP's RD model.

## C. Mathematical dynamics

10. **Cressman & Tao (2014)** — *The Replicator Equation and Other Game Dynamics*. PNAS. **Local files:** `pnas.201400823.pdf` and `rd 1 paper.pdf` (**duplicate title/paper**, not two independent references). **Role:** formal RD payoff-dependent change and stability concepts. **Does not establish:** cognitive attention obeys RD or a valid mapping from joystick radius to utility.

## D. Dataset and behavioral task

11. **Hinss et al. (2023)** — *Open multi-session and multi-task EEG cognitive Dataset for passive brain-computer Interface Applications*. Scientific Data 10:85. DOI: https://doi.org/10.1038/s41597-022-01898-y ; data: https://zenodo.org/records/6923638 . **Local file:** `COG-BCI_info.pdf`. **Role:** data/task documentation for MATB TRACK and SYSMON; dataset provenance, not a proof of any model.

## What was missing in the old documentation

The earlier register omitted the actual identities of the **Farmer et al. payoff paper**, **Janssen & Brumby PLOS ONE paper**, **Eisma et al. Senders sampling paper**, **Salvucci & Taatgen threaded cognition paper**, **Wickens multiple-resources paper**, and **Karpinsky et al. attention allocation paper**. These are now recorded explicitly.

## Evidence map: paper → model question

| Paper family | Research question informed | Tested DDP components |
|---|---|---|
| QN-MHP / Threaded Cognition / Wickens | How do cognitive and perceptual resources interfere? | FCFS, shared-server RD, queue-feasibility tests |
| Senders visual sampling | Why is monitoring intermittent? | periodic check gate, Bernoulli checking, hazard/refractory checks |
| Janssen / Farmer | Can attention adapt to objectives, payoffs and incentives? | TRACK/SYSMON utility variants, RD allocation, learned utilities |
| Karpinsky et al. | Does task context affect monitoring? | motivation for variable monitoring; no direct trust measurement in DDP |
| Cressman & Tao | What does RD mathematically predict? | two-task RD and stability/identifiability analysis |
| Hinss et al. | What can we measure? | warning onset/response matching and TRACK data audit |

**Integrity:** These connections are research motivations and comparisons, **not claims that the authors endorsed or validated our particular implementation**. Do not add paper-derived numerical utility coefficients without direct support. The original MATLAB `Update_TRACK.m` remains unverified.
