# Mirror 🪞

**Weekly engineering retro for AI agents — git commits → velocity insights → trend tracking**

[![OpenClaw Skill](https://img.shields.io/badge/OpenClaw-Skill-blue)](https://openclaw.ai)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Free on ClawMart](https://img.shields.io/badge/ClawMart-Free-success)](https://www.shopclawmart.com/listings/gstack-retro-acc478d9)

---

## What It Does

Mirror analyzes your git commits, detects work patterns, and tracks shipping velocity over time — so you actually know how your team works, not just how you *think* it works.

**Key metrics:**
- 📊 Velocity trends (7d, 14d, 30d comparisons)
- ⏰ Commit time distribution (when do you actually ship?)
- 🔥 Hotspot analysis (what files change most?)
- 🎯 Focus score (deep work vs. context switching)
- 📈 Week-over-week deltas (improving or stagnating?)

---

## Why It Matters

Most teams ship on intuition. "We've been productive lately" — but *how* productive? *What* patterns? *Which* habits?

Mirror replaces feelings with data:

| Question | Mirror Answers |
|----------|----------------|
| "How much did we ship?" | Commits, LOC, PR counts |
| "When are we most productive?" | Hour-by-hour distribution |
| "Are we fixing or building?" | feat/fix/refactor ratios |
| "Is test coverage improving?" | Test file trends |
| "What's eating our time?" | Hotspot analysis |

---

## Installation

### Option 1: ClawMart (Recommended)
```
Visit: https://www.shopclawmart.com/listings/gstack-retro-acc478d9
```

### Option 2: Manual
```bash
git clone https://github.com/NovaCaliforniaLabs/mirror-skill.git
cp -r mirror-skill ~/.openclaw/workspace/skills/mirror
```

---

## Usage

```
/mirror          # Last 7 days (default)
/mirror 24h      # Last 24 hours
/mirror 14d      # Last 14 days
/mirror 30d      # Last 30 days
/mirror compare   # Week-over-week comparison
```

---

## How It Works

1. **Gathers raw git data** — commits, timestamps, file changes, PR numbers
2. **Computes velocity metrics** — commits/day, LOC trends, session counts
3. **Detects work sessions** — 45-min gap threshold for "deep work" blocks
4. **Identifies hotspots** — top 10 most-changed files (refactor candidates?)
5. **Calculates focus score** — are you shipping or context-switching?
6. **Saves snapshots** — JSON history for trend comparison

---

## Example Output

```
📊 Velocity Report (Last 7 Days)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Commits: 47 | Files: 89 | +2,341/-891 LOC
Sessions: 12 deep work blocks (avg 2.3h)
Focus Score: 7.2/10

🔥 Top Hotspots:
  src/api/handlers.ts (23 changes)
  tests/integration/* (18 changes)

📈 Compared to Prior Week:
  Commits: +12%
  Focus: +0.8
  Refactor ratio: improving
```

---

## Philosophy

**From Garry Tan's gstack workflow.** Adapted for AI agents with persistent memory and trend tracking.

---

## Contributing

PRs welcome! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

---

## License

MIT — free for personal and commercial use.

---

**[Get it free on ClawMart →](https://www.shopclawmart.com/listings/gstack-retro-acc478d9)**
