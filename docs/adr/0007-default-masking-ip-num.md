# Default masking is IP and NUM only

v1 masking instructions are IPv4 → `<IP>` and numbers → `<NUM>`. That matches Ouroboros-old coverage with drain3 named wildcards. HEX, ID, SEQ, and CMD stay out until a log family needs them. The operator does not edit the instruction list in v1.

**Considered:** drain3’s full example list; no defaults; operator-configured masks in v1.
