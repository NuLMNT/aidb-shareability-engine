# aidb-shareability-engine
It takes episode metadata, title, guest, summary, timestamps and generates platform-native content for LinkedIn, X, Instagram, newsletter, and YouTube descriptions.
# AIDB Episode Shareability Engine

An AI-powered tool that takes episode metadata and generates platform-native shareable content for The AI Daily Brief.

Built specifically for AIDB. Not a generic podcast tool.

---

## What it does

Paste in an episode title, summary, and timestamps. Select your target platforms. The engine generates ready to post content for LinkedIn, X (thread), Instagram, newsletter, and YouTube descriptions — each in a separate Claude API call so output stays under token limits and results stream in incrementally as they complete.

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

### Option A — Claude.ai artifact (fastest)

Open the file in Claude.ai as a React artifact. No setup, no API key management. Anthropic handles auth. Works immediately.

### Option B — Replit

1. Create a new Replit using the **React (Vite)** template
2. Go to **Secrets** and add: `VITE_ANTHROPIC_API_KEY` = your Anthropic API key
3. In `index.html`, add to `<head>`:
```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@tabler/icons-webfont@latest/tabler-icons.min.css" />
```
4. Replace `src/App.jsx` with the contents of `App.jsx` in this repo
5. Click **Run**

### Option C — Local (Vite)

```bash
git clone https://github.com/[YOUR_USERNAME]/aidb-shareability-engine
cd aidb-shareability-engine
npm create vite@latest . -- --template react
npm install
```

Create a `.env` file in the project root:
```
VITE_ANTHROPIC_API_KEY=your_key_here
```

Add the Tabler Icons CDN link to `index.html`, replace `src/App.jsx`, then:
```bash
npm run dev
```

---

## Stack

- React (Vite)
- Anthropic Claude API — `claude-sonnet-4-20250514`
- Inline styles only, no CSS framework
- Tabler Icons (CDN)

---

## Notes

- Each platform generates in a separate API call. This is intentional — combining them into one call hits the output token limit and breaks JSON parsing mid-response.
- The voice brief embedded in every prompt is specific to AIDB's editorial character. Swap it out for a different show's voice brief and the engine works for any podcast.
- Show name is an editable field. The prompt enforces exact show name usage and blocks model inference from host identity (relevant: NLW is associated with The Breakdown, the prior show name).

---

Built by Jaye — [nulmnt.com](https://nulmnt.com)
