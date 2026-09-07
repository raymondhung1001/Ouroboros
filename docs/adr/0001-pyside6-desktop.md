# Desktop shell is PySide 6, installed with uv

The viewer is a native desktop window, not a local web app and not a klogg fork. PySide 6 is the UI toolkit; uv owns the environment. Current PySide 6 requires Python >=3.10, so the repo’s 3.8 pin must rise (3.12 recommended).

**Considered:** browser UI + Python backend (faster to sketch, wrong shape for a tailing desktop tool); fork klogg and call Drain3 out of process (two runtimes); CLI only (not a viewer).
