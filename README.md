# TijaPass V6 — Intelligent Accounting & Financial Verification

**TFL-owned product concept / browser demonstration**, extending the original role-based TijaPass V4/V5 ecosystem. TijaPass allows customers, TFL administrators, financial institutions and suppliers to explore finance, wallets, supplier flows, statements and the upgraded accounting workbench.

## V6 changes visible in the application

1. **New responsive, corrected TijaPass branding**, using the two supplied orange/navy logo variants, transparently cropped and aligned. Home/sidebar logos no longer sit inside oversized rectangular screenshots.
2. **English / Kiswahili picker** in the page header, preserved between browser reloads. Core accounting capture, import, review, warnings, status messages and navigation labels are bilingual. **Some existing V4 finance/onboarding/supplier screens are still in English** and need a full translation pass before public rollout.
3. **Three mutually exclusive transaction capture choices** for each transaction: Guided entry, Describe in your words, Upload bank/mobile-money statement. One choice is used at a time, but all feed the same normalised accounting staging queue and then the same balanced general ledger.
4. **Mandatory payment/receipt details**: direction, date, amount, account/channel, payer/receiver, business reason. Recognised walk-in sales can use "Walk-in customers" as the counterparty, rather than inventing a name.
5. **Unclear statements prompt for follow-up**. Each imported line must be confirmed with its business counterparty and reason, even if classification rules confidently propose a label.
6. **Rules-based suggestions in Kiswahili/English**, learned description correction after approved TFL reviews. No external generative AI model is connected; it is not accurate to describe this pilot as autonomous AI accounting.
7. **Unusual-amount warnings** using historical comparisons (e.g. TZS 20m receipt versus a prior maximum of TZS 20k). TFL must explicitly approve the exception, record a meaningful explanation and check supporting evidence.
8. **De-duplication and evidence links**: same-source fingerprint duplicates are skipped; potentially overlapping source entries are held for review. A TFL reviewer can link a second source record to an existing transaction **without posting revenue/expense twice**. Valid separate transactions of identical amounts remain possible after justification.
9. **Source quality clearly differentiated**: customer-entered cash, imported statement exports and internal demo wallet events are never represented as API-verified bank events. Statement import itself does not prove business purpose.
10. **Deterministic double-entry reports** for posted transactions: P&L, balance sheet/business position, cash flow and general ledger, with validation and demo opening balances. Inventory purchase, cost of sales, owner injections, internal transfers and loan-interest splits remain separate accounting categories.
11. Original V4 FI, loan product/pricing, supplier, fee and wallet scenarios remain available in the application. The V6 accounting journal is a **separate demonstration subsystem** and does not yet feed every V4 finance or wallet calculation.

## Five-minute BOT / developer demo

1. Open the **Smart Accounting** page as **TFL Admin**. Use header switch **English ↔ Kiswahili**.
2. Show the three entry cards. **Add demonstration transactions** under Upload statement (they are fictional).
3. Go to **Review & verify**. Compare one small cash sale with a matching imported 20,000 receipt. Fill the imported receipt's payer and purpose, then **Match as additional evidence**; no second sale is posted.
4. Review the TZS 20,000,000 cash receipt and show the mandatory unusual-amount explanation + TFL check. The record cannot be approved until the control conditions are satisfied.
5. Demonstrate a normal entry with payer/purpose and confirm how a TFL-approved transaction appears in **Financial statements → Income Statement / Business Position / Cash Flow / Trial Balance**.
6. Switch to **Customer** to show the layperson review and confirmation steps for statement uploads; then back to TFL for approval.
7. Demonstrate finance readiness, noting the real credit underwriting model is a later integration.

## Quick deployment (GitHub + Netlify)

- Extract the ZIP. Upload **contents of `TijaPass_V6_Intelligent_Accounting/`** directly to a **new GitHub repository**. Do not upload the outer folder itself as one nested folder.
- In Netlify, **Add new project → Import an existing project → GitHub** and choose that new repository.
- Build: `npm run build`; publish: `dist` (already configured in `netlify.toml`).
- Test the new URL in a private browser tab before replacing any older TijaPass version.
- The old browser data is intentionally isolated under the `tijapass-v6-intelligent-accounting` key. Reload should keep V6 demo data **only in the same browser/device**.
- To reset sample data: use the demo reset control under TFL Controls. Do not use actual customer IDs or real bank statements in a public browser-based demo.

## Developer handoff

- `src/AccountingStudio.jsx`: three inputs; staged confirmation; TFL review; duplicate evidence linking; ledger UI; bilingual labels.
- `src/accountingControls.js`: required details, anomaly detection, duplicate candidates, review readiness.
- `src/accounting.js`: deterministic chart of accounts, postings, statements and reconciliation parser.
- `src/v6i18n.js`: English/Kiswahili core interface dictionaries (extend to every remaining screen before public release).
- `src/importers.js`: browser-side CSV/TSV/basic XLSX reader. **PDF and secure OCR are not implemented**.
- `supabase/schema.sql`, `supabase/accounting_v5_upgrade.sql`, `supabase/accounting_v6_upgrade.sql`: **review-only proposed database schemas**, not deployed by uploading this ZIP.
- `V6_IMPLEMENTATION_STATUS.md` and `BOT_DEMO_SCRIPT.md`: acceptance scenarios and production security gaps.
- `tests`: core accounting controls, double-entry examples and source parsing.

## Important production boundary

There is **no genuine multi-user authentication, cloud-backed audit trail, secure transaction posting, external LLM/OCR, actual bank/mobile-money APIs or real payment processing** in this app. Changing roles in the header does **not** authenticate users. The sample TFL wallet TZS 1bn is **fictional demo value, not real funds**. For actual pilot customers, complete the server-owned financial ledger, customer confirmation with secure identity, bank reconciliation, privacy safeguards, RBAC/RLS, independent testing and required regulatory/payment-provider permissions.

## Local development

Node 20+: `npm install`, then `npm run dev`; tests: `npm test`; production bundle: `npm run build`.

The authoring environment could run the pure JavaScript accounting/control tests and TS/JSX syntax checks but **could not obtain the Vite packages from npm**. Verify the GitHub/Netlify build completes successfully before presenting the deployed V6.
