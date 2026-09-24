# AGENTS.md

This repository is data, not an app: design tokens (`tokens.json`), component rules (`components/*/README.md`), reference markup (`components/*/preview.html`, `components/bundle.css`), fonts and logos.

- Keep `tokens.json` valid JSON in its list shape (`{"tokens":[{"name","value","usage"}]}` per family; `color.themes` = light, dark). Every token carries a `usage` note naming where it is used.
- Change a value here only together with the consuming repositories that use it (orbi-cloud, orbi-website); say which pages change in the PR.
- Text contrast 4.5:1 per theme; a failing pair inherited from the source stays and is flagged in its `usage` note.
- Fonts under `fonts/` are OFL; keep their license files next to them.
