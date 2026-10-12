---
name: summary-slides
description: Summarize a topic, repository, or technical session as a self-contained HTML slide deck, or publish an existing deck in erain/summary-slides on Vercel. Use when asked to create or publish slides for summary-slides.vercel.app.
---

# Summary Slides

Create a useful, self-contained knowledge summary and prepare it for this site:

- Repository: https://github.com/erain/summary-slides
- Site: https://summary-slides.vercel.app/
- This skill: https://summary-slides.vercel.app/skills/summary-slides/SKILL.md

These instructions work with coding agents that can edit files and run shell
commands. No particular agent, plugin, or presentation library is required.
Reading the hosted skill does not install it; use your agent's skill mechanism
if persistent discovery is desired.

## Establish the task

Respect whether the user wants a new summary, an existing deck published, or
both. For an existing deck, preserve its content and design unless changes are
requested or needed for hosting. Infer audience and scope from the request;
ask only when missing information would materially change the result.

Locate the user's checkout, or clone the repository into a new directory if
needed. Verify the remote before editing. Read applicable `AGENTS.md`,
`CLAUDE.md`, `CONTRIBUTING.md`, and `README.md` instructions. Inspect the current
root `index.html`, `vercel.json`, and one deck before assuming the layout below
still applies. Work on a branch and preserve unrelated user changes.

All files deployed from this repository are public. Include only material the
user intends to share; never copy credentials, private logs, or private source
code into a deck. An unlinked URL is still public.

## Summarize knowledge

Read the supplied material before drafting. For repository summaries, trace
the relevant implementation and tests rather than relying only on README
claims. For a completed coding session, explain the problem, final behavior,
important decisions, and validation. For external topics, verify changing or
uncertain claims with primary sources.

Choose a narrative that suits the audience: orient the reader, explain the
mechanism with a concrete example, show important tradeoffs, and finish with
takeaways. Prefer one main idea per slide; choose the slide count to fit the
material rather than enforcing a fixed count. Use diagrams, short code
excerpts, and comparisons when they explain more clearly than bullets.

Make the deck understandable without the chat transcript. Define unfamiliar
terms, distinguish evidence from inference, and avoid invented measurements
or unsupported claims. Put source links beside factual claims or on a sources
slide. Record repository revisions or dates when they affect reproducibility;
use shareable source links instead of local filesystem paths.

## Build and integrate the deck

The current repository is a static site with no package manager or build step:

```text
index.html                         # Homepage with manually maintained cards
slides/<slug>/index.html           # Each deck's entrypoint
slides/<slug>/...                  # Optional local images or other assets
vercel.json                        # Static hosting and deck URL rewrites
skills/summary-slides/SKILL.md      # Hosted agent instructions
```

Use a descriptive lowercase, hyphenated slug. Do not overwrite an existing
deck unless the user requested an update. Place a new deck at
`slides/<slug>/index.html`; keep any local assets inside that folder and use
relative asset URLs. The expected public URL is
`https://summary-slides.vercel.app/slides/<slug>`; confirm the current hosting
configuration when publishing.

Prefer a single HTML file with embedded CSS and JavaScript, system fonts, and
inline SVG diagrams. Avoid adding a framework, build pipeline, or CDN
dependency for an ordinary deck. Match a requested visual style; otherwise
use a readable, consistent design rather than copying an existing deck's
limitations.

Provide semantic headings, readable contrast, visible previous/next controls,
keyboard navigation, focus indicators, and a slide counter. Keep controls
clear of content. Handle the first and last slides, avoid intercepting keys in
editable controls, and ensure long content remains reachable on small screens.
Include a viewport declaration and useful document title. If using animation,
honor reduced-motion preferences. A print stylesheet should expose every
slide for printing or saving as PDF.

Add a card to the root `index.html` with the deck title, a concise description,
and a link to `/slides/<slug>`. Keep existing cards intact. Update the README's
current-deck list if it is still maintained manually. Do not introduce a
second catalog or change Vercel settings unless the task requires it.

## Validate before review

Run any checks required by the current repository. At the time this skill was
written, it had no test, lint, or build target; do not invent a successful
build result. Serve it locally, for example:

```bash
python3 -m http.server 8080 --bind 127.0.0.1
```

Check the homepage link, `/slides/<slug>/index.html`, and all local assets over
HTTP. Python's server does not implement Vercel rewrites: test the explicit
HTML path locally and the canonical deck URL on Vercel after deployment.

When browser tooling is available, inspect desktop and narrow viewports,
advance through every slide, exercise buttons and keyboard controls, check
focus and print layout, and inspect the console for errors. For a supplied
deck, verify its existing navigation rather than imposing a new design.
If browser tooling is unavailable, report that visual and interaction checks
were not run. Re-read the complete diff and ensure changes stay within scope.

## Publish and report

The documented deployment flow is Git integration: merging a branch into
`main` triggers Vercel. Follow current repository instructions if this changes.
Do not push directly to `main` or create a separate Vercel project.

Prepare and validate the files before any required approval. Commit, push,
open a PR, or merge only within the user's authorization and applicable
instructions. If commits must be written by the author, leave the changes
uncommitted and explain the remaining step. Never add AI attribution to commit
messages. A PR description should explain the resulting behavior, validation,
related issue when applicable, and AI assistance in one truthful sentence;
do not claim the human reviewed or tested changes before they have.

After an authorized merge, inspect deployment status if available and fetch
the public deck URL. Verify that it serves the expected deck and assets;
HTTP 200 alone can be an unrelated fallback page. If deployment fails, diagnose
within scope and report the failure; do not retry pushes or alter project
settings without a concrete reason.

Return the deck path, checks performed, and publication status. Label a URL as
expected or pending until the deployment has been verified. If authorization
or deployment access is missing, leave a reviewable result and state the exact
remaining step rather than claiming it is published.
