# Summary Slides

A collection of self-contained HTML slide decks for technical presentations, deployable to Vercel.

## Structure

```text
├── index.html              # Main index page listing all slide decks
├── slides/
│   ├── pi-agent-loop/      # Pi Agent Loop Design slides
│   │   └── index.html
│   └── [future-slides]/    # Add new slide decks here
├── vercel.json             # Vercel static deployment configuration
├── skills/summary-slides/
│   └── SKILL.md            # Portable agent skill for creating and publishing decks
└── README.md
```

## Local Development

Serve locally with any static file server:

```bash
# Python
python3 -m http.server 8080

# Node.js
npx serve

# Vercel CLI
vercel dev
```

Then open:

```text
http://localhost:8080
```

## Adding New Slides

1. Create a new folder under `slides/`:

   ```bash
   mkdir slides/my-new-topic
   ```

2. Add an `index.html` file with your slide deck:

   ```text
   slides/my-new-topic/index.html
   ```

3. Update the root `index.html` to add a card linking to:

   ```text
   /slides/my-new-topic/
   ```

## Vercel Deployment

One-time setup:

1. Open Vercel.
2. Import Git repository `erain/summary-slides`.
3. Use framework preset `Other` or static site defaults.
4. No build command is required.
5. Output directory can remain the repository root.

After setup, merging a pull request into `main` deploys automatically. Prepare
changes on a branch, validate locally, and have the author review and commit
them before opening a pull request. Do not push directly to `main`.

## Agent Skill

The portable [Summary Slides skill](skills/summary-slides/SKILL.md) covers
summarizing knowledge, building self-contained HTML decks, updating this
site's catalog, validating, and publishing through the repository's Git flow.
Once these files are deployed, its public URL is:

<https://summary-slides.vercel.app/skills/summary-slides/SKILL.md>

Give any coding agent that can fetch URLs and edit the repository this prompt:

```text
Read and follow https://summary-slides.vercel.app/skills/summary-slides/SKILL.md.
Summarize <topic, repository, or session> as an HTML slide deck for <audience>.
Prepare it in erain/summary-slides for review and publication.
```

For an existing deck, replace the last two sentences with:

```text
Use this skill to prepare <path/to/deck.html> for publication in erain/summary-slides.
```

Fetching the skill supplies instructions for that session. For persistent
discovery, copy the `skills/summary-slides/` directory into the skill location
supported by your agent (for example, `~/.codex/skills/summary-slides/` or
`~/.claude/skills/summary-slides/`). Commit, push, and merge permissions still
follow the user's instructions; the skill does not grant them.

## Current Decks

- `Pi Agent Loop Design`: `/slides/pi-agent-loop/`

## License

MIT
