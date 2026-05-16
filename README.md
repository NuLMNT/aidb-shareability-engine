# aidb-shareability-engine
It takes episode metadata, title, guest, summary, timestamps and generates platform-native content for LinkedIn, X, Instagram, newsletter, and YouTube descriptions.
# AIDB Episode Shareability Engine

An AI-powered tool that takes episode metadata and generates platform-native shareable content for The AI Daily Brief.

Built specifically for AIDB. Not a generic podcast tool.

---

## What it does

Paste in an episode title, summary, and timestamps. Select your target platforms. The engine generates ready-to-post content for LinkedIn, X (thread), Instagram, newsletter, and YouTube descriptions — each in a separate Claude API call so results stream in incrementally as they complete.

Every prompt is loaded with AIDB's editorial voice brief: analytically serious, slightly contrarian, treats headlines as evidence of larger patterns, never hysterical. The output reads like the show, not a marketing recap.

Each piece gets a shareability score (0–100) weighted across hook strength, virality potential, platform fit, and CTA clarity. A "Best Hook" is extracted separately — the single most citable sentence from the episode.

Platform outputs:
- **LinkedIn** — 130–180 words, punchy first line, ends with a question
- **X Thread** — 5 tweets, numbered, each standalone
- **Instagram** — caption with emotional arc + 6 niche hashtags
- **Newsletter blurb** — 70–90 words, FOMO-driven, clear CTA
- **YouTube description** — 180–240 words, SEO front-loaded, chapter timestamps included if provided

---

## How to run it

Open `App.jsx` in Claude.ai as a React artifact. No setup, no API key management. Works immediately.

---

## Stack

- React (Vite)
- Anthropic Claude API — `claude-sonnet-4-20250514`
- Inline styles only, no CSS framework
- Tabler Icons (CDN)

---

## Notes

- Each platform generates in a separate API call. This is intentional — combining them hits the output token limit and breaks JSON parsing mid-response.
- The voice brief is specific to AIDB's editorial character. Swap it out and the engine works for any show.
- Show name is an editable field. The prompt enforces exact show name usage and blocks model inference from host identity (NLW is associated with The Breakdown, the prior show name — this prevents bleed-through).

---

Built by Jaye — [nulmnt.com](https://nulmnt.com)

