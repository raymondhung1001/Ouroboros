# Reimplement Drain in-tree; do not import drain3

The rebuild owns a Drain engine copied from analysis of the drain3 package (tree search, masking, extra delimiters, numeric-token routing, similarity, change types), not a PyPI import. The old `DrainParser` is the other source: event IDs, per-line assignment, and rolling-window eviction. v1 does not persist the tree, does not have a match-only mode, and does not LRU-cap log groups. The UI speaks log group / inferred template / event ID — never cluster.

**Considered:** `pip install drain3` and wrap `TemplateMiner` (loses eviction and event IDs; pulls jsonpickle/persistence we do not want); keep the old parser unchanged (misses drain3’s named masking and tree knobs); call drain3 out of process; persist or LRU-cap log groups in v1.
