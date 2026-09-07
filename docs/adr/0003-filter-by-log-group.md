# Clicking a log group filters the table

Template ranking is no longer display-only. Selecting a log group restricts the table to that group’s log lines. Ranking counts stay on the full loaded window. Search pattern and severity preset still AND with this filter. This is the hole in Ouroboros-old (ADR-0013 there rejected a second pane; we are not adding one).

**Considered:** keep ranking as stats only (fails “see groups, then jump to those lines”); klogg dual pane (second product).
