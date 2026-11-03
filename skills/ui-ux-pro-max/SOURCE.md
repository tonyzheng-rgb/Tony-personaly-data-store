# Update (2026-11-03)

At Tony's request to learn this repo again, upstream was re-fetched and diffed against
this install. Upstream HEAD 713eef51b04efc98d6fa565323b495f7c9c89fd4 (2026-11-02 23:10 +0700)
adds exactly one feature over the 2026-11-02 install: RTL compatibility levels and a
`--rtl` filter for style/product search (SKILL.md guidance, an RTL column in
data/styles.csv and data/products.csv, and matching logic in scripts/core.py and
scripts/search.py). The script diff was reviewed — no new network or system imports.
Those 5 files were updated in place; the tests/ folder and validate_data.py remain
excluded as before. Smoke test after update: dataset search works, and
`--domain style --rtl=full` returns filtered results.

# Source and review (2026-11-02)

Installed from the public GitHub repo nextlevelbuilder/ui-ux-pro-max-skill (MIT, ~143.9k stars at review time), skill folder .claude/skills/ui-ux-pro-max, at Tony's request for stronger web UI/design skills.

- Installed the SKILL.md, data CSVs, references, and the local scripts (search.py, core.py, design_system.py, reasoning_contract.py). The scripts do BM25 search and design-system generation over the bundled local data only; a network-import scan of the core scripts found no urllib/requests/http usage.
- Excluded the scripts/tests suite (repository self-tests and fixtures, not needed to use the skill) and the optional npm CLI installer.
- The repo also markets a paid Premium version; the installed GitHub version is the free release and is complete as installed. LICENSE.txt (MIT) is retained.
