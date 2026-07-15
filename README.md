# RemodelQuoter

Personal remodeling estimator for the Charlotte, NC market. Single HTML file, no build step, no backend. AI drafting via OpenRouter (OAuth sign-in, any model — Claude, GPT, Grok, Gemini) or direct API keys for Anthropic / OpenAI / xAI.

## Put it on GitHub Pages (one-time, ~3 minutes)

1. Create a new repository on github.com (e.g. `remodelquoter`). Public is fine — the app contains no secrets; your quotes and keys live only in your own browser.
2. Upload `index.html` (and this README) to the repo root — the "Add file → Upload files" button works, no git required.
3. In the repo: **Settings → Pages → Source: Deploy from a branch → Branch: main / (root) → Save.**
4. Wait ~1 minute, then open `https://<your-username>.github.io/remodelquoter/`.
5. In the app: **Settings → Sign in with OpenRouter** → approve on openrouter.ai → you land back in the app, signed in. Pick a model, set web search on, and draft your first quote.

You'll need an OpenRouter account with a few dollars of credits (openrouter.ai). Web-search research costs about $0.02 per quote plus model tokens.

## Or deploy on Vercel instead

Same files, no configuration needed — the app is fully static:

- **From GitHub:** vercel.com → Add New Project → import this repo → Deploy. Done.
- **Without GitHub:** go to vercel.com/new and drag this folder onto the page.

Your app lands at `https://<project>.vercel.app`. OAuth works there too — the app builds its OpenRouter callback from whatever URL it's served on, so GitHub Pages, Vercel, or localhost all work interchangeably. (Note: if you use the app at two URLs, quotes don't sync between them — browser storage is per-site. Export/Import JSON moves them.)

## Notes

- Quotes autosave in your browser and can be exported/imported as JSON.
- The OAuth key is stored in your browser's localStorage for that site only. Use "Sign out" in Settings to remove it.
- No key at all? The Draft button loads a built-in demo quote so the app still works.
- To update the app later, just replace `index.html` in the repo; Pages redeploys automatically.
