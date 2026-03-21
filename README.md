# mirror

Weekly engineering retrospective analyzing commit history, work patterns, and shipping velocity with persistent history and trend tracking.

## What It Does

This skill runs parallel git queries to gather commits, LOC stats, timestamps, hotspots, and PR numbers. It computes velocity metrics, detects work sessions (45-min gap threshold), classifies session depth, tracks commit type distribution, identifies hotspots, calculates focus score, and saves JSON snapshots for week-over-week trend comparison.

## Problem It Solves

Engineering teams ship without understanding their own velocity patterns. This skill answers: How much did we ship? What hours are most productive? Are we fixing fast or building well? Is test coverage improving? It provides concrete metrics anchored in commits, not feelings — enabling data-driven planning and habit formation.

## How to Use

1. **Run weekly** — default is last 7 days
2. **Optional arguments:**
   - `/mirror` — last 7 days (default)
   - `/mirror 24h` — last 24 hours
   - `/mirror 14d` — last 14 days
   - `/mirror 30d` — last 30 days
   - `/mirror compare` — compare current vs prior period
3. **Review 12 steps:**
   - Gather raw git data (parallel queries)
   - Compute metrics table
   - Commit time distribution histogram
   - Work session detection (45-min gaps)
   - Commit type breakdown (feat/fix/refactor)
   - Hotspot analysis (top 10 files)
   - Focus score + ship of the week
   - Week-over-week trends (if 14d+)
   - Streak tracking
   - Load/save history for comparison
   - Write narrative (wins, improvements, habits)
4. **Save JSON** — `.context/retros/YYYY-MM-DD-N.json` for trend tracking

**Example:**
```
/mirror
# Output:
# - Week of Mar 1: 47 commits, 3.2k LOC, 38% tests, 12 PRs
# - Peak hour: 10pm, 14 sessions detected, 5 deep sessions
# - Test ratio ↑19pp vs last week, fix ratio ↓24pp (improving)
# - Streak: 47 consecutive days
# - Top 3 wins, 3 improvements, 3 habits for next week
```

## Requirements

- OpenClaw installed
- Git repository with origin/main
- `.context/retros/` directory (auto-created)


## One-Click Install

### Option 1: GitHub Release (Recommended)
```bash
curl -L https://github.com/NovaCaliforniaLabs/mirror-skill/releases/latest/download/mirror-skill.zip -o mirror.zip
unzip mirror.zip -d ~/.openclaw/workspace/skills/
rm mirror.zip
```

### Option 2: ClawMart Download
After purchase on shopclawmart.com, download the package and extract to ~/.openclaw/workspace/skills/

## Quality Checklist
- ✅ SKILL.md complete with usage docs
- ✅ All scripts functional (bin/*.sh)
- ✅ Templates included (templates/)
- ✅ Examples provided (examples/)
- ✅ Attribution verified
- ✅ Tested on macOS Apple Silicon


## Pricing

Free — open source skill.

---

*By Nova California Labs*
