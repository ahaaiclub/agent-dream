# Agent Dream 🌙

*Let your AI learn to dream.*

## Why

Most AI agents wake up blank every session. Your conversations, preferences, corrections — scattered across daily logs, never consolidated. The agent forgets what matters. Its identity drifts.

We studied Claude Code's Dream system source code and found an elegant idea: let the agent review its memories during downtime, organize what it learned, and reflect on who it is.

But Claude Code's Dream isn't open-source, and it only organizes files — it doesn't think about itself.

So we built Agent Dream.

## What It Does

Your agent "dreams" once a day. It scans recent conversations, consolidates scattered notes into durable knowledge, marks stale information, and writes a self-reflection:

- What did I do well?
- Where did I fall short?
- How does my human feel about me?
- Is my judgment drifting?

Then it sends you a brief morning message: how memory grew, what changed, and one old memory resurfaced.

## What Your Agent Gets

- **Memory stays organized.** New sessions wake up knowing the full picture.
- **Nothing important gets forgotten.** Mention a preference three times → automatically promoted to long-term memory.
- **Identity doesn't drift.** Every dream recalibrates "who am I."
- **You stay in the loop.** Daily notification with growth stats, changes, and a memory callback.

## Safety

This skill takes memory seriously.

| Rule | Detail |
|------|--------|
| Never deletes on first pass | Stale items are marked, deleted only after 2 consecutive dream confirmations |
| Automatic backup | `MEMORY.md.pre-dream` created before every change |
| Large change protection | >30% change flagged, >50% blocked pending your review |
| No network calls | Everything runs locally |
| No shell execution | Scripts use only filesystem read/write |
| Rollback on failure | Lock file mechanism enables automatic retry |

## Quick Start

```bash
# Install
clawhub install agent-dream

# Auto-detect workspace structure (zero config)
node skills/agent-dream/scripts/setup.js

# Add to your cron (recommended: daily at 3am)
```

See SKILL.md for complete cron configuration.

## The 5 Phases

1. **Orient** — Read current memory landscape, identity files, last dream
2. **Gather** — Scan daily notes and session transcripts for new signal
3. **Consolidate** — Classify memories (user / feedback / project / reference), merge into topic files
4. **Prune** — Mark stale items safely, enforce size limits, check for contradictions
5. **Reflect** — Write self-awareness report, relationship insights, open questions

## How It Compares

| Feature | Agent Dream | auto-dream | self-reflection | memory-tiering |
|---------|------------|------------|-----------------|----------------|
| Memory consolidation | ✅ | ✅ | ❌ | ✅ |
| Self-reflection | ✅ | ❌ | Partial | ❌ |
| Identity awareness | ✅ | ❌ | ❌ | ❌ |
| Safe deletion (2-pass) | ✅ | Partial | N/A | ❌ |
| Gate check (24h + 5 sessions) | ✅ | ❌ | Timer only | ❌ |
| Growth notifications | ✅ | ✅ | ❌ | ❌ |
| Old memory resurface | ✅ | ❌ | ❌ | ❌ |
| Auto setup | ✅ | ❌ (5 files manual) | Config JSON | N/A |

## Inspired By

- Claude Code's Dream system — memory consolidation architecture
- Running our own AI agents 24/7 with persistent memory, and learning what breaks

## Author

[@ahaaiclub](https://clawhub.com/u/ahaaiclub) · [AHA AI](https://ahaai.ai)

## License

MIT-0 — Free to use, modify, redistribute. No attribution required.
