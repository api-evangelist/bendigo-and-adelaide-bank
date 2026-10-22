---
name: up-manage-webhooks
description: Register, test, inspect and remove Up Banking API webhooks, and verify signed transaction events.
api: openapi/bendigo-and-adelaide-bank-webhooks-api-openapi.yml
operations: [postWebhooks, getWebhooks, getWebhooksById, postWebhooksByWebhookIdPing, getWebhooksByWebhookIdLogs, deleteWebhooksById, getTransactionsById]
---

# Manage Up webhooks

Base URL: `https://api.up.com.au/api/v1`, with `Authorization: Bearer <personal access token>`.

## Steps
1. **Create** a webhook with `postWebhooks` (`POST /webhooks`), body
   `{"data":{"attributes":{"url":"https://...","description":"..."}}}`. The 201 response includes
   `secretKey` **only once**. Store it securely.
2. **List or inspect** webhooks with `getWebhooks` (uses `page[size]`) and `getWebhooksById`.
3. **Test** with `postWebhooksByWebhookIdPing`, which sends a `PING` event to your URL.
4. **Debug delivery** with `getWebhooksByWebhookIdLogs`.
5. **Handle events**: Up POSTs JSON events of type `PING`, `TRANSACTION_CREATED`, `TRANSACTION_SETTLED` and
   `TRANSACTION_DELETED`. Reply 200 quickly; Up times out after about 30s and retries with exponential backoff.
   For created and settled events, follow the `transaction` relationship with `getTransactionsById`.
6. **Verify** every event: compute HMAC-SHA256 over the raw request body using `secretKey`, then compare it in
   constant time with the `X-Up-Authenticity-Signature` header.
7. **Rotate or remove**: if `secretKey` is lost, create a new webhook with the same URL, then remove the old one
   with `deleteWebhooksById` (returns 204).

See `asyncapi/bendigo-and-adelaide-bank-up-webhooks-asyncapi.yml` for the event payloads.
