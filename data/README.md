# Data provenance and access

Raw Reddit posts and CSVs are intentionally excluded. Several source files include author names, URLs, post identifiers, and sensitive mental-health text. Public availability alone is not a redistribution permission.

The author confirmed manual review of the 78-row test input, yielding 74 rows after the notebook's preprocessing. CSV columns retain weak labels and numeric labels but do not preserve a separate human-annotation history. Second-annotator reliability is reported in the thesis and saved notebook outputs; the independent annotation file was not supplied.

Historical input filenames: `darija_train(2).csv`, `darija_val(2).csv`, and `darija_test(4).csv`. Uploaded suffixes are download/version labels, not canonical dataset version identifiers. Their hashes and aggregate audit findings are in [dataset_audit.json](../results/dataset_audit.json).

No public dataset download or approval procedure has been established. Readers should contact the repository author about whether access is permitted. Do not upload annotation exports, raw posts, or checkpoints without reviewing their disclosure and reuse conditions.
