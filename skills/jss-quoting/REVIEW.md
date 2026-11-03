# JSS Quoting Skill Review

Reviewed and installed on 2026-11-01 by Muse at Tony's request.
Source: `jss-quote-agent.zip` (78,736 bytes, 40 files) from the public GitHub repository `tonyzheng-rgb/Tony-personaly-data-store`, commit `10121ca404da47b91792fe0c04c390b20e7d8614`, uploaded 2026-11-01 15:34 Asia/Shanghai.

## Installed

- Adapted `skills/jss-quoting/SKILL.md` as the Muse skill body, with metadata moved to `skill.yaml`.
- `references/quoting-knowledge.md` and `references/3a225-compliance.md`, copied unchanged.
- `references/project/`, the 12 category knowledge files from `agent/memory/project/`, copied unchanged.
- `references/business-rules-source.md`, copied from `agent/rules.md` for delivery, warranty and payment terms.

## Not installed, with reasons

- Upload helpers `push.sh`, `push.bat`, `upload.sh`, `device_flow.sh` and `上传到GitHub.md`. They are GitHub publishing helpers, not quoting tools. The device flow script obtains a GitHub access token and writes it to the gh CLI hosts file, so it was excluded on credential safety grounds. No actual token, API key or password was found anywhere in the package. The device flow script contains one public OAuth client ID, which is not a secret.
- Generator scripts under `scripts/gen_*`. Syntax checks passed, but they are one off examples with hardcoded customer data, including the customer names Saeed Bright Company and MujtahidCNC, the customer emails samiullahsamim735@gmail.com and ameenfahmi@gmail.com, the mobile number 18896754675, and Windows output paths under `C:\Users\Administrator\Coze\`. The installed skill instructs Muse to build a fresh generic generator per quote instead. This also means the README claim that the package contains no customer personal information is not accurate.
- `scripts/daily_market_chart.py`. It fetches live data from Sina Finance, open.er-api.com and investing.com and depends on a Coze SDK that is not available here. It is a market chart tool, not a quoting tool.
- `scripts/quote_calc.py`. It is a single hardcoded order with an exchange rate of 7.2 and takes no arguments, despite the migration guide claiming a `--net --tax --qty --fx` interface.
- `agent/system_prompt.md`, `agent/memory/SOUL.md` and `agent/memory/USER.md`. These are Coze agent persona files. They ban Markdown headings and tables, which conflicts with the copyable quote table this skill must produce, and the user profile describes a generic Coze account rather than Tony. Their business rules were merged where consistent, and conflicts were flagged instead.

## Conflicts flagged in the installed skill

- Tax. General rules say taxed equals untaxed times 1.10, with drag chains at 1.13 and NMRV already taxed with freight. Several original price tables state tax added at 13 percent, including the main stepper, BLDC, servo and power supply table, Changrong inverters, ball screws and rails, and drag chains. The JSSMK1 servo file uses 1.10. The installed skill requires confirming and stating the tax basis per category.
- Exchange rate. 6.67 in the README, original skill and quick reference. 6.7 in the business rules, agent memory, user profile and system prompt, dated 2026-10-13. 7.2 in the old example calculator. The quick reference also converts USD from the taxed price, while other files convert from an unspecified RMB price. The installed skill requires stating the rate, its date and the conversion basis, and forbids 7.2.
- Quantity tiers. The export workflow treats about 50 units as the baseline, adds 5 percent for 1 to 10 units and negotiates 100 plus. The business rules treat 1 to 10 units as the baseline and subtract 5 percent for 51 to 100 units. The installed skill requires stating the baseline and confirming when it decides the price.
- Missing file. The migration guide lists `scripts/tony_daily_todo.py`, which is not in the zip. It also points at `pricing_xlsx/` and `data/*.xls` source spreadsheets, which are not in the package, so the Markdown knowledge base is the only price source installed.

## Verification

- All eight Node generator scripts passed `node --check`, and both Python scripts compiled, during review. None of them were executed, because several write to hardcoded Windows paths or fetch live network data.
- The installed skill was confirmed discoverable through `muse.skill_search` after installation, and a knowledge lookup test was run against the installed references.
- Quote file generation with this skill is untested. The first real quote file should be checked against a known good sample before it is sent to a customer.

## Privacy warning

- The source repository is public, and the zip inside it contains supplier pricing, the company full name and the customer data listed above. The migration guide itself recommends a private repository for this material. Consider making the repository private, or publishing a scrubbed copy.
