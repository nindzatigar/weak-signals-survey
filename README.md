# Weak Signals Survey — Prototype (Phase 1–5)

A minimal, dependency-free prototype of the full interview script: the
opening (Phase 1), grounding (Phase 2), weak signal identification
(Phase 3), macro-scenario mapping (Phase 4), and close (Phase 5), so you can
test tone and pacing end to end before the rest gets built.

## Run it

Requires Node.js 18+ (you have v22, which is fine).

```
node server.js
```

Then open **http://localhost:3000** in your browser.

No `npm install` needed — it uses Node's built-in `fetch` and `http` modules,
zero external dependencies.

## Files

- `server.js` — tiny HTTP server. Serves the chat page and proxies messages
  to the Claude API with the interview's system prompt.
- `public/index.html` — the chat UI (vanilla HTML/JS, no framework).
- `.env` — holds your `ANTHROPIC_API_KEY` and model name. **Not meant to be
  shared or committed** (see note below).

## A note on the API key

Your key is sitting in `.env` in this folder, which lives in your iCloud-synced
workspace. That means it's now stored beyond just this one machine. For a
quick local test that's a reasonable tradeoff, but once you're done
experimenting, consider regenerating the key from
[console.anthropic.com](https://console.anthropic.com) for hygiene — especially
before this folder is shared with anyone else or pushed to a repo. `.gitignore`
already excludes `.env` from git, but it doesn't stop iCloud sync.

## Scope

This now covers all five phases of `interview-architecture-v1.md`: entry and
calibration, grounding, weak signal identification with real examples pulled
from the JournalismAI Use Cases database, macro-scenario mapping across six
possible futures, and a close that branches on how deeply the respondent
engaged. Next up: wiring real response storage instead of an in-memory chat,
and deciding on local LLM vs. Claude API for production.
