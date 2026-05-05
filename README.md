# Summary Slides

A collection of HTML slide decks for technical presentations, deployable to Vercel.

## Structure

```
├── index.html              # Main index page listing all slide decks
├── slides/
│   ├── pi-agent-loop/     # Pi Agent Loop Design slides
│   │   └── index.html
│   └── [future-slides]/   # Add new slide decks here
├── vercel.json            # Vercel deployment configuration
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

## Adding New Slides

1. Create a new folder under `slides/`:
   ```bash
   mkdir slides/my-new-topic
   ```

2. Add an `index.html` file with your slide deck

3. Update the main `index.html` to link to your new slides

## Deployment

Push to the `main` branch to trigger Vercel deployment:

```bash
git add .
git commit -m "Add slide deck"
git push origin main
```

## License

MIT
