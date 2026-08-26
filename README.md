# GitHub Jet Heatmap

A retro-arcade "starfighter" that flies over your GitHub contribution grid — an animated SVG built from your real GitHub contribution data, meant to be dropped into your profile README.

<p align="center">
  <img src="https://raw.githubusercontent.com/Shoegum010/github-jet-heatmap/main/dist/github-jet.svg" alt="GitHub Jet Heatmap" width="100%" />
</p>

## How it works

- `generate.mjs` fetches your contribution calendar via the GitHub GraphQL API and renders it as an animated SVG (scanlines, HUD, target-lock brackets, a jet that patrols across your contribution weeks).
- A GitHub Action (`.github/workflows/jet-heatmap.yml`) regenerates the SVG daily and commits it back to the repo, so the embedded image always reflects your latest activity.
- If no `GH_TOKEN` is available (e.g. running locally without setup), it falls back to a deterministic mock grid so you can preview the visual.

## Using this in your own profile README

1. Fork or clone this repo as `github-jet-heatmap` under your own account.
2. The workflow already uses `github.repository_owner` and the built-in `GITHUB_TOKEN`, so no extra secrets are needed — just make sure Actions has write permission (Settings → Actions → General → Workflow permissions → Read and write).
3. Run the workflow once (or wait for the daily schedule) so `dist/github-jet.svg` gets generated.
4. Embed it in your profile README:
   ```md
   ![GitHub Jet Heatmap](https://raw.githubusercontent.com/<your-username>/github-jet-heatmap/main/dist/github-jet.svg)
   ```

## Local development

```bash
npm install    # no runtime deps currently required, but keeps this future-proof
GH_USERNAME=<your-username> GH_TOKEN=<a token with read:user scope> npm run generate
npm test
```

## Credits

Concept and original implementation by [pratikforge](https://github.com/pratikforge). This version has been customized and is maintained independently.
