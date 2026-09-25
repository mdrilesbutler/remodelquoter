# NOW — remodelquoter

## STATE (as of 2026-09-25)
- Last deploy commit 2026-08-27 (`33757c7`): "deploy pages from remodelquoter-claude 652a55e...".
- This repo is the frozen public GitHub Pages host only. Canonical source is `remodelquoter-pages/` inside the private monorepo `mdrilesbutler/remodelquoter-claude`; deploy via that monorepo's `scripts/deploy-github-pages.sh`, rollback via `scripts/rollback-github-pages.sh`.
- `.pages-source.json` records provenance: `source_commit 652a55e691e18e97a02b39e36e533c3653cdf055` from `remodelquoter-claude`, `rollback_sha a50dd3962c5d33777d72471aafe70e0a390c278a`, deployed 2026-08-27T07:03:51Z.
- Public URL: https://mdrilesbutler.github.io/remodelquoter/ (title "RemodelQuoter — Charlotte NC"), last verified HTTP 200 as of the 2026-08-27 deploy checkpoint.
- Do not delete this repo — it is the only thing serving the public URL (a separate, active v2 app lives in `remodelquoter-claude` and does not touch this compatibility surface).

## NOW
Verify the deploy is still healthy and un-drifted: `curl -sI https://mdrilesbutler.github.io/remodelquoter/` should return HTTP 200, and the page title should still read "RemodelQuoter — Charlotte NC". Then confirm `remodelquoter-claude`'s `remodelquoter-pages/` HEAD still matches `.pages-source.json`'s `source_commit` (no un-deployed monorepo changes waiting). Report drift only — do not run the deploy script without Michael's yes.

## BLOCKED
none

## OWNER
none

## NEXT
- If `remodelquoter-pages/` in `remodelquoter-claude` has moved past `source_commit`, tell Michael and get his yes before running `scripts/deploy-github-pages.sh`.
- No further feature work belongs in this repo — route it to the `remodelquoter-claude` monorepo instead.
