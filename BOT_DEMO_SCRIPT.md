# TijaPass V6 — BOT / developer demonstration script

**Purpose**: Demonstrate the fintech/accounting concept, risk controls and potential to create better MSME financial records — **not real bank-account access or payment processing**.

**Preparation:** A new browser/device with fictional accounts only. Open the new V6 Netlify website, not the older V4/V5 pages. Select **TFL Admin → Smart Accounting**.

## Demonstration (8–10 minutes)

**1. Brand & language (1 minute)** — Show corrected TijaPass logo and select English, then Kiswahili. Accounting buttons, questions and warnings change language; the other older financing screens are not yet fully translated.

**2. Three ways to capture (1 minute)** — Choose **Guided entry**, **Describe in your words** and **Upload statement**, one at a time. Guided uses simple received/paid, payer/receiver, amount, purpose and payment channel. Narrative supports Kiswahili/English and optional browser speech. Upload accepts any provider's CSV/TSV/basic XLSX format (not live APIs).

**3. Record a straightforward small receipt (1 minute)** — As Customer or TFL Admin, Guided Entry: Money received, Cash, Juma, TZS 20,000, Sale of rice. Submit. Show it is pending review and that TFL posts it only after classification/accounting checks.

**4. Duplicate prevention (2 minutes)** — Choose Upload Statement → Add demonstration transactions. In Review, find the customer-declared sale for 20,000 and the imported 20,000 receipt. Explain that statement movement and an entered sale may be **one underlying business event**. As TFL, use **Match as additional evidence** to link records and avoid posting sales twice. A different valid sale of the same amount should be documented as a separate event, never automatically deleted.

**5. Anomaly escalation (1 minute)** — Examine the TZS 20,000,000 cash receipt against normal amounts. TFL must document why the value is unusual and review corroboration before approval. The prototype cannot independently inspect a real bank or customer identity.

**6. Normal bookkeeping and statements (2 minutes)** — Confirm another complete receipt, pay rent, and post with TFL approval. Show balanced journal, profits, cash flow, business position and trial balance. Explain stock purchases do not necessarily count as cost of sales, owner loans are not sales, and transfers between own accounts should not inflate turnover.

**7. Explain institutional value and next stage (1 minute)** — Customer/business evidence could support lender permissioned access and finance suitability. Next build: secure Supabase authentication, server-owned ledgers, bank-verified data APIs, independent reliability testing, secure receipts, payments through licensed parties and proper regulator-guided pilot.

## Audience questions to anticipate

**Is this real AI?** Not yet. Classification is rules and approved-history assisted; an actual LLM needs secured deployment, eval tests, prompt guardrails and a deterministic booking system.

**Can it read SimBanking/M-Pesa directly?** No. It can import customer-authorised *statement exports* if supplied in a supported format. Direct APIs require a regulated provider agreement and implementation.

**Does the accounting eliminate all errors?** No. It reduces known errors through structured questions, flags, human approval, balanced journals and matching; it cannot guarantee completeness, authentic source documents, correct stock counts or zero fraud.

**Are the financial statements audited?** No. Illustrative management reports from user-declared/approved entries; quality must be independently validated for credit or regulatory use.
