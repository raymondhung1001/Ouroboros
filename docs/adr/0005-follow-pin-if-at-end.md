# Follow mode pins the viewport only if already at the end

While follow mode is on, the window always tails. The table jumps to new log lines only when the operator was already at the end. If they have scrolled into history, appends must not steal the viewport.

**Considered:** tail with no pin (old app — easy to miss new lines); always pin (steals the scroll during reading).
