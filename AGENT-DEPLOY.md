# Agent Deploy Prompt — paste into Claude Code or Codex

Run your coding agent (Claude Code, Codex CLI, etc.) from inside this folder (the one containing `index.html`) and paste the prompt below. It handles GitHub upload, Pages activation, and optional Vercel deploy.

---

Deploy this folder as my personal static web app. It is a single-file app (`index.html`) plus docs — no build step. Do the following, showing me each command before running anything that creates or changes something on my accounts:

1. **Preflight:** verify `git` and `gh` are installed and `gh auth status` shows me logged in. If not logged in, walk me through `gh auth login` and wait.
2. **Create the repo:** initialize git here if needed, commit all files, then create a repo named `remodelquoter` under my account and push:
   `gh repo create remodelquoter --public --source=. --push`
   (Ask me first if I'd rather it be private — note that GitHub Pages on a private repo requires a paid plan, and this app contains no secrets; keys and quotes live only in my browser.)
3. **Enable GitHub Pages** from the main branch root via the API:
   `gh api repos/{owner}/remodelquoter/pages -X POST -f "source[branch]=main" -f "source[path]=/"`
   If Pages is already enabled, skip gracefully. Then poll `gh api repos/{owner}/remodelquoter/pages` until `status` is `built` (or ~2 minutes) and print the `html_url`.
4. **Verify:** fetch the published URL and confirm it returns HTTP 200 and the page title "RemodelQuoter". Print the final URL for me to open.
5. **Optional — Vercel too:** ask me if I also want a Vercel deployment. If yes: check for the `vercel` CLI (`npm i -g vercel` if missing), run `vercel login` if needed, then `vercel --prod` from this folder and print the production URL. No vercel.json is required for a static site.
6. **Hand-off summary:** print the live URL(s) and remind me: open the site → Settings tab → "Sign in with OpenRouter" → approve → pick a model → draft a quote. The OAuth callback works automatically on any https URL this app is served from.

Rules: never commit or echo any API keys; never force-push; if the repo name is taken, ask me for another name instead of guessing.
