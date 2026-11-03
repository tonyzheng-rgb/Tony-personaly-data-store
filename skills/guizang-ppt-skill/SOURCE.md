# Source and review

Learned and installed on 2026-11-03 at Tony's request from the public GitHub repository
`op7418/guizang-ppt-skill` （歸藏）, commit 93d21bf4a73a851907a6eb00acbf30618236667a (2026-10-30).
Upstream: https://github.com/op7418/guizang-ppt-skill

## What the skill does

Generates a single-file HTML horizontal-swipe presentation deck in two styles:
A) editorial magazine x e-ink (serif, fluid WebGL background, warm themes) and
B) Swiss International (sans, grid/dot-matrix, IKB / lemon yellow / lemon green / safety orange).
Shared features: keyboard/wheel/touch paging, ESC overview, presenter mode with current/next
16:9 previews, speaker notes, rehearsal timing, audience-screen sync.

## License

Upstream is GNU AGPL-3.0; the full LICENSE text is kept in this folder. Note for later use:
decks built from the bundled templates embed AGPL-licensed template code, so public
distribution of generated decks should respect AGPL terms; internal/company use is
unaffected in practice.

## Review findings (2026-11-03)

- `scripts/` (4 .mjs files: gz-theme, validate-swiss-deck, validate-presenter-mode,
  check-presenter-runtime-sync) inspected: pure local file/text and color-contrast checks.
  No network calls, no environment-variable or credential access, no child processes,
  no telemetry, no hardcoded personal or customer data.
- `assets/template.html` and `template-swiss.html` load public CDN resources when a
  generated deck is opened online: Google Fonts, Motion One (jsdelivr) and Lucide
  (unpkg). Motion also has the bundled local `assets/motion.min.js` fallback; fonts and
  icons simply degrade offline. Nothing is uploaded by the templates.
- SKILL.md "Step 0" asks the agent to check upstream git updates before each use and to
  ask the user before updating, never auto-update. This install is NOT a git checkout,
  so that check cannot run; per the upstream text itself, state that and continue with
  the installed version. To update, re-clone the upstream repo and re-review.

## Installed / excluded

Installed: SKILL.md (upstream text unchanged), references/ (11 files), scripts/ (4 files),
assets/ (both templates, motion.min.js, screenshot-backgrounds/), LICENSE, plus this
SOURCE.md and a Muse skill.yaml.

Excluded as non-skill material: .github/, docs/unification-plan.md (upstream internal
planning), README.md / README.en.md / CONTRIBUTING.md / SPONSORS.md, and
assets/ppt-skill-showcase.png (3.5 MB README showcase image).
The review clone is kept at ~/workspace/skill-review/guizang-ppt-skill/.
