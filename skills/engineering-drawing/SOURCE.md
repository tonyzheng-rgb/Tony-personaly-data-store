# Source and review (2026-11-02)

Installed from the public GitHub repo earthtojake/text-to-cad (MIT, LICENSE verified at repo root on 2026-11-02), skills cad, dxf and engineering-drawing, at Tony's request for mechanical-design and CAD skills.

- Installed as text: each skill's SKILL.md, references/ and its own LICENSE. The agents/openai.yaml files for other agent platforms were dropped.
- NOT installed: the repo's cadgen engine, CAD Viewer, MCP servers and installer (a uv-managed Python 3.13 plus Node runtime, roughly 300 MB cloned), and the other eight skills (bambu-labs and sendcutsend involve external printing/ordering services; gcode, sdf, srdf, urdf, step-parts, dfm and dfam-check are niche). The modeling, positioning, export and inspection knowledge in the references is usable as installed; actually building models needs the runtime set up or direct build123d work via the build123d skill, which should be arranged on the first real CAD job.
- LICENSE.txt (MIT) is retained in each skill folder.
