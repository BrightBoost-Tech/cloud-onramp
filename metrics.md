# Metrics & Checks

## Time-to-first-success (TTFS)
Record median times (self or testers).

- Part 1 (VM): _3m___
- Part 2 (GPU): 9m_5s___
- Part 3 (K8s Job): 3min_45s___

## Pre/Post question links
- Part 1: [pre](), [post]()
- Part 2: [pre](), [post]()
- Part 3: [pre](), [post]()

Notes:
- Count a run when the **Verify** output appears.
- Part 1: tester noted confusion about `chmod 600` step.
- Part 2: tester hit `cuda available: False` until driver installed.
- Part 3: cluster creation took longer than expected (≈90s).
