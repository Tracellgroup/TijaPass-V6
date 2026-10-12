# AI classification — safe implementation specification

**What this version does:** transparent phrase/category matching and merchant-description corrections learned from TFL-reviewed entries in browser state; confidence percentages are heuristic labels, not evaluated probabilities.

**Next developer step: an opt-in AI service** (e.g. Google Gemini or an equivalent) behind a Supabase authenticated Edge Function. Do **not** put API keys in Vite frontend variables. Restrict by customer consents, tenant isolation, budgets/rate limits and retention policy.

Input: {customer_id, transaction_id, date, narrative, amount, direction, source_type, currency, redacted_counterparty, supplier_id_if_known, prior_approved_mapping}.

Output strict JSON: {proposed_category, debit_account_hint, credit_account_hint, inferred_counterparty_type, confidence, explanation, needs_clarification, clarification_question, model_version}.

Controls:
1. Allow only chart-of-accounts categories; validate JSON against schema and against deterministic accounting rules.
2. Model must **not** create cash deposits, journal entries or credit approvals; only returns suggestions.
3. Never treat a transfer, owner's money, or a loan as sales without clear supporting evidence.
4. Require TFL human approval for unknown/low-confidence cases or inconsistencies; store before/after reviewer edits for audit.
5. Test with Swahili variations, common Tanzanian merchant descriptions, cash receipts, supplier invoices and messy exports; measure top-1 accuracy, false revenue recognition, duplicate missed rates and calibrated uncertainty on a labelled, consenting test set.
6. Document privacy, localisation/processor data transfer, and model risks before enabling external inference.
7. Always keep deterministic fallback available when the AI service is offline or unaffordable.

Receipt OCR & PDF import should be added via securely managed file-processing pipeline with scanned-document isolation and PII controls, not via public unauthenticated browser endpoints.
