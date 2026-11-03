# Source and review

Learned and installed on 2026-11-03 at Tony's request via `npx dashi-ppt-skill@latest`.
Registry state at install time: the `latest` dist-tag pointed to version 0.4.5 on both
registry.npmjs.org and registry.npmmirror.com, even though higher patch versions up to
0.4.11 exist on the registry without the `latest` tag. Version 0.4.5 (the @latest
resolution of the user's command) is what was reviewed and installed.
Upstream: https://github.com/chuspeeism/dashi-ppt-skill (author chuspeeism; npm
maintainer jadon7). License: AGPL-3.0-only — LICENSE copied into this folder from the
npm package (the package keeps it at the root, outside skill/). Same AGPL caveat as
guizang_ppt_skill: internal use fine; public distribution of generated decks/templates
should respect AGPL terms.

## Install method

Reviewed the tarball first (extracted to ~/workspace/skill-review/dashi-ppt-skill/),
then installed with the package's own installer pointed at Muse's skill root:
`node bin/install.mjs --dir ~/workspace/custom-skills`, producing `dashi-ppt/`
(57 MB, the upstream skill name). Running bare `npx dashi-ppt-skill@latest` would only
have probed ~/.agents/skills, ~/.claude/skills, ~/.codex/skills and
~/.config/agents/skills — none of which register skills in Muse.
Added by Muse after install: skill.yaml, this SOURCE.md, LICENSE.
Note: re-running the upstream installer replaces the whole folder atomically, so these
three added files would need to be re-added after any upstream update.

## Review findings (2026-11-03)

- `bin/install.mjs` inspected in full: it only copies the package's `skill/` tree into
  the target skill root via a staging dir + atomic rename, preserves an existing
  project/node_modules and .npmrc across updates, migrates a legacy `dashiai-ppt`
  folder inside the same root, and writes project/.npmrc. No network, no credentials,
  no writes outside the target skill folder.
- The skill is a generator, not just guidance: `project/` is a Node/React app
  (Node >= 20) with 12 themes. On first generation its render script runs `npm install`
  inside project/ (registry from project/.npmrc — the installer wrote
  registry=https://registry.npmmirror.com) and starts a local HTTPS preview server;
  PPTX/PDF export drives a local Chrome/Playwright. All network endpoints found in the
  code are the npm registries, the npmmirror Playwright binary mirror, localhost
  preview hosts, and the version-check endpoints below. No telemetry or data upload
  was found.
- `scripts/check_latest_version.mjs`: SKILL.md requires running it before the final
  reply of each generation request. It only GETs the published version number from
  npmmirror / npmjs / GitHub raw and prints an update notice if newer; it sends no
  user data, and failures are silent by design. Kept as-is; this is also why update
  notices may appear after future deck generations.
- SKILL.md workflow rules kept unchanged: it must ask the user for theme style and
  media needs before building (unless fully delegated), shows
  assets/skill/theme-style-grid.png when asking about style, defaults to HTML output,
  and only produces PPTX when the user explicitly asks for PPTX/PowerPoint format.
