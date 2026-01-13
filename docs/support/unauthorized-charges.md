# Unauthorized Charges (Refund + Payment Method Removal)

## Customer-facing reply template (copy/paste)

Subject: Urgent: Unauthorized charges — refund and payment method removal

Hello,

Thank you for reporting this — I’m sorry for the stress this has caused.

I’ve escalated your case for an urgent billing review. We will:

- Issue a **full refund** for the unauthorized charges once the review confirms
  they were not authorized.
- **Manually remove all saved payment methods** from your account (since you’re
  unable to remove the debit card via self-serve).
- Confirm in writing that **no further charges** will occur.

To help us locate the exact transactions quickly, please reply with:

- The **date/time** you see for each charge and the **amounts**
- The **last 4 digits** of the card charged
- The **country** and **currency** shown on your statement (if available)
- The account email to investigate: `<customer_email>`

Important safety step (recommended):

- If you believe your card details may be compromised, please contact your bank
  immediately to **block the card and dispute the charges**, and consider
  rotating any passwords reused elsewhere.

We’ll update you as soon as the refund is processed and the payment methods are
removed.

Sincerely,
Support Team

## Internal checklist (do not send to customer)

### 1) Triage and verification

- Confirm the request is coming from the account owner:
  - Use your standard account verification steps (do not request full card
    numbers or sensitive bank details).
- Capture ticket metadata:
  - Customer email: `<customer_email>`
  - Date of report: `<report_date>`
  - Amounts reported: `<amounts_reported>`

### 2) Identify and freeze charge sources

- Review billing events for the account:
  - Charges, invoices, subscriptions, payment intents/authorizations
- Cancel all active subscriptions (if not already canceled).
- If your billing provider supports it, set the customer/payment profile to:
  - No future off-session charges
  - No active mandates/authorizations

### 3) Payment method removal (manual)

Self-serve removal may be blocked by:

- An active subscription
- A pending invoice
- A payment method set as default for an open invoice
- A dispute/chargeback workflow holding the payment method

Actions:

- Remove default payment method from the customer profile.
- Detach/delete all saved payment methods from the customer profile.
- Ensure no “backup” payment method remains.
- Confirm UI now shows no saved payment methods (if applicable).

### 4) Refund processing

- Determine which events are refundable (captured charges vs. authorizations).
- For captured charges:
  - Issue refunds for all unauthorized captured transactions.
  - Ensure you refund the exact amounts charged (including any add-ons/fees
    collected by your system).
- For authorizations only:
  - Cancel/void authorizations where possible, and communicate expected release
    timeframes.

### 5) Confirm “no further charges”

- Verify:
  - No active subscriptions
  - No pending invoices with auto-collection enabled
  - No saved payment methods
  - No scheduled jobs that can trigger off-session charges

### 6) Close-out communication

Send customer confirmation including:

- Refund confirmation (amounts + status + expected timeline)
- Confirmation that all payment methods were removed
- Confirmation that subscriptions are canceled and no future charges will occur

## Common pitfalls

- Refunding only the primary invoice while missing add-on charges
- Leaving a backup payment method attached
- Canceling subscriptions but leaving auto-collection enabled on an open invoice

