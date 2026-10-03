---
date: 2026-10-03
type: task
tags: [vault/personal-os, devops]
energy: low
time-estimate: 10min
project:
area: github-learning
source: raw/captures/2026-10-03-tomorrow-push-personal-os.md
due: 2026-10-04
priority: high
triaged: 2026-10-03
completed:
---

# 2026-10-04 push Personal-OS to GitHub

## Goal
Push Personal-OS vault to GitHub as a private repo.

## Decision
- public or private -> PRIVATE. Personal data: areas, tasks, daily notes.
- vault-template is public as framework. Personal-OS holds personal data.

## Steps
1. cd /home/gary/services/shared-vault/Personal-OS
2. git remote -v. Should be empty.
3. GitHub: create new repo Personal-OS, private visibility.
4. git remote add origin git@github.com:me9487ab-commits/Personal-OS.git
5. git push -u origin main
6. Settings -> Danger Zone -> confirm private visibility.

## Done means
- git log origin/main matches local
- GitHub repo set to private
- First push successful

## Related
- vault-template public framework: https://github.com/me9487ab-commits/Personal-os-vault
