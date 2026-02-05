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

## Setup

1) Copy the skill to your OpenClaw skills directory (or symlink it):

```bash
mkdir -p ~/clawd/skills/local
cp -a skill ~/clawd/skills/local/english-learn-cards
```

2) Pick a DB path.

By default, `words.py` uses a placeholder path. Set an env var to control it:

```bash
export ENGLISH_LEARN_CARDS_DB=~/clawd/memory/english-learn-cards.db
```

3) Initialize DB:

```bash
python ~/clawd/skills/local/english-learn-cards/scripts/words.py init
```

## Usage (CLI)

```bash
python .../words.py add "implement" \
  --pos verb \
  --ipa "/ˈɪmpləˌmɛnt/" \
  --meanings "to put a plan into action" \
  --examples "We implemented the change." "..." "..."

python .../words.py render "implement" --fill-audio
python .../words.py teach-me   # (your agent/prompt can implement the chat loop)
```

## Publishing / customization

This is meant to be a starting point:
- Adjust your agent prompt to match your communicator’s formatting.
- Keep one-off scripts in a separate local folder (don’t commit them).

## License

MIT
