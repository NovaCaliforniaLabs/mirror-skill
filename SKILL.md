---
name: mirror
description: Weekly engineering retrospective. Reflect on what happened. Analyzes commit history, work patterns, and shipping velocity with persistent history and trend tracking.
price: 0
version: 1.0.0
---

# Weekly Engineering Retro

## When to Use

Use this skill when:
- You want to understand what you shipped this week
- You need velocity metrics for planning
- You want to track trends over time
- You're doing a weekly review

**Do NOT use for:**
- Code review (use `adversarial-verify`)
- Shipping (use `gstack-ship`)
- Planning (use `gstack-ceo` or `gstack-eng`)

## Arguments

- `/retro` — last 7 days (default)
- `/retro 24h` — last 24 hours
- `/retro 14d` — last 14 days
- `/retro 30d` — last 30 days
- `/retro compare` — compare current vs prior period

## Step 1: Gather Raw Data

Fetch origin, then run ALL git commands in parallel:

```bash
# 1. Commits with timestamps and stats
git log origin/main --since="<window>" --format="%H|%ai|%s" --shortstat

# 2. Test vs production LOC breakdown
git log origin/main --since="<window>" --format="COMMIT:%H" --numstat

# 3. Timestamps for session detection
TZ=America/Los_Angeles git log origin/main --since="<window>" --format="%at|%ai|%s" | sort -n

# 4. Hotspot analysis
git log origin/main --since="<window>" --format="" --name-only | grep -v '^$' | sort | uniq -c | sort -rn

# 5. PR numbers from commit messages
git log origin/main --since="<window>" --format="%s" | grep -oE '#[0-9]+' | sed 's/^#//' | sort -n | uniq | sed 's/^/#/'
```

## Step 2: Compute Metrics

From raw data, calculate:

| Metric | Formula |
|--------|---------|
| **Commits** | Count of commits in window |
| **Files changed** | Sum of files per commit |
| **LOC added** | Sum of insertions |
| **LOC deleted** | Sum of deletions |
| **Net LOC** | Added - Deleted |
| **Test ratio** | Test LOC / Production LOC |
| **Hotspots** | Files changed > 3 times |
| **Sessions** | Clusters of commits < 2h apart |
| **Streaks** | Consecutive days with commits |

## Step 3: Detect Patterns

**Session Detection:**
- Group commits < 2 hours apart into "sessions"
- Calculate average session length
- Identify longest/shortest sessions

**Hotspot Analysis:**
- Files changed > 3x = hotspot
- Hotspots indicate refactoring targets

**Streak Tracking:**
- Consecutive days with commits
- Compare to prior streaks

## Step 4: Trend Comparison

If `compare` flag:

| Metric | Current | Prior | Change |
|--------|---------|-------|--------|
| Commits | X | Y | +Z% |
| LOC added | X | Y | +Z% |
| Test ratio | X% | Y% | +Z |
| Sessions | X | Y | +Z |

## Step 5: Generate Summary

```
+====================================================================+
|            WEEKLY RETRO — [DATE RANGE]                               |
+====================================================================+
| Commits              | [X]                                          |
| Files changed        | [X]                                          |
| LOC added            | [+X]                                         |
| LOC deleted          | [-X]                                         |
| Net LOC              | [X]                                          |
| Test ratio           | [X%]                                         |
| Sessions             | [X] (avg [Y]h)                              |
| Hotspots             | [X files changed >3x]                       |
| Streak               | [X days]                                    |
+====================================================================+
| TREND vs last week:   | [+/-Z%]                                      |
+====================================================================+

TOP FILES BY CHANGES:
1. [file] — [X] changes
2. [file] — [X] changes
3. [file] — [X] changes

SESSION BREAKDOWN:
- [Day]: [X] commits ([topics])
- [Day]: [X] commits ([topics])

RECOMMENDATIONS:
- [Refactor hotspot: X]
- [Increase test ratio: Y% → Z%]
- [Continue streak: X days]
```

## Step 6: Save to History

Append metrics to `.retro/history.json`:

```json
{
  "date": "2026-03-19",
  "commits": 12,
  "loc_added": 847,
  "loc_deleted": 234,
  "test_ratio": 0.32,
  "sessions": 5,
  "streak": 7
}
```

## Trend Visualization

After 4+ weeks, show trend:

```
COMMITS PER WEEK
Week 1: ████ 4
Week 2: ██████ 6
Week 3: ████████ 8
Week 4: ████████████ 12

TEST RATIO
Week 1: 20%
Week 2: 25%
Week 3: 28%
Week 4: 32%
```

## Attribution

Inspired by Garry Tan's gstack methodology for startup workflow optimization.
