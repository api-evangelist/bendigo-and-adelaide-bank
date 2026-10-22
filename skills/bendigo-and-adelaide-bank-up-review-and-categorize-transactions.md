---
name: up-review-and-categorize-transactions
description: List an Up customer's accounts and transactions with the Up Banking API, then categorize and tag transactions.
api: openapi/bendigo-and-adelaide-bank-transactions-api-openapi.yml
operations: [getUtilPing, getAccounts, getAccountsByAccountIdTransactions, getTransactions, getTransactionsById, getCategories, patchTransactionsByTransactionIdRelationshipsCategory, getTags, postTransactionsByTransactionIdRelationshipsTags, deleteTransactionsByTransactionIdRelationshipsTags]
---

# Review and categorize Up transactions

Up is the digital bank brand of Bendigo and Adelaide Bank. Base URL: `https://api.up.com.au/api/v1`.
Every request needs `Authorization: Bearer <personal access token>`. The token belongs to one customer,
so this skill only works on that customer's own data. An unauthenticated call to `/util/ping` returned 401 when probed on 2026-10-20.

## Steps
1. **Check the token** with `getUtilPing` (`GET /util/ping`).
2. **List accounts** with `getAccounts` (`GET /accounts`), then take an account `id`.
3. **List transactions** with `getAccountsByAccountIdTransactions` (`GET /accounts/{accountId}/transactions`)
   or `getTransactions` (`GET /transactions`) for all accounts. Filters: `filter[status]` (`HELD`/`SETTLED`),
   `filter[since]`, `filter[until]` (RFC 3339), `filter[category]`, `filter[tag]`. You set the page size with `page[size]`.
   Pagination uses cursors: follow `links.next` until it is null.
4. **Fetch one transaction** with `getTransactionsById` (`GET /transactions/{id}`).
5. **Categorize**: list categories with `getCategories` (`filter[parent]` is optional), then call
   `patchTransactionsByTransactionIdRelationshipsCategory` with `{"data":{"type":"categories","id":"<id>"}}`.
   Send `{"data": null}` to remove the category. Success returns 204.
6. **Tag**: list tags with `getTags`. Add tags with `postTransactionsByTransactionIdRelationshipsTags` and remove them with
   `deleteTransactionsByTransactionIdRelationshipsTags`. Both take `{"data":[{"type":"tags","id":"<label>"}]}`
   and return 204.

## Rules
- Errors use the JSON:API format `{"errors":[{"status","title","detail","source"}]}`. Do not retry a 4xx without changing the request.
- PATCH, POST and DELETE on relationships set state, so repeating one with the same body has the same effect.
