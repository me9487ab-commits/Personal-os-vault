---
date: 2026-10-03
type: task
tags: [openclaw, devops]
energy: medium
time-estimate: 30min
project:
area: github-learning
source:
due: 2026-10-04
priority: high
triaged: 2026-10-03
completed:
---

# 2026-10-04 upgrade OpenClaw 2026.9.5 to 2026.9.7

## Goal
Upgrade OpenClaw from 2026.9.5 to 2026.9.7 safely.

## Steps
1. Backup: openclaw gateway() snapshot current state
2. openclaw gateway() update.run (owner explicit request only)
3. Wait for completion notice
4. Test core functions: /status, /memory, /exec
5. If refused, follow tool recovery instructions

## Risks
- Plugin compatibility break
- Config schema change
- Channel disconnect

## Done means
- openclaw status shows new version
- Core functions respond normally
- No plugin errors in log
