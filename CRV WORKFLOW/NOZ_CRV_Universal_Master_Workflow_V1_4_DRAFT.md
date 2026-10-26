# NOZ CRV — UNIVERSAL MASTER WORKFLOW V1.4 (DRAFT FOR REVIEW)

**Portable instructions for ChatGPT, Claude, and any assistant capable of inspecting and editing Excel workbooks.**

> **HOW TO USE:** Upload this `.md`, the original blank NOZ CRV `.xlsx`, and the supplier material you have (website, offer or stock list, correspondence, product images). Say: **"Follow NOZ CRV Universal Master Workflow V1.4. Prepare the complete CRV proposal and an exceptions list first. Do not modify Excel until I approve."**
>
> For a simulation add: **"TRAINING MODE. Research the products, propose clearly labelled hypothetical values for genuinely missing commercial and logistics details, and request one consolidated approval."**
>
> **PORTABILITY RULE:** Do not assume access to earlier conversations, past uploads, memory, prior approvals, example workbooks, or another AI's output. This document is self-contained and universal; each new supplier's evidence and approvals must be supplied in the current task. Examples and appendices are never authorization to reuse their values.

**Status: V1.4 DRAFT, NOT FROZEN.** It becomes the master only when the user explicitly approves it. It is built on V1.3 and keeps every V1.3 control. Changes from V1.3:
1. §4 and Appendix B now document the verified Additional Information layout of the GOL template (four merged areas, seven numbered prompts) as a template-specific example.
2. Appendix C restores the useful XML-editing lessons as template-specific implementation examples that must be verified before use.
3. The word "pallet" is used consistently for warehouse pallets.
4. §3 strengthens domain and website verification (parked domains, redirects, regional stores, currency differences).
5. New standing rule §6.1: the Supplier's Designation (C) and the NOZ Designation (D) are the same text, and it must be fully visible in the cell.

**Document map:** §1–§3 rules and research · §4 template inspection · §5–§7 content and prices · §8 approval · §9 editing · §10 quality control · §11 delivery · §12 procedure and checklist · Appendix A exceptions register · Appendix B verified GOL-template reference map · Appendix C XML implementation examples · Appendix D QC report skeleton · Appendix E case lessons (illustrative only).

---

## 1. Objective and non-negotiable rules

Prepare an accurate, usable NOZ clearance-stock **CRV Excel workbook** from the **actual supplied template**. Preserve the original. Research product facts, separate them from lot facts, identify missing data, present a consolidated proposal, obtain approval **before editing**, then create a separate verified output and a candid quality-control (QC) report.

**Never:**

- Treat a website listing or an "in stock" button as evidence of an actual liquidation lot.
- Invent a real supplier SKU, warehouse quantity, logistics specification, price, commercial offer, or NOZ response.
- Present training assumptions as verified supplier facts.
- Assume a dollar symbol identifies a currency; assume tax status; or reuse unverified exchange rates silently.
- Substitute an unrelated image, alter the product shown, or claim an image is visible merely because media exists inside an `.xlsx` package.
- Overwrite the template or any previously delivered file.
- Discard dropdowns, hidden support sheets, relationships, formulas, external links, data models, or connections without disclosure.
- Report a check as **PASS** when only part of the check was completed.

## 2. Determine operating mode

The two modes are separate. State the mode at the top of the proposal and the QC report, and never carry training assumptions into a real-supplier task.

### A. REAL SUPPLIER MODE

Prepare a genuine commercial opportunity. The lot-specific supplier, warehouse location, SKU, actual quantities, packing, number of pallets, costs, clearance proposal, and NOZ response must come from lot evidence, direct supplier communication, or explicit informed user confirmation. Catalogue pages are evidence only of publicly displayed product information, not of the actual lot. Leave unsupported fields missing and flag them; a user-requested provisional estimate must be unmistakably labelled and must not masquerade as confirmed inventory.

### B. TRAINING MODE

Prepare a fictional or simulated lot. Product images and attributes may be sourced from real websites, but stock, packing, references, offer terms and prices are **hypotheses until approved**.

- **Proactive proposal:** Research all reasonably available attributes; propose missing commercial and logistics inputs in one table. Label each proposed fact `[A — PROPOSED]`, source-backed product facts `[V — VERIFIED]`, unresolved data `[M — MISSING]`, and inconsistencies `[C — CONFLICT]`. Do not ask the user for information you can research or sensibly propose.
- **No unapproved defaults:** A placeholder reference such as `TRN-SUPPLIER-001`, "Prospect", "Overstocks", "Global", one unit per carton, or any price or pallet amount is a *suggestion*, never an automatic approved fact.
- **No universal percentage pricing:** Wholesale and clearance prices should preferentially come from the user or a stated hypothetical source-currency or EUR amount. If a percentage-of-retail training model is proposed, disclose the percentage, tax basis, and dependency, and obtain explicit approval. Fixed percentages used in any earlier exercise are not NOZ policy and must not be reused as defaults.
- **Physically plausible training logistics:** Do not assume a fixed number of cartons per pallet across products of different dimensions and weights. Inspect dimensions and weight where available; otherwise state clearly that the packing plan is simulated and unverified. Proposed pallet counts must reconcile with the approved lot total.
- Training assumptions must be identified in the proposal and the QC report. Where the workbook has no proper assumption-status field, put the qualifier in appropriate narrative sections or in the external QC register **without corrupting required dropdown values or numeric cells**.

If the mode is genuinely unclear, ask one targeted question while safely researching available product information.

## 3. Inputs, research, and evidence register

Possible inputs: blank CRV template, supplier offer or stock list, invoices or shipment papers, correspondence, supplier website and product URLs, actual product image files, approved-data sheet, a previously approved workbook **supplied in the current task**, and explicit instructions.

**Evidence hierarchy depends on the field:**

1. **Lot facts:** actual supplier lot document → direct supplier confirmation → explicit user-provided facts or approval, appropriately qualified. A catalogue does not prove lot quantities.
2. **Product facts:** exact manufacturer or product listing, or technical sheet → matching supplier listing → credible secondary reference, labelled as such.
3. **Public retail prices:** dated, region-specific product page with confirmed source currency, regular/sale distinction, and tax status.
4. **Training assumptions:** separately approved. They are *not* source-backed facts.

### 3.1 Supplier domain and website verification (mandatory before any product research is trusted)

The domain or URL the user names may not be the supplier's real site. Verify it before using anything from it.

1. **Fetch the exact URL given.** Record the final URL, the redirect chain, and the date checked.
2. **Detect parked or for-sale domains.** A redirect to a domain marketplace, registrar "for sale" page, parking page, advertising page, or an unrelated business means the named domain is **not** the supplier's site. Do not use that page as evidence.
3. **Check for the real site.** Search for the company name; look at alternative top-level domains (`.com`, `.ca`, `.co.uk`, `.eu`, `.ro`, and so on), country subdomains, and separate store domains. Confirm identity using at least two signals: legal or trading name, address, phone, about page, branding, product range, social profiles.
4. **Identify regional or sister stores.** One brand may operate separate stores per country with different currencies, models, voltages, colours, prices, tax display, shipping regions and stock. Identify which store the user means, which one you used, and why. Do not mix facts from two stores for one product.
5. **Establish currency from evidence, not symbols.** Use store metadata, a currency selector, cart/checkout, a currency code in page data, or an explicit statement. A bare `$`, `£` or `kr` is not currency evidence. If two stores of the same brand use different currencies, report both and use only the one tied to the supplier the user intended.
6. **Establish tax display:** price including tax, excluding tax, "taxes extra", or unspecified. Record the exact wording.
7. **Never silently replace the named supplier.** If the user's domain is wrong, say so, name the site you used instead, and list the discrepancy in the exceptions register for the approval gate. The user confirms the supplier identity; you do not decide it.
8. **Do not trust your own search terms.** An assumed model attribute (for example a voltage) can be wrong. Take attributes only from the matched listing.
9. If the supplier's site cannot be verified, mark every product fact from it `[C — CONFLICT]` or `[M — MISSING]` and continue only with clearly qualified information.

### 3.2 Product, image, price and rate research checklist

- **Match an uploaded image to its product through multiple signals:** appearance, colour/variant, model, image filename or ID, photos on the page, technical description, and supplier confirmation where possible. Filename or visual resemblance **alone** does not establish a match. An unmatched user image remains flagged rather than replaced without approval.
- Check technical details against the actual matched model: voltage, motors, battery, age, weight/load rating, dimensions, remote control, colour, and so on. Omit unsupported attributes.
- Treat conflicting "Sold Out" and "Add to cart" labels as an unresolved website-status conflict, not lot availability.
- Record source website, exact product URL, observed regular price, promotional price when relevant, currency evidence, tax basis, and date checked.
- Verify official exchange-rate data when required. If only a secondary citation of the official source is reachable, disclose it and classify official verification as NOT VERIFIED.
- Never assume another model or chat still has previously uploaded files; check the current attachments and explicitly identify any missing artifact.

Maintain a field-level evidence register:

| Field / row | Proposed value | Classification `[V]/[A]/[M]/[C]` | Evidence or approval source | Caveat |
|---|---|---|---|---|

## 4. Inspect the actual workbook BEFORE applying any map

**The attached workbook is the authority.** Verify sheet names and order, hidden state, cell locations, dropdown sources, named ranges, merged cells, styles, widths and heights, existing drawings, XML namespaces, print areas, and package parts in the supplied template before editing. For a changed template version, build a fresh map; never write into assumed cells.

Some workbooks include external links, connections, a data model, `customXml` content, `calcChain`, named ranges, printer settings and extended (`x14`) data validation. **Detect their presence; do not presume them or invent missing parts.**

The verified map of one inspected template (`Modele CRV GOL.xlsx`) is in **Appendix B**. It is a **template-specific example and a starting hypothesis, not a universal guarantee**.

**Additional Information (general rule):** Standard NOZ guidance groups this content into four thematic subjects: (1) supplier status and company; (2) lot origin and need; (3) NOZ response and type of offer; (4) logistics and extras. A given template may not have one box per subject. Inspect the actual prompts, their numbering and the merged areas in the supplied workbook; place each answer under its matching actual prompt; account for every prompt, and show the proposed mapping at the approval gate when it is not obvious. Do not assume the number of boxes or prompts.

**Print settings:** Inspect print areas. One inspected template had print areas that did not cover the data rows (see Appendix B). Handle print settings intentionally and disclose any change. **A print-area change does not by itself fix worksheet drawing visibility.**

Preserve actual sheet names and order, hidden sheet status, values, merged ranges, formatting, widths and heights, conditional formatting, validations (standard and extended), defined names, formulas, comments, external links, connections, model and unknown workbook parts wherever present.

## 5. Batch Information and Additional Information

Fill all 18 Batch fields according to evidence or **approved** training assumptions. Use **exact** valid dropdown text found in the current template; never place `[A]` markers inside fixed-choice cells.

- Do not confuse mixed **carton packing** with mono-product **pallet organisation**; these can coexist.
- Use `Yes / Registered` (or the equivalent) only with evidence of official licensing or as an explicitly approved training assumption, flagged as simulated.
- A shop or showroom address is **not** evidence of the actual pickup or stock location. Use it as a training stand-in only when approved. Real mode: request the actual warehouse or collection address.
- `Batch total pallets = SUM(P for all included references)`; verify before and after saving.
- Keep intentionally inapplicable items blank and record why.
- Distinguish **supplier expectations** (for example Global) from the **NOZ response**; do not infer one from the other.

**Additional Information content:** follow the actual prompts per §4. Never invent a real offer, past purchase or supplier motive. In real mode, unsupported statements stay missing. For battery-powered stock, flag battery transport and handling details when they are needed and not supplied.

## 6. Supplier's Listing — frozen A:P rules

| Column | Mandatory treatment |
|---|---|
| **A — Visual** | Embed the actual matched product image supplied by the user or verified from the product page; never a generic substitute. Fit it visibly within its row. Keep a product/variant match register. |
| **B — Supplier Reference** | Genuine lot reference if provided. If missing in real mode, flag it; a training placeholder only after approval. |
| **C — Supplier's Designation** | One accurate, concise product description from the matching source (product type, key technical attributes, variant), omitting unknown facts. **Column D must contain exactly the same text (rule 6.1).** |
| **D — NOZ Designation** | **Exact copy of column C**, character for character. No separate shorter or "saleable" wording (rule 6.1). |
| **E — Colour(s)** | **Exactly** `As per visual` in every populated reference row. |
| **F — Measure Units** | Actual confirmed or approved unit (`Box`, `Piece`, etc.). |
| **G — Brand / License** | Actual brand or licence, not automatically the supplier name. Mark product-line names provisional in the QC report; leave blank if unapproved. |
| **H — BIUB/BBD** | Blank when not applicable, otherwise a supported date. |
| **I — Untaxed (Wine)** | Blank when not applicable, otherwise a supported value. |
| **J — Qty Available** | Real Excel formula `=N{row}*O{row}*P{row}` **with a cached result** equal to the multiplication. Preserve the formula so Excel recalculates. |
| **K — Wholesale Unit Price** | Numeric EUR only, two-decimal display, no `€` character. Source or user-approved estimate. |
| **L — Clearance Unit Price** | Numeric EUR only, two-decimal display, no `€` character. Source or user-approved estimate. |
| **M — Regular Retail incl. Tax** | Numeric EUR only, regular retail price with documented currency and tax method; do not use the sale price unless approved. |
| **N — Units per Package** | Numeric, real lot data or approved training quantity. |
| **O — Packages per Pallet** | Numeric, real lot data or approved training quantity. |
| **P — Number of Pallets** | Numeric; the sum over the included references must equal the Batch total. |

### 6.1 Designation rule: column C = column D

- **Standing rule:** for every populated reference row, the **Supplier's Designation (C) and the NOZ Designation (D) contain the identical text.** Write one description, then copy it unchanged into both cells.
- Write that single description so it reads well as the NOZ designation: concise, accurate, with the distinctive verified attributes (product type, brand or licence if verified, voltage or size, key technical features, variant) and nothing unsupported.
- **It must be fully visible.** Check that the whole text shows inside the cell at the template's row height and column width, without being cut off. If it is clipped, shorten the text; do not change row heights or column widths unless the user approves. As a guide, a description of roughly 200–250 characters fit the visible area of the one inspected template (Appendix B); verify for each workbook.
- Both cells show the same text in the proposal at the approval gate and in the QC report. QC (§10C) compares C and D for every row.
- Any exception (for example a supplier text in another language that NOZ wants translated) requires the user's explicit approval and is recorded in the exceptions register.

For any row with genuinely unknown N, O or P in real mode, do not invent a credible-looking J quantity. Flag the unresolved components and explain that the formula cannot produce a trustworthy count until they are supplied. Do not quietly type zero as if it were actual stock.

## 7. Prices, currency and tax — dependency rules

1. Determine source **currency explicitly** from store or supplier information (§3.1); do not identify currency from `$` alone.
2. Distinguish regular from promotional pricing and whether displayed prices include sales tax. Do not apply tax twice.
3. Determine and document the applicable region, tax rate, and whether the method adds tax before conversion. In training mode, propose these as `[A — PROPOSED]`; do not apply any one region's tax universally.
4. For conversion via BNR: `EUR = SourceAmount × (SourceCurrency/RON) ÷ (EUR/RON)`. Select the correct approved date, use official published rates where possible, record links and timestamps, and compute with decimal arithmetic. Use consistent rounding to two decimals; recalculate the output independently.
5. **K, L and M are separate commercial fields.** Their dependency varies with the **approved price methodology**:
   - If K and L are independently supplied wholesale or clearance prices, a change in retail tax affects **M only**, not K or L.
   - If K and/or L are expressly calculated as a percentage of *tax-inclusive M*, changing tax can change the corresponding amount; report this before recalculating.
   - If K/L are based on pre-tax retail, fixed source-currency quotes, or other approved references, follow *those* dependencies instead.
   - An exchange-rate change affects only fields whose approved source prices require that conversion.
6. Never use a fixed percentage margin as a default business rule. In training mode offer illustrative pricing options and request approval of one option, with source amounts and units.
7. If the tax basis, currency or exchange rate remains unverified, flag the commercial accuracy as `NOT VERIFIED`; arithmetic equality alone is not documentary validation.

## 8. Consolidated proposal and approval — before Excel changes

Research the **whole batch** first. Present one clearly labelled package:

1. **Supplier identity and domain verification result** (§3.1), including any discrepancy with the domain the user named.
2. **Batch Information:** the proposed 18 fields with exact dropdown values and source/assumption labels.
3. **Additional Information:** text mapped to the workbook's actual prompts, with assumed commercial statements clearly separated.
4. **Supplier's Listing:** all product rows A:P (image match, descriptions, SKU, unit, brand, formula-derived units, EUR prices, packaging, pallets), including the currency and tax calculations and the price method.
5. **Exceptions register:** missing source documents, image mismatches, uncertain brands or specs, unknown shipment facts, conflicting catalogue claims, tax or currency uncertainties, proposed training numbers, intentional blanks.
6. **Reconciliation:** sum of P, expected sum of J, and evidence status.

Request **one consolidated approval**. If only specific fields change afterwards, update their dependents and show a concise difference, preserving previously approved fields. **Do not edit Excel until that approval.** An authorization to *prepare* a proposal is not permission to change the workbook.

## 9. Safe Excel editing and image insertion — template-adaptive

**Select the editing technique only after template inspection.** For complex workbooks with extended validations, data models, connections, external links and unknown XML parts, **surgical OOXML ZIP-part editing is often safer** than whole-workbook serialization. A library may be used read-only to inspect. Do not assume XML editing is always the safest route, and do not assume that any particular drawing part, image filename or row height exists; verify the actual package architecture.

**If OOXML part editing is appropriate:**

1. Make a new output from the original, preserving unrelated ZIP parts, names, content types and relationships. Compare unchanged parts against the source. Handle namespace prefixes and XML structure correctly.
2. Write strings, numbers, styles and formulas to the **observed** cell addresses with appropriate XML structures. Do not delete existing attributes or unrelated cell content.
3. For quantities, store both the formula XML (`<f>N2*O2*P2</f>`, without a leading `=` in OOXML) and an accurate cached numeric `<v>`; repeat by row with the actual approved values. Set appropriate recalculation flags without destroying caches.
4. For prices use numeric values and correct number formats (usually `0.00`); extend styles safely by adapting existing compatible styles, not by blindly assuming an index is free.
5. **Images:** convert uploaded WebP or other incompatible types into a widely compatible format (typically PNG) without changing visual content. Inspect whether the target sheet **already has drawings or relationships**, then safely create or update the media files, the drawing XML, the drawing relationship part, `[Content_Types].xml`, the worksheet drawing reference, unique drawing shape IDs and suitable anchoring. Preserve aspect ratio; calculate offsets from the actual column width and row height; ensure each image is visible in its own row.
6. Preserve sheet order, hidden support sheets, validation, merging, external parts, named ranges and other template features. If preservation is not possible, flag the limitation rather than declaring success.
7. **Print settings are separate from worksheet display.** Inspect and, if necessary, propose or approve updating print areas so all relevant rows can print. Updating a print range is **not** a fix for a missing floating image in Excel's normal worksheet view.
8. Save to a distinct filename; never overwrite the original or a prior output.

**If a workbook editor is instead proven to preserve all existing features**, it may be used. Re-check the resulting workbook against the original rather than relying on assumptions about the tool.

Appendix C lists implementation examples from one template. They are optional aids, not mandatory steps.

## 10. Post-save quality control (mandatory)

**Open and inspect the exact file being delivered**, not only an intermediate or modified working copy. No claim of full verification may rest on a modified or post-processed render.

### A. Workbook/package preservation

- ZIP integrity passes; all XML parts that were touched parse.
- Expected worksheets and their exact order and hidden state preserved.
- Expected merge ranges, formulas, style references, validations (including extended `x14`), dropdown options, defined names, external links, model, connections and other preserved components match the original, except explicitly approved changes.
- Record changed, added and removed parts, and identify byte-for-byte unchanged source parts when that comparison is available.
- All entered dropdown values are actual members of their lists.

### B. Images — three distinct checks

1. **Binary/media integrity (package check):** expected image count; each embedded media payload is nonzero and decodes; it matches the approved input photograph after any format conversion; no unintended duplicate or substitution.
2. **Drawing integrity (structural check):** worksheet drawing pointer → drawing XML → relationship → correct image file; unique IDs; correct source-to-row association; correct anchors and sizes; visible placement within the proper column A product row.
3. **Display verification (visual check):** open or render the **unmodified delivered file** with an image-capable spreadsheet viewer and inspect the worksheet itself. Inspect print and print preview **separately**. A print area that omits rows can make a print-based renderer look empty even when worksheet pictures are valid. Some web and mobile previews, and some in-app file panes, ignore floating drawings. **Mark worksheet display `PASS` only when it was actually viewed in a renderer that supports those drawing objects.** If desktop Excel was not available, state `Desktop Excel visual/open test NOT VERIFIED` even if an alternative compatible viewer was used.

If pictures do not appear for the user, investigate the viewer's support **and** the OOXML relationships and anchors before altering the saved file. Do not call pictures valid solely because they exist inside the ZIP, and do not claim a specific cause you could not reproduce.

### C. Values, formulas, currency and totals

- Confirm every approved cell's actual stored value and type, including deliberate blanks.
- Every J formula multiplies its own N, O and P cells; independently compute and compare the cached results.
- Reconcile total available units, the sum of P and the Batch pallet count; flag differences explicitly.
- K/L/M are numeric EUR cells displayed to two decimals; confirm no literal currency symbol and no errors; verify derivations against the documented approved sources and rates.
- Confirm Additional Information sits under the correct numbered prompts, not merely in some similarly sized merged box.
- Confirm that column C and column D are identical in every populated row (§6.1) and that the full text is visible in the cell, not clipped.

### D. Text, font and print caveats

- If a headless render substitutes missing fonts or shows `###`, separate **value correctness** (checked via cell data) from **visual legibility** (not necessarily verified). Never infer that the workbook will look right in desktop Excel merely because the XML values are correct.
- If full print coverage is required, verify that the delivered file's **actual** print areas cover the intended reference rows and Batch content. List any print-area changes as intentional.
- If desktop Excel was not used, state exactly: **"Desktop Excel visual/open test not performed."**

**Valid QC statuses:** `PASS`, `FAIL`, `NOT VERIFIED`, `NOT APPLICABLE`. Split a partial pass into separate checks; never hide a failure in an overall green label.

## 11. Versioning, delivery and report

Always create a new `.xlsx` with a distinct filename (for corrections use `_v2`, `_v3`, and so on), preserve old versions, and deliver a paired QC report (`.md`). When fixing an existing output, patch the existing approved output *unless doing so would damage template fidelity*, and record which package parts were changed. Never silently revert approved content to an earlier state.

**The QC report must provide:**

- Input files actually received, model and tool limitations, inspection date, operating mode.
- Supplier domain verification result, store/region used, currency evidence, and any discrepancy with what the user named.
- Approved reference count, embedded image count, per-image source match, and the three-part image QC.
- Batch fields, narrative mapping and provenance/assumption status.
- The J formula list, cached totals, sum of P, and the Batch pallet count.
- Each pricing method, source currency, tax basis, rate date, cited exchange-rate provenance, arithmetic checks, and unresolved verification.
- Template fidelity checks: validations, hidden sheets, formulas, styles, relationships, external links, connections and model, print settings.
- Clear `PASS` / `FAIL` / `NOT VERIFIED` / `NOT APPLICABLE` statuses and outstanding actions.
- Changes from the immediately preceding output, and a clear statement when desktop Excel was unavailable.

If there is a critical `FAIL` (missing required picture, corrupt image payload, broken formula, wrong pallet or quantity count, lost validation, or unusable workbook), attempt to repair and rerun the checks before delivery. If it is still unresolved, deliver only with a prominent failure disclosure and do **not** claim completion.

## 12. Start-of-chat execution procedure

1. Identify which attachments and URLs are **actually accessible in the current task**.
2. Establish REAL SUPPLIER or TRAINING mode; build the field-level evidence register.
3. Inspect the workbook layout and unusual Excel parts; verify (do not assume) any reference cell map.
4. **Verify the supplier domain and store (§3.1)**; then verify exact product and image matches; extract sourced technical facts and dated regular retail prices with currency and tax basis.
5. Prepare the **complete batch proposal** and one exceptions/assumptions register; obtain one consolidated approval **before** editing.
6. Build a new output safely using the actual template's structure.
7. Reopen the exact saved output; audit package, data, formulas, images, print settings and display; write the QC report.
8. Deliver validated files. Handle corrections as clearly versioned updates, never by overwriting originals.

### New-task intake checklist

- [ ] Workflow file and the supplied original blank CRV template
- [ ] Operating mode confirmed
- [ ] Supplier identity; named domain verified (not parked, redirected, or a different regional store); real lot evidence or training scenario
- [ ] Store/region and source currency evidence recorded
- [ ] Product list or links, and supplied product images individually matched
- [ ] All 18 Batch inputs, or intended blanks, or approved proposed assumptions
- [ ] Additional Information mapped to the workbook's actual prompts
- [ ] Source currency, regular retail price, tax basis, applicable rate date
- [ ] K/L price sources or an explicitly approved training model
- [ ] N/O/P packaging facts or explicitly approved hypothetical values
- [ ] Pallet total reconciled; actual warehouse or approved simulated location
- [ ] Full proposal and exceptions approved once
- [ ] Reopened output QC performed; report lists remaining unverified tests

---

## Appendix A — Reusable exceptions register

| Location / field | Proposed value | Status `[V]/[A]/[M]/[C]` | Source / approval | Next action |
|---|---|---|---|---|
| Example: B7 | `TRN-EXAMPLE-006` | `[A — PROPOSED]` | Training proposal only | Await batch approval |

## Appendix B — Verified reference map of one template (`Modele CRV GOL.xlsx`)

**Template-specific example. Verify every item against the supplied workbook before use; do not treat it as a universal layout.**

**Package:** sheets `Supplier's Listing`, `Batch information`, and a hidden `Données` sheet holding the dropdown source lists (labels switch with `Batch information!A1` = `en`). Also present: an external link, connections, a data model, 20 `customXml` parts, `calcChain`, defined names, printer settings, and mostly extended (`x14`) dropdown validations (one standard validation, on C28, using the named range `Paletise`).

**Batch information input cells** (values in merged `C:F`):

| Cell | Field | Allowed values / type |
|---|---|---|
| C2 | Supplier Name | Text |
| C4 | Origin of Lot | End of line; End of collections; Short dates; Cancelled order; Wine Tank residue; Bankruptcy; Store returns; Second Choice; Damaged goods; Overstocks; Delisting; Transport damage |
| C6 | Supplier's Expectation | Global; Global / Ref; Best Price |
| C8 | Stock Year | Text / year |
| C10 | Brands / Licenses | No; Yes / Unregistered; Yes / Registered |
| C12 | Samples | Yes; No |
| C14 | Translation | Yes; No |
| C16 | Concurrence | Yes; No |
| C18 | If Concurrence | Text / blank |
| C20 | Packing Details | Per size; Per color; Mixed; Bulk |
| C22 | Package | Yes; No |
| C24 | Number of Pallets | Number |
| C26 | Palletized | Yes; No |
| C28 | If Palletized | Bulk; Mixed; Mono produits |
| C30 | Shared Order | At The Reference; At Volume; Not sharable |
| C32 | City / Country | Text |
| C34 | ZIP Code | Text |
| C36 | Reply Notice | Call Offer; Usual; Urgent |

**Additional Information layout (verified in this template):** **four merged areas** hold **seven numbered prompts**:

| Merged area (top-left cell) | Numbered prompts it contains |
|---|---|
| H3 (merged H3:N10) | 1. Supplier status; 2. Description of the company |
| H11 (merged H11:N20) | 3. Origin of the batch; 4. Need |
| H21 (merged H21:N31) | 5. Our response; 6. Type of offer (global, global à la ligne, partial, etc.) |
| H32 (merged H32:N39) | 7. Extras + other details / restrictions / packaging about the batch |

The four thematic subjects of §4 map onto these areas as: company → prompts 1–2; origin and need → prompts 3–4; NOZ response and offer type → prompts 5–6; logistics and extras → prompt 7. Keep the template's own prompt text and numbering in each cell. Another template version may differ; always inspect.

**Supplier's Listing layout:** row 1 headers; data from row 2; tall product rows (row height 153.6 pt); column A about 39 characters wide; columns H (BIUB/BBD) and I (Untaxed Wine) hidden; header N "Packing details", O "Nb packets / pallet", P "Number of pallets".

**Print areas in this template:** Listing `A1:P1` (header row only) and Batch `A1:O24` (stops before the lower Batch fields and the Extras box). Both need an explicit decision and disclosure.

**Other:** `Batch information` column O contains helper formulas whose cached values ship empty.

## Appendix C — Template-specific implementation examples (verify before use)

These steps worked on the GOL template when editing the `.xlsx` package directly. They are **examples, not mandatory instructions**: another workbook may need different handling. Inspect first, then adapt, and re-run the §10 checks.

1. **Inline strings.** New text cells can be written as `<c r="B2" s="23" t="inlineStr"><is><t xml:space="preserve">text</t></is></c>`, keeping the cell's existing style index. This avoids editing `sharedStrings.xml`. Escape XML characters.
2. **Numeric price format.** To show `0.00`, append a new `cellXfs` entry cloned from the existing price-cell style with `numFmtId="2"` (and `applyNumberFormat="1"`), update the `count` attribute, and apply the new index to the K/L/M cells. Store prices as plain numbers (no `€`).
3. **Formulas with cache.** J cells: `<c r="J2" s="33"><f>N2*O2*P2</f><v>24</v></c>` with the cached value equal to N×O×P.
4. **Pictures (when the sheet already has a drawing part).** Keep any existing template shape (the GOL Listing drawing contained a hidden rectangle). Add one picture anchor per row. A cell-bound form that worked: `<xdr:twoCellAnchor editAs="oneCell">` with `from` and `to` both inside the intended column A cell and row; declare `xmlns:r` once on the drawing root; give each picture a unique `cNvPr id` and a descriptive `descr`; reference the image with `r:embed`. As a sizing example, a picture of about 190 × 190 px centred in a cell of about 279 × 205 px (derived from column width 39.1 characters and row height 153.6 pt) fitted fully inside; recompute for every workbook.
5. **Drawing relationships.** The GOL Listing drawing had **no** relationship file at first; the file `xl/drawings/_rels/drawing1.xml.rels` had to be created with one `image` relationship per picture, targeting `../media/imageN.png`. Check whether the relationship part exists before creating it.
6. **PNG content type.** Add `<Default Extension="png" ContentType="image/png"/>` to `[Content_Types].xml` if no PNG default exists.
7. **Image preparation.** Convert the uploaded WebP files to PNG from the originals; confirm nonzero size and that each decodes; compare with the source image.
8. **`fullCalcOnLoad`.** Because helper formulas in `Batch information` column O shipped with empty cached values, `<calcPr … fullCalcOnLoad="1"/>` in `xl/workbook.xml` makes Excel recalculate them on open. Verify that this is appropriate for the workbook at hand and that J's cached values remain.
9. **Print area.** In `xl/workbook.xml`, the Listing `_xlnm.Print_Area` defined name was widened from the header row to the data rows so print-area-based viewers show them. Disclose any such change. It does not by itself make floating pictures visible in Excel's normal view.
10. **Package handling.** Rewrite the ZIP with the original entry order and entry attributes; replace only changed parts; list changed, added and byte-identical parts in the QC report. A spreadsheet library that re-saves the whole workbook can drop extended validations, the data model and connections, so treat that route as unsafe unless proven by comparison.
11. **Verification trap.** Rendering a *modified* copy (for example one with a widened print area) can show pictures that the delivered file does not show. Always render the delivered file unmodified.

## Appendix D — QC report skeleton

| Check | Status | Evidence / limitation |
|---|---|---|
| Supplier domain, redirect and store/region verification | | |
| Workbook opens / ZIP integrity | | |
| Sheets, order, hidden support data | | |
| Dropdowns (standard and extended) | | |
| Connections, model, external links | | |
| Images: nonzero, decode, source matching | | |
| Images: drawing relationships and anchors | | |
| Images: worksheet visual display (unmodified file) | | |
| Print area and print preview | | |
| J formulas and cached values | | |
| K/L/M numeric values and price method | | |
| Batch/Listing pallet reconciliation | | |
| Additional Information prompt mapping | | |
| Column C = column D in every row; text fully visible | | |
| Desktop Excel open/visual test | | |

## Appendix E — Case lessons (illustrative only; contains no reusable values)

These are patterns observed in earlier exercises. They illustrate the rules above and are **not** rules, data or approvals for any new case.

- A domain named by the user redirected to a for-sale page; the real supplier operated on a different top-level domain, and a sister store in another country used a different currency and different models. Each of these was found only by verifying the domain, as §3.1 requires.
- A voltage assumed during searching turned out to be wrong for the matched product; the attribute had to be taken from the matched listing.
- One user-supplied image could not be located on any product page and was flagged instead of being silently replaced.
- Pictures were present in the package but invisible in a print-area-based render of the delivered file; a render of a modified copy had given a false PASS. Display in desktop Excel was never verified, which is why the QC report must say so.
- An in-app file preview pane showed cell values and fills but not floating pictures; the user's desktop view differed.
- Fixed pricing percentages and per-product pallet quantities used in one training exercise were case-specific approvals and must not become defaults.
- A product-line name was used as a provisional brand only after the user chose that option.

**END — NOZ CRV UNIVERSAL MASTER WORKFLOW V1.4 (DRAFT, NOT FROZEN).** The document guides AI work; it does not authorize fabricated commercial facts, unapproved training assumptions, or unverified QC claims.
