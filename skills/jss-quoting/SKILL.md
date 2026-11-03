# JSS Quoting

- Use this skill when the user asks for a price, a quote file or an export compliance check for JSS products from Changzhou Jin Sanshi, including stepper motors, closed loop steppers, JSSMK1 servo, BLDC motors, spindle motors, inverters, gearboxes, ball screws, linear rails and drag chains.

- Treat the price data as dated internal reference data from the 2026-03-30 V5 sales price list, and remind the user to confirm against the current price list before a real deal closes when the quote matters.

## Resolve conflicts before quoting

- Check the tax rate for the specific category before calculating a taxed price, because the source package conflicts on this point.

  - Tax basis was verified against the original price sheets on 2026-11-02 and is recorded per category at the top of `references/quoting-knowledge.md`: servo uses 1.10; stepper motors, switching power supplies, Jester and Changsheng spindles, fourth axis, Changrong inverters and drag chains use 13 percent; NMRV is already taxed with freight. Hanqi and Changlong spindles, ball screws and rails, and the Tonghang AST section state no tax rate in their originals, so confirm those with the user before quoting a taxed price.

  - State in the quote which tax basis was used, and ask the user to confirm when the category basis is unclear.

  - Treat NMRV worm gearboxes as already taxed with freight included, and do not add tax again.

- Calibrate the USD exchange rate on the day of the quote, because the source package conflicts here too.

  - Note that the skill and README use 6.67, the business rules and agent memory use 6.7 as of 2026-10-13, and an old example script uses 7.2, which must never be used.

  - State the rate used and its date in every USD quote, and say whether the USD figure was converted from the untaxed or the taxed RMB price.

- State the quantity tier baseline used, because the sources conflict on small orders.

  - There is no company-wide baseline: the original sheets verified on 2026-11-02 each carry their own tiers (servo and power supplies add 5 percent below 100 units, Jester spindles and fourth axis below 10, Changrong below 20, and each motor series has its own quantity bands). Use the tier printed in the matching original sheet and name it in the quote; the generic tiers in `references/business-rules-source.md` do not override a sheet's own tiers.

## Find the price

- Read `references/quoting-knowledge.md` first for the category price table and tier rules for every quote.

- Read the matching file under `references/project/` when the quick table lacks detail or when sources conflict, and treat that fuller knowledge base as the deciding source.

- Read the original price spreadsheet with the documents skill when the user supplies one, and match by sheet name exactly rather than by memory.

- Say plainly that a model cannot be found when it is not in the knowledge base, list the likely meanings for the user to confirm, and never invent a price.

- Decode model suffixes from the knowledge base before quoting, for example JSSMK1-H4T4030BS26 means 4 kW, three phase 380 V, 130 frame, 3000 rpm, no brake, 17 bit multi turn magnetic encoder.

## Calculate and present the quote

- Apply the quantity tier for the category before any tax or currency conversion, and name the tier in the output.

- Calculate the taxed price from the confirmed tax basis for that category, and calculate the USD price from the stated rate.

- Apply the closed loop torque rule when drawing or describing a speed torque curve, where theoretical torque equals the same size open loop value times 1.10.

- Give a copyable table first, with model, specification, quantity, unit price, subtotal, tax basis, tier and rate, so the user can forward it to a customer directly.

- Add delivery, warranty and payment terms from `references/business-rules-source.md` only when the user asks for a full quotation, and check the current terms with the user before sending a formal quote to a customer.

## Make quote files

- Build a fresh generic generator for each quote file with the documents skill, using the format rules in this skill and customer details only from the current request.

- Follow the Chinese MIA layout for Chinese quotes, with title, seller and buyer blocks, product table, four notes, speed torque table and curve.

- Follow the English layout for English quotes, with customer header details, product table and terms and conditions.

- Prefer pdfkit for PDF output in a Linux environment because it needs no local browser, and use exceljs style output for xlsx files with merged cells, borders and inserted images.

- Do not run the generator scripts from the source package, because the review found them to be one off examples with hardcoded customer names, customer email addresses, a mobile number and Windows file paths, and they were not installed.

## Make export documents from templates

- Read `~/workspace/templates/出口单据模板/模板索引.md` before generating any export document, and copy the matching template from that library and edit the copy rather than building the layout from scratch or editing the library original.

- Confirm which customs entity applies before filling a letterhead, because the templates exist in JSS and MPS versions and the letterhead and stamp follow the entity actually declaring.

- Keep the PI number, invoice number and contract number identical for one order, and use the packing list invoice number as the shipment reference in the booking note, following the cross document rules in the template index.

## Check export compliance

- Read `references/3a225-compliance.md` whenever the user asks about inverter export control, customs or compliance.

- Apply the three part 3A225 test, where an inverter is controlled only when output power is at least 40 VA, working frequency is at least 600 Hz and frequency control accuracy is better than 0.2 percent, all at the same time.

- Note that Changrong H100 and H300 series units at 0 to 400 Hz fall outside 3A225 control on the reference dated 2026-10-09, and tell the user to verify current rules before a major export decision.

- Offer only fully compliant routes, and never suggest false declaration, under declaration, nameplate alteration or any other evasion.

## Available connectors

- [GitHub](/opt/hatch/connectors/github/CONNECTOR.md) for fetching an updated JSS quote package from the user's repository before refreshing this skill.

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.

- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.
