# NaiMed — Mama Scout MVP

> SMS-based Maternal Health AI Assistant for rural Kenya  
> Built on the Four-Terrain Capstone Framework (AIM · 4D · ETHOS/TRACK/OASIS · RANK/TRAIL)

## Live Demo

Deploy instantly — no build step required. It is a single `index.html` file.

## Quick Deploy Options

### Option A — GitHub Pages (Recommended, Free)

1. Create a new GitHub repository (e.g. `naimed-mvp`)
2. Upload `index.html` to the repository root
3. Go to **Settings → Pages → Source → Deploy from branch → main → / (root)**
4. Your app is live at `https://YOUR-USERNAME.github.io/naimed-mvp/`

### Option B — Netlify Drop (Fastest, Free)

1. Go to https://app.netlify.com/drop
2. Drag and drop `index.html` onto the page
3. Live URL generated in seconds (e.g. `https://random-name.netlify.app`)

### Option C — Vercel (Free)

1. Install Vercel CLI: `npm i -g vercel`
2. In the folder containing `index.html`, run: `vercel`
3. Follow the prompts — live in ~30 seconds

### Option D — Surge.sh (CLI, Free)

```bash
npm install -g surge
surge index.html naimed-mvp.surge.sh
```

## What This MVP Demonstrates

| Feature                                    | Framework               | Status |
| ------------------------------------------ | ----------------------- | ------ |
| CHW onboarding & sign-in                   | —                       | ✅     |
| Dashboard with KPIs                        | —                       | ✅     |
| Enrolled mothers table                     | —                       | ✅     |
| Risk alert panel                           | GUARD                   | ✅     |
| ANC visit progress bars                    | —                       | ✅     |
| Mama Scout AI chat (Swahili)               | AIM + MAP               | ✅     |
| Local dietary advice (ugali, sagaa, omena) | AIM                     | ✅     |
| Symptom escalation trigger                 | HUNT                    | ✅     |
| Guardian CHW Bridge dispatch               | RANK + TRAIL            | ✅     |
| ANC tracker with visit dots                | —                       | ✅     |
| Ethics & Compliance dashboard              | ETHOS/TRACK/OASIS/PRIDE | ✅     |
| Kenya DPA 2019 compliance status           | OASIS                   | ✅     |
| TRAIL audit logging (simulated)            | TRAIL                   | ✅     |
| M-Pesa Linda Mama guidance                 | MAP                     | ✅     |

## Architecture Notes

- **Single file** — no dependencies, no build tools, no server required
- **Zero external APIs** — all AI responses are client-side (for MVP demo)
- **Font** — Sora + Noto Sans via Google Fonts CDN
- **Mobile-responsive** — works on phones (important for CHW field use)
- **Production path** — replace the `getMamaScoutResponse()` function with a real Anthropic API call

## Extending to Production

```javascript
// Replace getMamaScoutResponse() with:
async function getMamaScoutResponse(text) {
  const response = await fetch("https://api.anthropic.com/v1/messages", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({
      model: "claude-sonnet-4-20250514",
      max_tokens: 500,
      system: `You are Mama Scout, a Kenya-trained maternal health assistant...
               [Insert full AIM prompt from NaiMed Strategic Blueprint]`,
      messages: [{ role: "user", content: text }],
    }),
  });
  const data = await response.json();
  return data.content[0].text;
}
```

## Regulatory Anchors

- Kenya Data Protection Act 2019
- Kenya MoH ANC Guidelines 2022
- KMPDC (Kenya Medical Practitioners & Dentists Council) oversight
- AWS af-south-1 (Cape Town) data residency
- Safaricom TLS 1.3 encryption

## License

MIT — Built for the NaiMed Capstone Project
