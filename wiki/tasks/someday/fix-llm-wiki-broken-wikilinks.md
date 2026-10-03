---
date: 2026-10-03
type: task
tags: [llm-wiki, maintenance]
energy: high
time-estimate: 2hr+
project:
area: github-learning
source:
due:
priority: low
triaged: 2026-10-03
completed:
---

# Fix LLM-Wiki 174 broken wikilinks

## Goal
Fix all 174 broken wikilinks in LLM-Wiki vault.

## Background
- LLM-Wiki uses path-based wikilinks wiki/summaries/foo
- Convention: only use basename foo
- 174 broken wikilinks across vault

## Strategy
- Top 10-20 highest-use wikilinks first / most impact
- Write audit script to detect path-based, replace with basename
- Fix one batch, re-audit

## Steps
1. Audit script: python3 audit_wikilinks.py > list
2. Sort by reference count descending
3. Fix top 20 first
4. Re-audit
5. Repeat for remaining

## Done means
- Audit shows 0 broken wikilinks
- All path-based replaced with basename

## Note
No fixed due date - backlog task. Do when have time.
