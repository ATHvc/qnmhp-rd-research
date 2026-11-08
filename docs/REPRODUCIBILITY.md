# Reproduction protocol

**Current status: NOT REPRODUCIBLE FROM THIS REPOSITORY ALONE.**

The original scripts, portable runner, raw MATB files, and environment manifests must be imported and checked before running the experiments.

## Import checklist
- [ ] Import the complete original Python source tree without modification.
- [ ] Import the original portable reproduction runner.
- [ ] Verify the provenance and permitted redistribution of each .mat/.set dataset pair.
- [ ] Store restricted datasets outside public Git history if necessary.
- [ ] Record Python version and exact dependency versions.
- [ ] Capture SHA-256 checksums of inputs and source files.
- [ ] Run original tests and save their output.
- [ ] Reproduce all 93 frozen S02–S09 event-level predictions.
- [ ] Recalculate pooled fixed-attention and RD MAE.
- [ ] Compare each prediction against archived values, recording any discrepancies.

## Acceptance targets from archived documentation
- 93 matched events for S02–S09.
- Fixed MAE 0.960738 s.
- RD-radius-attention MAE 1.063586 s.

These are **historical targets**, not results newly executed in this repository.
