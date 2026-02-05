# English Learn Cards (OpenClaw skill)

A lightweight flashcard + SRS (spaced repetition) skill for **OpenClaw**, backed by **SQLite**.

- Store vocabulary cards (words / phrases / idioms)
- Review with a simple 0–3 grade scale (SM-2–like scheduling)
- Deterministic rendering via a helper CLI (`words.py`) so your chat output stays stable

This repo is intentionally **platform-agnostic**: it can be used from Slack, Discord, WhatsApp, Telegram, etc. Your channel/agent prompt decides the formatting.

See: `skill/prompt-examples/AGENT_PROMPT_TEMPLATE.md` for a ready-to-copy prompt template.

## What’s included

- `skill/SKILL.md` — skill instructions (generic; no personal info)
- `skill/scripts/words.py` — SQLite helper CLI (init/migrate/add/find/render/due/hardest/grade/stats)

## Local data (not in git)

- SQLite DB (your deck)
- Any enrichment/migration scripts you write for your own deck
- Secrets / tokens

See `.gitignore`.

## Install (OpenClaw)

Copy this skill into your OpenClaw workspace:

```bash
mkdir -p ~/clawd/skills/local
cp -a skill ~/clawd/skills/local/english-learn-cards
```

Then follow the skill instructions:

<https://github.com/RacyMind/english-learn-cards-skill/blob/main/skill/SKILL.md>

## Publishing / customization

This is meant to be a starting point:
- Adjust your agent prompt to match your communicator’s formatting.
- Keep one-off scripts in a separate local folder (don’t commit them).

## License

MIT
