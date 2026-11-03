# Source and review

Written by Muse on 2026-11-01 after studying the spreadsheet skill in the public GitHub repository `anthropics/skills` at commit ca45fc496a3436251f191354091d557da31c15b5, folder `skills/xlsx`.

That upstream skill carries a proprietary Anthropic license that forbids retaining copies outside Anthropic services and creating derivative works, so neither its text nor its scripts were copied into Muse. This skill is an original summary, in Muse's own words, of widely used spreadsheet practice that the study confirmed, including live formulas, assumption cells, LibreOffice recalculation, function compatibility limits and financial model color conventions.

Verified in this environment during installation. openpyxl and pandas import cleanly, LibreOffice is available as `soffice`, and a test workbook with a SUM formula recalculated to the correct cached value. The markitdown command mentioned upstream is not installed here, so this skill does not rely on it.
