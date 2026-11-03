# Source and review (2026-11-02)

Installed from the public GitHub repo drandric/claude-skills (MIT, LICENSE verified at repo root on 2026-11-02), folder src/pcb-engineer, at Tony's request for electrical and circuit knowledge.

- Installed the SKILL.md, six reference files (KiCad formats, design rules, common circuits, component selection, connector pinouts, manufacturing checklist) and scripts/generate_bom.py. The script was reviewed: it only reads a JSON parts list and writes an XLSX BOM with openpyxl; no network, no subprocess, no external calls.
- LICENSE.txt (MIT) is retained.
