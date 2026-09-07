# Operational defaults inherited from Ouroboros-old

Unless a later ADR overturns them: UTF-8 with replace; multi-select and open-folder (one window per log-like file; duplicate path focuses the existing window); Drain knobs `depth=4`, similarity `0.4`, `max_children=100`; extra delimiters empty; load soft cap with index-all / last-N / cancel; rolling window while follow mode is on; rotation keeps history, inserts a marker, continues tail, incremental Drain only; reload rebuilds index and Drain; no export/clipboard in v1; no cross-window analytics.

**Considered:** inventing new numbers or open paths before the rebuild exists.
