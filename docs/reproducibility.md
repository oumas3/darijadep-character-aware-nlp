# Reproducibility audit

Audit date: 2026-10-03. Review covered both supplied notebooks, five figures, the thesis report, and supplied dataset versions. GPU training was not rerun.

## Historical source

`vrdarhbrt.ipynb` is the main source: it contains M0/M1/M2, AraBERT, bootstrap analysis, gate analysis, and saved outputs matching the thesis. `chardarija.ipynb` is an earlier working version and is not packaged as the final experiment.

The packaged notebook preserves experimental code, removes all saved outputs and execution counts (including raw-post previews), removes execution metadata, and omits one Kaggle session keep-alive utility cell. It has not been reorganized or relabeled as a clean runnable pipeline.

## Checks completed

- Every code cell in the main source passes Python syntax parsing. This does not prove runtime correctness.
- Reapplied the notebook's preprocessing to the supplied CSVs and confirmed train/validation class counts and the 74-post test counts.
- Checked exact processed-text duplicates and overlap.
- Confirmed saved seed-42 test outputs and bootstrap intervals match report tables.
- Confirmed gate-plot values match the seed-1 validation analysis.
- Confirmed final checkpoint prediction helper explicitly activates character branches after loading.

## Outstanding issues

1. `CoralLayer` is used alongside `corn_loss` and `corn_label_from_logits`, while the report names CORAL. Resolve the scientific description before replacing either code or labels.
2. Several classes, optimizers, and training engines are redefined. Earlier saved output counts do not establish a clean sequential runtime state. One M2 retraining output differs from the later all-in-one comparison; use the final comparison when citing the packaged headline table.
3. One initial M2 class uses `_set_extension_grad`; a later version uses `_set_char_grad`. Preserve the model/training-engine pair for each historical run.
4. The final optimizer assigns CharCNN parameters to a 5e-5 group, while earlier configuration describes 4e-5. Do not assume every run used the configuration printed at the top.
5. Vocabulary construction includes validation/test text. A train-only revision requires new metrics.
6. Five distinct processed texts occur across training and validation; training has 14 duplicate text rows. Report the historical limitation and use a new version for repaired splits.
7. Test CSV labels match its `weak_label` column, with no separate human label field. Manual review is author-confirmed, not independently reconstructable from the CSV.
8. The notebook mixes earlier test evaluations, exploratory relabeling, parameter-width ablations, recovery, and final comparisons. Do not imply the test was never inspected during development without further evidence.
9. Checkpoints, original per-example predictions, and full M0/M1 three-seed result exports were not supplied. Saved text outputs support historical claims but do not replace those artifacts.

## Safe reproduction boundary

Do not add a passing CI badge, claim a successful `Run all`, or replace the reported metrics with new results without recording changed configurations, split hashes, and method definitions. A future clean implementation belongs on a separate branch with historical results preserved.
