# Log lines stay on disk; the session holds a line-offset index

A log source session stores byte offsets (and compact per-slot Drain fields), not every raw body. The table seeks visible rows. This is the klogg / Ouroboros-old shape and the only way laptop-sized files stay open.

**Considered:** load all strings into a list (simple, dies on large files).
