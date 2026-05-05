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

After setup, every push to `main` deploys automatically:

```bash
git add <files>
git commit -m "Add slide deck"
git push origin main
```

## Current Decks

- `Pi Agent Loop Design`: `/slides/pi-agent-loop/`

## License

MIT
