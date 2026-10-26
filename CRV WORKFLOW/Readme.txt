# NOZ CRV – Run the Workflow with Claude

Builds a complete CRV (Batch Information, Additional Information, product rows, embedded images) from the blank GOL template, a supplier website and product photos. Each run produces a new workbook and a quality-control report.

## What you need (attach all of these in ONE message)
1. `NOZ_CRV_Universal_Master_Workflow_V1_4_DRAFT.md`, the governing workflow
2. The blank CRV template (`Modele CRV GOL.xlsx`), unmodified
3. The supplier's email, pasted as text or attached. It should include any offer, price list, stock list or specs they sent.
4. Any supplier attachments (price list, catalogue, spreadsheet, PDF)
5. Product pictures, one file per reference
6. Optional: the supplier website URL (clean, without ad-tracking parameters), to confirm specs or retail prices the email doesn't cover

If the workflow file is missing, Claude will ask for it and stop.

**Real runs:** nothing is filled in without concrete information from the email, attachments or website. Anything missing is left blank and flagged [M] in the proposal. Claude never guesses or uses hypothetical values.
**Training runs:** only when the prompt says TRAINING, Claude may propose hypothetical values, always marked as training assumptions.

## Prompts to paste

### Real supplier
```
Read the attached NOZ CRV Universal Master Workflow V1.4 completely and follow all its instructions.
OPERATING MODE: REAL SUPPLIER
I have attached the original blank NOZ CRV Excel template and the supplier materials available to me, including emails, stock lists, documents, product pictures, or other supporting information.
Your task:

1. Analyze the supplier's email, attachments, stock information, and website (if provided).
2. Prepare the complete CRV proposal, including all 18 Batch Information fields, the Additional Information sections, and every product reference in the Supplier's Listing.
3. Use verified information from the supplier's documents and correspondence for stock quantities, supplier references, wholesale prices, clearance prices, packaging, pallets, and commercial terms.
4. Use the supplier's or manufacturer's website to research product specifications, brand information, images, and regular retail prices. Do not treat catalogue availability as evidence of actual clearance stock.
5. Do not invent, estimate, or assume missing supplier facts. Leave unsupported fields blank and flag them as `[M — MISSING]` in the exceptions report.
6. If packaging information or quantities are missing, never insert zero as a substitute. Preserve quantity formulas where appropriate, but do not present an unsupported calculation as verified stock.
7. Confirm the currency, applicable tax treatment, exchange-rate date, and official BNR rates before converting prices into EUR. If verification is incomplete, flag it.
8. Follow the approved designation rule: Column C and Column D must contain exactly identical descriptions, character for character.
9. Preserve all original Excel functionality, including dropdowns, hidden sheets, formulas, formatting, connections, external links, and other applicable template features.

APPROVAL PROCESS
First, present one consolidated CRV proposal with all available information and a clear exceptions report.
Do not modify Excel until I explicitly approve.
AFTER MY APPROVAL
Create a new completed Excel workbook without overwriting the original.
Before delivery, compare every populated field against the approved proposal. Verify the quantity formulas, cached results, prices, pallet totals, dropdowns, and embedded product images.
Verify that images actually display in the correct worksheet rows, not merely that they exist inside the Excel package. If actual display cannot be tested, mark it `NOT VERIFIED`.
Deliver the completed `.xlsx` workbook and a detailed Markdown quality-control report with `PASS`, `FAIL`, `NOT VERIFIED`, or `NOT APPLICABLE` results.
SUPPLIER INFORMATION
Supplier website (optional): [PASTE WEBSITE]
Supplier email: [PASTE EMAIL OR ATTACH IT]
Additional instructions: [OPTIONAL]
```

### Training
```
Read the attached NOZ CRV Universal Master Workflow V1.4 completely and follow all its instructions.
OPERATING MODE: TRAINING
This is a simulated NOZ clearance-stock exercise.
I have attached the original blank NOZ CRV Excel template and the available product images. Use the supplier website below to research and identify the products.
Your task:

1. Identify each product from the uploaded images and match it to the correct supplier or manufacturer listing.
2. Research product specifications, model, brand, technical details, and regular retail prices.
3. Prepare all 18 Batch Information fields, the Additional Information sections, and every product reference in the Supplier's Listing.
4. For information missing from the website, proactively propose realistic hypothetical training values for references, quantities, packing, pallets, wholesale prices, clearance prices, lot origin, and commercial arrangements.
5. Clearly label proposed hypothetical information as `[A — PROPOSED]`. Never present simulated supplier information as a verified fact.
6. Do not automatically use fixed wholesale or clearance percentages or standard cartons-per-pallet assumptions. Explain your proposed pricing and logistics methodology.
7. Confirm or clearly qualify the source currency, retail tax treatment, applicable BNR exchange rates, and EUR calculations.
8. Follow the approved designation rule: Columns C and D must contain identical descriptions, character for character.
9. Ensure the proposed pallet allocation and quantities are internally consistent.
10. Identify unmatched images, missing specifications, unclear brands, and any contradictory information.

APPROVAL PROCESS
Prepare the complete batch proposal and exceptions report before editing.
Propose sensible values wherever information is missing instead of asking me to research everything manually.
Present one consolidated approval request covering the entire batch.
Do not modify Excel until I explicitly approve.
AFTER MY APPROVAL
Create a new completed Excel workbook using the original template.
Preserve all workbook features, including dropdowns, hidden sheets, formatting, external links, connections, and supported data-model components.
Embed the actual approved product images into the correct rows. Do not substitute unrelated pictures.
Before delivery, compare the entire finished workbook against the approved proposal. Verify that:

* All approved reference data matches.
* Columns C and D contain identical descriptions.
* Column E contains `As per visual`.
* All J formulas and cached quantity results are correct.
* K, L, and M contain numeric EUR prices.
* The total pallets match Batch Information.
* All product images are correctly embedded and visibly displayed.

If actual image display cannot be tested, mark it `NOT VERIFIED` rather than claiming success.
Deliver the completed `.xlsx` workbook together with a Markdown quality-control report documenting passed checks, failed checks, limitations, and all approved training assumptions.
SUPPLIER WEBSITE: [PASTE WEBSITE]
Additional training instructions: [OPTIONAL]
```

## Steps
1. **Attach** everything listed in "What you need" in ONE message, then paste the Real or Training prompt with the placeholders filled in. Delete any optional lines you don't use.
2. **Review the proposal.** Claude shows ONE consolidated proposal: all 18 Batch Information fields, the Additional Information sections, every product reference, and an exceptions report. Each value is tagged:
   - [V] verified (supplier documents or website)
   - [A — PROPOSED] training assumption (training mode only)
   - [M — MISSING] not provided, left blank (real mode)
   - [C] conflict or unverified
3. **Approve or correct.** Reply `approve`, or list the changes. Claude does not touch Excel before an explicit approval.
4. **Receive two files:**
   - the completed CRV workbook (`.xlsx`), created as a new file; the original template is never overwritten
   - a Markdown quality-control report with PASS / FAIL / NOT VERIFIED / NOT APPLICABLE per check

## Before you send the file on (always do this)
Claude's checks are structural. It can't open the file in desktop Excel, so the QC report will say "desktop Excel open test not performed". A human must do the final review.

1. **Open the file in desktop Excel.** Make sure it opens without a repair prompt and the dropdowns still work.
2. **Check the images.** Each picture must show in the correct row and match the product. Image-to-product matches are often probable, not certain.
3. **Check prices and currency.** Confirm the source currency, whether prices include VAT or other tax, and the BNR exchange rate and date if a conversion was done.
4. **Check the quantities.** Compare stock quantities, packing and pallet totals with the supplier's email, and check that pallet totals match Batch Information.
5. **Check the price columns for `###`.** If they appear, widen the columns.
6. **Read every flagged item** in the QC report ([M], [C], NOT VERIFIED) and resolve it, or leave it clearly marked.
7. **Disclosed file changes.** Excel recalculates formulas when the file opens, and the print areas are widened to include the filled rows. Both are listed in the QC report.

## Rules the workflow follows
- Columns C (Supplier's Designation) and D (NOZ Designation) are always identical, character for character.
- Column E always contains `As per visual`.
- The original template is never modified or overwritten; a new workbook is created.
- Nothing in Excel is changed before you explicitly approve the proposal.
- Dropdown cells only use values that exist in the template's lists.
- Template functionality (dropdowns, hidden sheets, formulas, formatting, links, connections) is preserved.
- Prices in K, L and M are numeric EUR. Currency, tax treatment and the BNR rate and date are confirmed before any conversion; if not verified, they are flagged.
- Real runs: nothing is invented or estimated. Missing data stays blank and is flagged [M — MISSING]. Missing packaging or quantities are never replaced with zero.
- Training runs: hypothetical values are allowed only if labelled [A — PROPOSED], with the pricing and logistics method explained. Percentages and standard cartons-per-pallet figures are not applied automatically.
- Catalogue availability on a website is not evidence of actual clearance stock.

## Known limits
- Supplier prices are often hidden behind a login. Claude then flags them [M] or, in training mode only, proposes labelled assumptions.
- Claude may not be able to read some websites. If so, attach screenshots or a PDF of the product page.
- Claude's checks (structure, formulas, image embedding, a LibreOffice render) don't replace a final human review in desktop Excel.
- A LibreOffice render can show `###` or odd letter spacing because the template's font (Segoe UI Emoji) isn't installed there. This is a display artefact, not necessarily an error in the file.
- If the supplier's email is unclear or contradicts its own attachments, Claude flags it [C] rather than choosing one version.
- The workflow is marked DRAFT (V1.4). If a newer version exists, attach that one instead.