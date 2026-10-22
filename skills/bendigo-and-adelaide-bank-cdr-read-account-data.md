---
name: cdr-read-account-data
description: As an accredited CDR data recipient with the customer's consent, read Bendigo and Adelaide Bank account data through the Consumer Data Standards banking endpoints. This covers accounts, balances, transactions, direct debits, scheduled payments, instalment plans and payees.
api: openapi/bendigo-and-adelaide-bank-banking-accounts-api-openapi.yml
operations: [listBankingAccounts, getBankingAccountDetail, listBankingBalancesBulk, listBankingBalancesSpecificAccounts, getBankingBalance, listBankingTransactions, getBankingTransactionDetail, listDirectDebits, listDirectDebitsBulk, listDirectDebitsSpecificAccounts, listScheduledPayments, listScheduledPaymentsBulk, listScheduledPaymentsSpecificAccounts, listInstalmentPlans, listInstalmentPlansBulk, listBankingPayees, getBankingPayeeDetail]
---

# Read consented CDR account data (Bendigo and Adelaide Bank)

**Not open to general agents.** These operations require CDR accreditation, an active customer consent
with the right scopes, FAPI 1.0 Advanced security and MTLS to the data holder's secure host. The specs give only
the Consumer Data Standards placeholder server `https://mtls.dh.example.com/cds-au/v1`. Find the real
endpoints in the CDR Register. Do not guess them.

## Headers (all operations)
- `x-v` (required): the endpoint version you request. `x-min-v` is optional.
- `x-fapi-interaction-id`, `x-fapi-auth-date`, `x-fapi-customer-ip-address` and `x-cds-client-headers`: send these as
  the Consumer Data Standards require. Send the last three when the customer is present.

## Steps
1. **Accounts**: `listBankingAccounts` (GET /banking/accounts, filters `product-category`, `open-status`,
   `is-owned`, paged with `page` / `page-size`). Then `getBankingAccountDetail` for one account.
2. **Balances**: `getBankingBalance` for one account, `listBankingBalancesBulk` for all, or
   `listBankingBalancesSpecificAccounts` (POST with a list of account IDs).
3. **Transactions**: `listBankingTransactions` (GET /banking/accounts/{accountId}/transactions), then
   `getBankingTransactionDetail` for extended data.
4. **Direct debits**: `listDirectDebits`, `listDirectDebitsBulk` or `listDirectDebitsSpecificAccounts`.
5. **Scheduled payments and instalment plans**: `listScheduledPayments`, `listScheduledPaymentsBulk`,
   `listScheduledPaymentsSpecificAccounts`, `listInstalmentPlans` and `listInstalmentPlansBulk`.
6. **Payees**: `listBankingPayees`, then `getBankingPayeeDetail`.

## Conventions
- All of these operations are read-only. The POST "specific accounts" variants send a list of IDs and change no data,
  so you can retry them safely.
- Pagination follows the CDS `links.next` / `meta.totalPages` envelope. Follow `links.next` instead of building page URLs yourself.
- Errors use the CDS `errors[]` envelope (`code`, `title`, `detail`). See `errors/bendigo-and-adelaide-bank-error-codes.yml`.
  If the server returns 406 for an unsupported `x-v`, retry with a supported version.

Specs: the banking-accounts, banking-account-balances, banking-account-transactions, banking-account-direct-debits,
banking-account-scheduled-payments and banking-payees files under `openapi/`.
