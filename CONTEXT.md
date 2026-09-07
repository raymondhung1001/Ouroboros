# Ouroboros

A desktop application for analyzing log files. The primary workflow is opening a set of completed, static log files and surfacing structure through search, severity presets, and template inference. The operator may enable follow mode on a log source window to tail a file that is still being written. The raw log line is always preserved in full.

## Viewing

**Static log source**:
A log file that is fully written and not expected to receive new lines during analysis. Opened files are treated as static until the operator turns on follow mode.
_Avoid_: Dead file, archived log, snapshot

**Log file**:
A text file on disk that contains log output from an application or system.
_Avoid_: LogFile, source file, input file

**Log source**:
One log file loaded for analysis or tailing. Each log source has its own log source window.
_Avoid_: File handle, stream

**Hub**:
The launcher window that opens log sources and lists the current log set. It is not a log source. It stays open after the last log source window closes.
_Avoid_: Main window, workspace, project

**Log set**:
The collection of log source windows the operator has open for one investigation. There is no merged line sequence and no shared miner. The Hub lists the roster; it is not itself a log source.
_Avoid_: Batch, corpus, collection, LogSet (as one miner)

**Log source window**:
The top-level UI window dedicated to one log source: its lines, filters, tail state, analytics, and status for that file only.
_Avoid_: Tab, pane

**Log source session**:
The controller for one log source window. Discarded when the window closes.
_Avoid_: Controller, tab state

**Log line**:
A single line of text from a log file, shown and analyzed as one unit. The full raw text is always retained.
_Avoid_: Line, record, row, entry, message

**Follow mode**:
A per-window toggle for a live log source. When on, that window tails its file. The viewport stays on the newest log line only if the operator was already at the end.
_Avoid_: Follow (as a noun), live mode, stream mode

**Tail**:
Read newly appended lines from a log file on disk and add them to that log source window. Tail runs only while follow mode is on.
_Avoid_: Stream, watch, poll

**Log rotation**:
The tailed file is no longer a pure append of the previously indexed prefix (truncated, replaced, or rewritten). The window keeps prior lines, marks the break, and continues tailing.
_Avoid_: Truncate, rollover, file reset

**Reload**:
Re-read the full contents of a log source from disk, replacing what that window currently holds.
_Avoid_: Refresh, sync

## Search

**Search pattern**:
A regular expression the operator uses to find or filter log lines in the current view. An empty pattern applies no search filter.
_Avoid_: Pattern, parse template, matcher

**Severity preset**:
A built-in word-boundary filter for common log levels on the raw log line. ALL means no severity filter.
_Avoid_: Level filter, log level, parsed level

**Log-group filter**:
A restriction of the table to log lines that belong to one selected log group. Ranking counts ignore it. The operator toggles it by clicking the same ranking row again, and can clear it with a visible control while it is active.
_Avoid_: Cluster filter, template filter

**Filter composition**:
A log line is visible only if it passes every active filter (AND): severity preset, search pattern, and log-group filter.
_Avoid_: Combined filter, stacked filter

## Template inference

**Template inference**:
Discover recurring shapes across log lines using Drain, one log line at a time.
_Avoid_: Clustering, pattern mining, Drain3 (as a UI word)

**Inferred template**:
The generalized token string assigned to a log group. Catch-all wildcards are `<*>`. Named wildcards (`<IP>`, `<NUM>`) appear when a masking instruction fired.
_Avoid_: Template, pattern, cluster label

**Masking instruction**:
A regex that replaces a known variable span with a named wildcard before template inference. v1 defaults are IPv4 → `<IP>` and numbers → `<NUM>`.
_Avoid_: Preprocess rule, redaction, sanitizer

**Log group**:
The set of log lines that share the same inferred template. A group’s inferred template may become more general as new lines arrive.
_Avoid_: Cluster, bucket, event type

**Event ID**:
A stable numeric identifier for a log group for the duration of the session. It does not change when the inferred template generalizes.
_Avoid_: Cluster ID, template ID, signature ID

**Template parameter**:
A token value in a specific log line that corresponds to a wildcard position in its inferred template.
_Avoid_: Variable, capture, placeholder value

**Drain similarity**:
The token-similarity score recorded when a log line joins a log group.
_Avoid_: Confidence, match score, probability

**Template ranking**:
An ordered list of inferred templates by how many loaded log lines belong to each log group.
_Avoid_: Top clusters, frequency table

**Session analytics**:
Summary counts and rankings over all log lines currently loaded in the window, not over the search-filtered subset. Not merged across windows.
_Avoid_: Dashboard, stats, metrics panel
