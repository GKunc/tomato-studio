# Landing page template

Static landing pages (plain HTML, CSS, JS) built and maintained with Claude Code, optimized for Google and AI assistants (ChatGPT, Perplexity, Claude, AI Overviews), hosted on GitHub Pages. One repo per page.

## Make a new page
1. Fill in `brief/landing.md` (business facts, FAQ, repo name) and `site.config.json` (brand, colour, title, headline, CTA, form endpoint; cheat sheet at the end of the brief).
2. Open this repo in Claude Code and say: **"set up the landing"**.

Claude creates the page repo from this template, switches on hosting, fills the page, generates the social image and icons, runs every check, deploys, sets up Search Console and analytics, and gives you the live URL. You only provide business facts and, when asked, sign in to GitHub (`gh auth login`) and add DNS records for a custom domain. Google set-up is automatic after a one-time service account set-up (publish skill).

## Day to day
- new computer / "the preview doesn't work" → `dev-setup` skill (installs tools, git hooks, live-reload preview)
- "write a blog post about …" → `blog-post` skill
- "check SEO" / "why don't we show up in ChatGPT?" → `seo` skill
- "is the site OK?" → `audit` skill (the live site is also checked every Monday; problems open a GitHub issue)
- "undo the last change" → `undo` skill
- "hand the site over to the client" → `handoff` skill
- "update all client sites" (in the template repo) → `maintenance` skill
- "put it on example.com" → `publish` skill

## What's inside
| Path | Purpose |
| --- | --- |
| `site.config.json` | Every shared value (brand, URL, title, CTA, form endpoint…); pages use them as `{{KEY}}` |
| `src/` | Page sources: home, blog, privacy, 404, robots.txt, llms.txt, RSS feed, manifest, icons |
| `src/_partials/` | Head, header and footer shared by every page |
| `brief/landing.md` | Business facts; Claude never invents beyond it |
| `tools/build.mjs` | Builds `_site/`: fills values, includes partials, generates the sitemap, blog index, feed and llms.txt entries |
| `tools/serve.mjs` | Local preview with live reload (the `site` preview) |
| `tools/verify.mjs` | The command that gates every deploy, locally and in CI (`--quick` offline; `--lighthouse` adds Lighthouse on the pages changed since `origin/main`, `--lighthouse --all` on every page) |
| `tools/hook.mjs` | Claude Code hooks: rebuild after each edit, verify before Claude finishes |
| `tools/selftest.mjs` | Tests the template itself on a fixture site (`tools/fixture/`) |
| `tools/google.mjs` | Search Console (verify, owners, sitemap) and GA4 (property + stream) through Google's APIs |
| `emails/` | Autoreply and notification emails (HTML + text), shared layout, `STYLE.md` style guide; preview at `/__emails/` |
| `worker/form.js` | Contact form backend (Cloudflare Worker + Resend): notification to the business, autoreply to the visitor, Turnstile anti-bot |
| `tools/form-worker.mjs` | Builds the worker with the email templates, deploys it, sets its secrets |
| `tools/test-worker.mjs` | Tests the worker locally against fake email/anti-bot services |
| `tools/form-test.mjs` | Sends a real test enquiry (`--send`): notification + autoreply |
| `tools/monitor.mjs` | Checks the live site; weekly in CI (`.github/workflows/monitor.yml`), problems open a GitHub issue |
| `tools/history.mjs` | Site changes in plain words; `undo <n>` reverses one |
| `template.json`, `tools/template-update.mjs` | Which files belong to the template; brings a site up to date with it (`.template-version`) |
| `tools/fleet.mjs` | From the template repo: status of every client site, roll template updates out |
| `GUIDE.md` | Short guide for the client, translated at handoff |
| `src/js/consent.js` | GA4 behind a cookie banner (Consent Mode v2; nothing loads before "Accept") |
| `tools/doctor.mjs` | Checks this computer is ready to develop; `--fix` sets up hooks and the preview |
| `.githooks/` | pre-commit: release checks; pre-push: `verify.mjs --quick` |
| `tools/check.mjs` | Release checks (missing values, filler copy, meta, unique titles, JSON-LD, FAQ schema, blog posts) |
| `tools/make-assets.mjs` | Generates `og.png` and app icons from the brand (needs local Chrome) |
| `tools/indexnow.mjs` | Notifies Bing/IndexNow of changed URLs after each deploy |
| `.github/workflows/pages.yml` | On PRs and pushes to `main`: `verify.mjs --lighthouse`, where Lighthouse checks only the pages whose built output changed since the last successful deploy (more than 5 → 5 random ones; none → skipped; `lighthouserc.json` changed, first deploy or Run workflow by hand → every page). On `main` then → deploy → smoke test → IndexNow. In the template repo: `selftest.mjs` |
| `.github/dependabot.yml` | Keeps the workflow's actions up to date |
| `lighthouserc.json` | Lighthouse budgets: performance ≥ 0.9; accessibility, best practices, SEO ≥ 0.95; CLS ≤ 0.1 |
| `.claude/skills/` | dev-setup, new-landing, publish, domain-knowledge, seo, blog-post, emails, audit, undo, handoff, maintenance, webmcp |
| `.claude/launch.json` | Local preview server (`node tools/serve.mjs 4321`, live reload) |
| `.mcp.json` | Chrome DevTools MCP for checking pages while developing |

Requirements on the machine running Claude Code: Node 22+, git, Chrome and the GitHub CLI. Say "set up my environment" and the `dev-setup` skill installs and checks them.

## Maintaining this template
- Mark this repo as a template once: `gh repo edit --template`. CI and deploy are skipped in the template repo itself (it is all `{{placeholders}}`) and run in every repo created from it.
- To test template changes run `node tools/selftest.mjs` (`--lighthouse` for the full set). It fills a copy of the repo from `tools/fixture/`, adds a blog post and runs the real tools; CI does the same in the template repo.
