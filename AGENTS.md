# AGENTS.md

This repository is data, not an app: design tokens (`tokens.json`), component rules (`components/*/README.md`), reference markup (`components/*/preview.html`, `components/bundle.css`), fonts and logos.

**Change the artifact first, then export.** The editable system is the Orbi Design System artifact in Claude (https://claude.ai/artifact/FyGc28kcprZW3HMDPb3Cyu); this repository is its exported copy.

1. Edit the artifact and publish it. Note the version number the publish reports.
2. Export: copy every file under the artifact's `project/` to the same path here (`project/README.md` → `README.md`, `project/components/…` → `components/…`), and the Logos assets to `assets/Logos/`. The artifact's `project/design-system.json` stays in the artifact. Only `AGENTS.md` and `.github/` live in this repository alone.
3. Open a PR whose description has the line `Canvas version: N`, where N is that artifact version. The `canvas-version` check fails a PR without it.

Never change a file here that the artifact also holds without changing the artifact first; a PR that does is a fork of the system, not a change to it.

- Keep `tokens.json` valid JSON in its list shape (`{"tokens":[{"name","value","usage"}]}` per family; `color.themes` = light, dark). Every token carries a `usage` note naming where it is used.
- Change a value here only together with the consuming repositories that use it (orbi-cloud, orbi-website); say which pages change in the PR.
- Text contrast 4.5:1 per theme; a failing pair inherited from the source stays and is flagged in its `usage` note.
- Fonts under `fonts/` are OFL; keep their license files next to them.
