# Spreadsheet Craft

- Use this skill whenever the main input or output is a spreadsheet file, such as xlsx, xlsm, csv or tsv, alongside the built in documents skill.

- Pick the tool by the job, using openpyxl for creating and editing with formulas and formatting, pandas for bulk data in and out, and a plain text extraction for a quick first look at an unfamiliar file.

## Keep formulas alive

- Write real Excel formulas for totals, ratios and derived values instead of hardcoding results computed in Python, so the sheet recalculates when its inputs change.

- Put every assumption in its own labeled cell and reference that cell from the formulas, instead of burying a rate or factor inside a formula.

- Write two or three formulas first and check they pull the expected values before filling a whole grid, because a wrong range still evaluates without any error.

- Prefer long established functions such as SUM, SUMIFS, INDEX, MATCH, IFERROR and SUMPRODUCT when the file must also open cleanly in LibreOffice.

- Avoid XLOOKUP, SORT, FILTER, UNIQUE and SEQUENCE in files that will be recalculated by LibreOffice, because it cannot evaluate them reliably and the delivered file can silently lose values.

- Sort, filter and de-duplicate in Python before writing cells when a result would otherwise need a spilling array formula.

## Recalculate before delivery

- Recalculate every workbook that contains formulas before delivering it, because openpyxl saves formula strings without cached values and most readers then show blanks.

- Run the recalculation through headless LibreOffice, which is installed in this environment as `soffice`, then read the file back and confirm the formula cells hold the expected numbers.

- Never deliver a workbook that still shows formula errors such as #VALUE!, #REF!, #NAME? or #DIV/0!, and check whether an error was already in the original file before blaming the edit.

- Copy the cached values out of any cell that links to another workbook before re-saving, because re-saving and recalculating can destroy external links and their only copy of the data.

## Read existing files carefully

- Load a workbook twice when both formulas and values matter, once normally for the formulas and once with data only for the cached values, because one pass cannot give both.

- Never save a workbook that was loaded with data only, because saving replaces every formula with a literal value permanently.

- Match the existing file conventions when editing, find its designated input cells by their distinct font color or fill, write only there and leave existing formulas untouched.

- Write only to the top left anchor of a merged range, because the other cells in the range are read only.

- Pass keep_vba when loading an xlsm file that must keep its macros, and quote a sheet name that contains a space in any cross sheet reference.

## Format like a professional

- Use one professional font such as Arial throughout unless the user or the existing file says otherwise.

- Format currency with thousands separators and the unit named in the header, render zero as a dash, show negatives in parentheses and store percentages as fractions so 0.15 displays as 15 percent.

- Follow the common financial model color convention when building a model from scratch, with blue text for hardcoded inputs, black for formulas, green for links to another sheet, red for links to another file and a yellow fill for key assumptions and cells the user should fill in.

- Document every assumption and hardcoded number where the reader will see it, in a cell comment or a note beside the table, and name the source when a number came from somewhere other than the user.

- Add a short legend and one realistic example row to a blank workbook you create for someone else to fill in, and never add such a row to a file you were only asked to edit.

- Follow the user specification literally for tab names, column headers and requested formulas, because an elegant redesign that computes something else still fails the task.

## Environment notes

- Use the Python libraries openpyxl and pandas, which are verified installed in this environment, and use LibreOffice through `soffice` for recalculation.

- Read csv and tsv sources with their real delimiter and encoding before converting them, and clean malformed rows and misplaced headers in Python rather than by hand.

## Available connectors

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.

- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.
