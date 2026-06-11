---
name: pagarme-mcp
description: Skill da REST API do Pagar.me na MCP.AI: 80 endpoints em /api/pagarme. Gateway de pagamentos da Stone (api.pagar.me), pedidos, cobranças (cartão, Pix, boleto), clientes e cartões, planos e assinaturas, recebedores (split/marketplace), transferências, recebíveis e faturas, via a API oficial V5. Funciona em todas as versões: chave sk_… usa a API V5 (leitura + escrita); contas legadas (chave ak_…) ganham leitura da API V1–V4 (transações, assinaturas, recebíveis, saldo). Autenticação por chave secreta gerada no painel → Configurações → Chaves. Autentique com workspace API key (sk_live) gerada em app.mcp.ai/settings/api-keys. Use quando o usuário pedir algo coberto pelos endpoints.
---

# Pagar.me — REST API skill

Você tem acesso à **Pagar.me** REST API na MCP.AI.

> Gateway de pagamentos da Stone (api.pagar.me), pedidos, cobranças (cartão, Pix, boleto), clientes e cartões, planos e assinaturas, recebedores (split/marketplace), transferências, recebíveis e faturas, via a API oficial V5. Funciona em todas as versões: chave sk_… usa a API V5 (leitura + escrita); contas legadas (chave ak_…) ganham leitura da API V1–V4 (transações, assinaturas, recebíveis, saldo). Autenticação por chave secreta gerada no painel → Configurações → Chaves.

## Base URL

```
https://api.mcp.ai/api/pagarme
```

Todo endpoint é um **POST** na Base URL + o path abaixo. Os parâmetros vão no corpo JSON.

## Autenticação

Inclua em toda request:

```
Authorization: Bearer sk_live_...
Content-Type: application/json
```

> Gere sua chave em **https://app.mcp.ai/settings/api-keys** (workspace API key `sk_live_…`, não expira, revogável). Uma única chave serve pra todos os seus MCPs.

## Formato de resposta

```json
{ "ok": true, "tool": "<tool_id>", "result": <payload> }
```

## Exemplo cURL

```bash
curl -X POST https://api.mcp.ai/api/pagarme/cards/delete \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{"customer_id":"...","card_id":"..."}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/pagarme/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (80)

#### `pagarme_cards_delete`

Remove um cartão salvo do cliente no Pagar.me V5 (requer customer_id + card_id). Irreversível. _(POST /api/pagarme/cards/delete)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `customer_id` | string | Sim |  |
| `card_id` | string | Sim |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `customer_ids` | string[] | Não | Bulk mode: multiple values for customer_id |
| `card_ids` | string[] | Não | Bulk mode: multiple values for card_id |

#### `pagarme_cards_get`

Cartões salvos de um cliente no Pagar.me V5. _(POST /api/pagarme/cards/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `customer_id` | string | Sim |  |
| `card_id` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `customer_ids` | string[] | Não | Bulk mode: multiple values for customer_id |
| `card_ids` | string[] | Não | Bulk mode: multiple values for card_id |

#### `pagarme_cards_list`

Cartões salvos de um cliente no Pagar.me V5. _(POST /api/pagarme/cards/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `customer_id` | string | Sim |  |
| `card_id` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `customer_ids` | string[] | Não | Bulk mode: multiple values for customer_id |
| `card_ids` | string[] | Não | Bulk mode: multiple values for card_id |

#### `pagarme_cards_write_create`

Criar/renovar cartões de um cliente no Pagar.me V5 (só sk_; requer customer_id). _(POST /api/pagarme/cards/write/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `customer_id` | string | Sim |  |
| `card_id` | string | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `customer_ids` | string[] | Não | Bulk mode: multiple values for customer_id |
| `card_ids` | string[] | Não | Bulk mode: multiple values for card_id |

#### `pagarme_cards_write_renew`

Criar/renovar cartões de um cliente no Pagar.me V5 (só sk_; requer customer_id). _(POST /api/pagarme/cards/write/renew)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `customer_id` | string | Sim |  |
| `card_id` | string | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `customer_ids` | string[] | Não | Bulk mode: multiple values for customer_id |
| `card_ids` | string[] | Não | Bulk mode: multiple values for card_id |

#### `pagarme_charges_cancel`

Cancela/estorna uma cobrança no Pagar.me V5 (requer charge_id; data opcional com amount p/ estorno parcial). Irreversível. _(POST /api/pagarme/charges/cancel)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `charge_id` | string | Sim |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `charge_ids` | string[] | Não | Bulk mode: multiple values for charge_id |

#### `pagarme_charges_get`

Cobranças (charges) no Pagar.me V5. _(POST /api/pagarme/charges/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `charge_id` | string | Não |  |
| `charge_ids` | string[] | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |

#### `pagarme_charges_get_many`

Cobranças (charges) no Pagar.me V5. _(POST /api/pagarme/charges/get/many)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `charge_id` | string | Não |  |
| `charge_ids` | string[] | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |

#### `pagarme_charges_list`

Cobranças (charges) no Pagar.me V5. _(POST /api/pagarme/charges/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `charge_id` | string | Não |  |
| `charge_ids` | string[] | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |

#### `pagarme_charges_summary`

Cobranças (charges) no Pagar.me V5. _(POST /api/pagarme/charges/summary)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `charge_id` | string | Não |  |
| `charge_ids` | string[] | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |

#### `pagarme_charges_write_capture`

Operar cobranças no Pagar.me V5 (só contas sk_; não-destrutivas). _(POST /api/pagarme/charges/write/capture)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `charge_id` | string | Sim |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `charge_ids` | string[] | Não | Bulk mode: multiple values for charge_id |

#### `pagarme_charges_write_confirm`

Operar cobranças no Pagar.me V5 (só contas sk_; não-destrutivas). _(POST /api/pagarme/charges/write/confirm)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `charge_id` | string | Sim |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `charge_ids` | string[] | Não | Bulk mode: multiple values for charge_id |

#### `pagarme_charges_write_retry`

Operar cobranças no Pagar.me V5 (só contas sk_; não-destrutivas). _(POST /api/pagarme/charges/write/retry)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `charge_id` | string | Sim |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `charge_ids` | string[] | Não | Bulk mode: multiple values for charge_id |

#### `pagarme_charges_write_update_card`

Operar cobranças no Pagar.me V5 (só contas sk_; não-destrutivas). _(POST /api/pagarme/charges/write/update/card)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `charge_id` | string | Sim |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `charge_ids` | string[] | Não | Bulk mode: multiple values for charge_id |

#### `pagarme_charges_write_update_due_date`

Operar cobranças no Pagar.me V5 (só contas sk_; não-destrutivas). _(POST /api/pagarme/charges/write/update/due/date)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `charge_id` | string | Sim |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `charge_ids` | string[] | Não | Bulk mode: multiple values for charge_id |

#### `pagarme_charges_write_update_payment_method`

Operar cobranças no Pagar.me V5 (só contas sk_; não-destrutivas). _(POST /api/pagarme/charges/write/update/payment/method)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `charge_id` | string | Sim |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `charge_ids` | string[] | Não | Bulk mode: multiple values for charge_id |

#### `pagarme_customers_get`

Clientes e endereços no Pagar.me V5. _(POST /api/pagarme/customers/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `customer_id` | string | Não |  |
| `address_id` | string | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `customer_ids` | string[] | Não | Bulk mode: multiple values for customer_id |
| `address_ids` | string[] | Não | Bulk mode: multiple values for address_id |

#### `pagarme_customers_get_address`

Clientes e endereços no Pagar.me V5. _(POST /api/pagarme/customers/get/address)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `customer_id` | string | Não |  |
| `address_id` | string | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `customer_ids` | string[] | Não | Bulk mode: multiple values for customer_id |
| `address_ids` | string[] | Não | Bulk mode: multiple values for address_id |

#### `pagarme_customers_list`

Clientes e endereços no Pagar.me V5. _(POST /api/pagarme/customers/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `customer_id` | string | Não |  |
| `address_id` | string | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `customer_ids` | string[] | Não | Bulk mode: multiple values for customer_id |
| `address_ids` | string[] | Não | Bulk mode: multiple values for address_id |

#### `pagarme_customers_list_addresses`

Clientes e endereços no Pagar.me V5. _(POST /api/pagarme/customers/list/addresses)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `customer_id` | string | Não |  |
| `address_id` | string | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `customer_ids` | string[] | Não | Bulk mode: multiple values for customer_id |
| `address_ids` | string[] | Não | Bulk mode: multiple values for address_id |

#### `pagarme_customers_write_create`

Criar/atualizar clientes e endereços no Pagar.me V5 (só sk_). _(POST /api/pagarme/customers/write/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `customer_id` | string | Não |  |
| `address_id` | string | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `customer_ids` | string[] | Não | Bulk mode: multiple values for customer_id |
| `address_ids` | string[] | Não | Bulk mode: multiple values for address_id |

#### `pagarme_customers_write_create_address`

Criar/atualizar clientes e endereços no Pagar.me V5 (só sk_). _(POST /api/pagarme/customers/write/create/address)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `customer_id` | string | Não |  |
| `address_id` | string | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `customer_ids` | string[] | Não | Bulk mode: multiple values for customer_id |
| `address_ids` | string[] | Não | Bulk mode: multiple values for address_id |

#### `pagarme_customers_write_delete_address`

Criar/atualizar clientes e endereços no Pagar.me V5 (só sk_). _(POST /api/pagarme/customers/write/delete/address)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `customer_id` | string | Não |  |
| `address_id` | string | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `customer_ids` | string[] | Não | Bulk mode: multiple values for customer_id |
| `address_ids` | string[] | Não | Bulk mode: multiple values for address_id |

#### `pagarme_customers_write_update`

Criar/atualizar clientes e endereços no Pagar.me V5 (só sk_). _(POST /api/pagarme/customers/write/update)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `customer_id` | string | Não |  |
| `address_id` | string | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `customer_ids` | string[] | Não | Bulk mode: multiple values for customer_id |
| `address_ids` | string[] | Não | Bulk mode: multiple values for address_id |

#### `pagarme_customers_write_update_address`

Criar/atualizar clientes e endereços no Pagar.me V5 (só sk_). _(POST /api/pagarme/customers/write/update/address)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `customer_id` | string | Não |  |
| `address_id` | string | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `customer_ids` | string[] | Não | Bulk mode: multiple values for customer_id |
| `address_ids` | string[] | Não | Bulk mode: multiple values for address_id |

#### `pagarme_invoices_cancel`

Cancela uma fatura no Pagar.me V5 (requer invoice_id). Irreversível. _(POST /api/pagarme/invoices/cancel)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `invoice_id` | string | Sim |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `invoice_ids` | string[] | Não | Bulk mode: multiple values for invoice_id |

#### `pagarme_invoices_get`

Faturas (invoices) de assinatura no Pagar.me V5. _(POST /api/pagarme/invoices/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `invoice_id` | string | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `invoice_ids` | string[] | Não | Bulk mode: multiple values for invoice_id |

#### `pagarme_invoices_list`

Faturas (invoices) de assinatura no Pagar.me V5. _(POST /api/pagarme/invoices/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `invoice_id` | string | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `invoice_ids` | string[] | Não | Bulk mode: multiple values for invoice_id |

#### `pagarme_invoices_write`

Altera o status de uma fatura no Pagar.me V5 (requer invoice_id + status, ex.: 'paid', 'canceled'). _(POST /api/pagarme/invoices/write)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `invoice_id` | string | Sim |  |
| `status` | string | Sim |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `invoice_ids` | string[] | Não | Bulk mode: multiple values for invoice_id |

#### `pagarme_legacy_balance`

Leitura da API LEGADA V1–V4 do Pagar.me (modelo "transactions"). Ativa _(POST /api/pagarme/legacy/balance)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `transaction_id` | string | Não |  |
| `data` | string | Não | JSON com filtros (count, page, status, …) |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `transaction_ids` | string[] | Não | Bulk mode: multiple values for transaction_id |

#### `pagarme_legacy_get_transaction`

Leitura da API LEGADA V1–V4 do Pagar.me (modelo "transactions"). Ativa _(POST /api/pagarme/legacy/get/transaction)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `transaction_id` | string | Não |  |
| `data` | string | Não | JSON com filtros (count, page, status, …) |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `transaction_ids` | string[] | Não | Bulk mode: multiple values for transaction_id |

#### `pagarme_legacy_list_customers`

Leitura da API LEGADA V1–V4 do Pagar.me (modelo "transactions"). Ativa _(POST /api/pagarme/legacy/list/customers)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `transaction_id` | string | Não |  |
| `data` | string | Não | JSON com filtros (count, page, status, …) |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `transaction_ids` | string[] | Não | Bulk mode: multiple values for transaction_id |

#### `pagarme_legacy_list_payables`

Leitura da API LEGADA V1–V4 do Pagar.me (modelo "transactions"). Ativa _(POST /api/pagarme/legacy/list/payables)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `transaction_id` | string | Não |  |
| `data` | string | Não | JSON com filtros (count, page, status, …) |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `transaction_ids` | string[] | Não | Bulk mode: multiple values for transaction_id |

#### `pagarme_legacy_list_plans`

Leitura da API LEGADA V1–V4 do Pagar.me (modelo "transactions"). Ativa _(POST /api/pagarme/legacy/list/plans)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `transaction_id` | string | Não |  |
| `data` | string | Não | JSON com filtros (count, page, status, …) |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `transaction_ids` | string[] | Não | Bulk mode: multiple values for transaction_id |

#### `pagarme_legacy_list_recipients`

Leitura da API LEGADA V1–V4 do Pagar.me (modelo "transactions"). Ativa _(POST /api/pagarme/legacy/list/recipients)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `transaction_id` | string | Não |  |
| `data` | string | Não | JSON com filtros (count, page, status, …) |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `transaction_ids` | string[] | Não | Bulk mode: multiple values for transaction_id |

#### `pagarme_legacy_list_subscriptions`

Leitura da API LEGADA V1–V4 do Pagar.me (modelo "transactions"). Ativa _(POST /api/pagarme/legacy/list/subscriptions)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `transaction_id` | string | Não |  |
| `data` | string | Não | JSON com filtros (count, page, status, …) |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `transaction_ids` | string[] | Não | Bulk mode: multiple values for transaction_id |

#### `pagarme_legacy_list_transactions`

Leitura da API LEGADA V1–V4 do Pagar.me (modelo "transactions"). Ativa _(POST /api/pagarme/legacy/list/transactions)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `transaction_id` | string | Não |  |
| `data` | string | Não | JSON com filtros (count, page, status, …) |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `transaction_ids` | string[] | Não | Bulk mode: multiple values for transaction_id |

#### `pagarme_legacy_list_transfers`

Leitura da API LEGADA V1–V4 do Pagar.me (modelo "transactions"). Ativa _(POST /api/pagarme/legacy/list/transfers)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `transaction_id` | string | Não |  |
| `data` | string | Não | JSON com filtros (count, page, status, …) |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `transaction_ids` | string[] | Não | Bulk mode: multiple values for transaction_id |

#### `pagarme_list_accounts`

Lista as contas Pagar.me (chaves) conectadas a este install — id, label e versão (V5 ou legado V1–V4). _(POST /api/pagarme/list/accounts)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |

#### `pagarme_orders_get`

Pedidos (orders) no Pagar.me V5. _(POST /api/pagarme/orders/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `order_id` | string | Não |  |
| `order_ids` | string[] | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não | JSON com filtros extras (code, status, customer_id, created_since, created_until) |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |

#### `pagarme_orders_get_many`

Pedidos (orders) no Pagar.me V5. _(POST /api/pagarme/orders/get/many)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `order_id` | string | Não |  |
| `order_ids` | string[] | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não | JSON com filtros extras (code, status, customer_id, created_since, created_until) |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |

#### `pagarme_orders_list`

Pedidos (orders) no Pagar.me V5. _(POST /api/pagarme/orders/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `order_id` | string | Não |  |
| `order_ids` | string[] | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não | JSON com filtros extras (code, status, customer_id, created_since, created_until) |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |

#### `pagarme_orders_write_close`

Criar/atualizar/fechar pedidos no Pagar.me V5 (só contas sk_). _(POST /api/pagarme/orders/write/close)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `order_id` | string | Não |  |
| `closed` | boolean | Não |  |
| `data` | string | Não | JSON do corpo (create/update) |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `order_ids` | string[] | Não | Bulk mode: multiple values for order_id |

#### `pagarme_orders_write_create`

Criar/atualizar/fechar pedidos no Pagar.me V5 (só contas sk_). _(POST /api/pagarme/orders/write/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `order_id` | string | Não |  |
| `closed` | boolean | Não |  |
| `data` | string | Não | JSON do corpo (create/update) |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `order_ids` | string[] | Não | Bulk mode: multiple values for order_id |

#### `pagarme_orders_write_update`

Criar/atualizar/fechar pedidos no Pagar.me V5 (só contas sk_). _(POST /api/pagarme/orders/write/update)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `order_id` | string | Não |  |
| `closed` | boolean | Não |  |
| `data` | string | Não | JSON do corpo (create/update) |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `order_ids` | string[] | Não | Bulk mode: multiple values for order_id |

#### `pagarme_payables_get`

Recebíveis (payables) no Pagar.me V5. _(POST /api/pagarme/payables/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `payable_id` | string | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `payable_ids` | string[] | Não | Bulk mode: multiple values for payable_id |

#### `pagarme_payables_list`

Recebíveis (payables) no Pagar.me V5. _(POST /api/pagarme/payables/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `payable_id` | string | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `payable_ids` | string[] | Não | Bulk mode: multiple values for payable_id |

#### `pagarme_plans_delete`

Remove um plano no Pagar.me V5 (requer plan_id). Irreversível. _(POST /api/pagarme/plans/delete)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `plan_id` | string | Sim |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `plan_ids` | string[] | Não | Bulk mode: multiple values for plan_id |

#### `pagarme_plans_get`

Planos de assinatura no Pagar.me V5. _(POST /api/pagarme/plans/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `plan_id` | string | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `plan_ids` | string[] | Não | Bulk mode: multiple values for plan_id |

#### `pagarme_plans_list`

Planos de assinatura no Pagar.me V5. _(POST /api/pagarme/plans/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `plan_id` | string | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `plan_ids` | string[] | Não | Bulk mode: multiple values for plan_id |

#### `pagarme_plans_write_create`

Criar/atualizar planos no Pagar.me V5 (só sk_). _(POST /api/pagarme/plans/write/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `plan_id` | string | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `plan_ids` | string[] | Não | Bulk mode: multiple values for plan_id |

#### `pagarme_plans_write_update`

Criar/atualizar planos no Pagar.me V5 (só sk_). _(POST /api/pagarme/plans/write/update)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `plan_id` | string | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `plan_ids` | string[] | Não | Bulk mode: multiple values for plan_id |

#### `pagarme_recipients_anticipation_limits`

Recebedores (split/marketplace) no Pagar.me V5. _(POST /api/pagarme/recipients/anticipation/limits)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `recipient_id` | string | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `recipient_ids` | string[] | Não | Bulk mode: multiple values for recipient_id |

#### `pagarme_recipients_anticipations`

Recebedores (split/marketplace) no Pagar.me V5. _(POST /api/pagarme/recipients/anticipations)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `recipient_id` | string | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `recipient_ids` | string[] | Não | Bulk mode: multiple values for recipient_id |

#### `pagarme_recipients_balance`

Recebedores (split/marketplace) no Pagar.me V5. _(POST /api/pagarme/recipients/balance)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `recipient_id` | string | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `recipient_ids` | string[] | Não | Bulk mode: multiple values for recipient_id |

#### `pagarme_recipients_default`

Recebedores (split/marketplace) no Pagar.me V5. _(POST /api/pagarme/recipients/default)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `recipient_id` | string | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `recipient_ids` | string[] | Não | Bulk mode: multiple values for recipient_id |

#### `pagarme_recipients_get`

Recebedores (split/marketplace) no Pagar.me V5. _(POST /api/pagarme/recipients/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `recipient_id` | string | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `recipient_ids` | string[] | Não | Bulk mode: multiple values for recipient_id |

#### `pagarme_recipients_list`

Recebedores (split/marketplace) no Pagar.me V5. _(POST /api/pagarme/recipients/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `recipient_id` | string | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `recipient_ids` | string[] | Não | Bulk mode: multiple values for recipient_id |

#### `pagarme_recipients_transfers`

Recebedores (split/marketplace) no Pagar.me V5. _(POST /api/pagarme/recipients/transfers)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `recipient_id` | string | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `recipient_ids` | string[] | Não | Bulk mode: multiple values for recipient_id |

#### `pagarme_recipients_withdrawals`

Recebedores (split/marketplace) no Pagar.me V5. _(POST /api/pagarme/recipients/withdrawals)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `recipient_id` | string | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `recipient_ids` | string[] | Não | Bulk mode: multiple values for recipient_id |

#### `pagarme_recipients_write_create`

Criar/operar recebedores no Pagar.me V5 (só sk_). _(POST /api/pagarme/recipients/write/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `recipient_id` | string | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `recipient_ids` | string[] | Não | Bulk mode: multiple values for recipient_id |

#### `pagarme_recipients_write_create_anticipation`

Criar/operar recebedores no Pagar.me V5 (só sk_). _(POST /api/pagarme/recipients/write/create/anticipation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `recipient_id` | string | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `recipient_ids` | string[] | Não | Bulk mode: multiple values for recipient_id |

#### `pagarme_recipients_write_create_withdrawal`

Criar/operar recebedores no Pagar.me V5 (só sk_). _(POST /api/pagarme/recipients/write/create/withdrawal)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `recipient_id` | string | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `recipient_ids` | string[] | Não | Bulk mode: multiple values for recipient_id |

#### `pagarme_recipients_write_update`

Criar/operar recebedores no Pagar.me V5 (só sk_). _(POST /api/pagarme/recipients/write/update)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `recipient_id` | string | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `recipient_ids` | string[] | Não | Bulk mode: multiple values for recipient_id |

#### `pagarme_recipients_write_update_bank_account`

Criar/operar recebedores no Pagar.me V5 (só sk_). _(POST /api/pagarme/recipients/write/update/bank/account)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `recipient_id` | string | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `recipient_ids` | string[] | Não | Bulk mode: multiple values for recipient_id |

#### `pagarme_subscriptions_cancel`

Cancela uma assinatura no Pagar.me V5 (requer subscription_id; data opcional: { cancel_pending_invoices }). Irreversível. _(POST /api/pagarme/subscriptions/cancel)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `subscription_id` | string | Sim |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `subscription_ids` | string[] | Não | Bulk mode: multiple values for subscription_id |

#### `pagarme_subscriptions_cycles`

Assinaturas no Pagar.me V5. _(POST /api/pagarme/subscriptions/cycles)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `subscription_id` | string | Não |  |
| `item_id` | string | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `subscription_ids` | string[] | Não | Bulk mode: multiple values for subscription_id |
| `item_ids` | string[] | Não | Bulk mode: multiple values for item_id |

#### `pagarme_subscriptions_get`

Assinaturas no Pagar.me V5. _(POST /api/pagarme/subscriptions/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `subscription_id` | string | Não |  |
| `item_id` | string | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `subscription_ids` | string[] | Não | Bulk mode: multiple values for subscription_id |
| `item_ids` | string[] | Não | Bulk mode: multiple values for item_id |

#### `pagarme_subscriptions_items`

Assinaturas no Pagar.me V5. _(POST /api/pagarme/subscriptions/items)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `subscription_id` | string | Não |  |
| `item_id` | string | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `subscription_ids` | string[] | Não | Bulk mode: multiple values for subscription_id |
| `item_ids` | string[] | Não | Bulk mode: multiple values for item_id |

#### `pagarme_subscriptions_list`

Assinaturas no Pagar.me V5. _(POST /api/pagarme/subscriptions/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `subscription_id` | string | Não |  |
| `item_id` | string | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `subscription_ids` | string[] | Não | Bulk mode: multiple values for subscription_id |
| `item_ids` | string[] | Não | Bulk mode: multiple values for item_id |

#### `pagarme_subscriptions_usages`

Assinaturas no Pagar.me V5. _(POST /api/pagarme/subscriptions/usages)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `subscription_id` | string | Não |  |
| `item_id` | string | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `subscription_ids` | string[] | Não | Bulk mode: multiple values for subscription_id |
| `item_ids` | string[] | Não | Bulk mode: multiple values for item_id |

#### `pagarme_subscriptions_write_add_item`

Criar/operar assinaturas no Pagar.me V5 (só sk_; não-destrutivas). _(POST /api/pagarme/subscriptions/write/add/item)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `subscription_id` | string | Não |  |
| `item_id` | string | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `subscription_ids` | string[] | Não | Bulk mode: multiple values for subscription_id |
| `item_ids` | string[] | Não | Bulk mode: multiple values for item_id |

#### `pagarme_subscriptions_write_add_usage`

Criar/operar assinaturas no Pagar.me V5 (só sk_; não-destrutivas). _(POST /api/pagarme/subscriptions/write/add/usage)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `subscription_id` | string | Não |  |
| `item_id` | string | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `subscription_ids` | string[] | Não | Bulk mode: multiple values for subscription_id |
| `item_ids` | string[] | Não | Bulk mode: multiple values for item_id |

#### `pagarme_subscriptions_write_create`

Criar/operar assinaturas no Pagar.me V5 (só sk_; não-destrutivas). _(POST /api/pagarme/subscriptions/write/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `subscription_id` | string | Não |  |
| `item_id` | string | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `subscription_ids` | string[] | Não | Bulk mode: multiple values for subscription_id |
| `item_ids` | string[] | Não | Bulk mode: multiple values for item_id |

#### `pagarme_subscriptions_write_update_billing_date`

Criar/operar assinaturas no Pagar.me V5 (só sk_; não-destrutivas). _(POST /api/pagarme/subscriptions/write/update/billing/date)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `subscription_id` | string | Não |  |
| `item_id` | string | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `subscription_ids` | string[] | Não | Bulk mode: multiple values for subscription_id |
| `item_ids` | string[] | Não | Bulk mode: multiple values for item_id |

#### `pagarme_subscriptions_write_update_card`

Criar/operar assinaturas no Pagar.me V5 (só sk_; não-destrutivas). _(POST /api/pagarme/subscriptions/write/update/card)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `subscription_id` | string | Não |  |
| `item_id` | string | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `subscription_ids` | string[] | Não | Bulk mode: multiple values for subscription_id |
| `item_ids` | string[] | Não | Bulk mode: multiple values for item_id |

#### `pagarme_subscriptions_write_update_payment_method`

Criar/operar assinaturas no Pagar.me V5 (só sk_; não-destrutivas). _(POST /api/pagarme/subscriptions/write/update/payment/method)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `subscription_id` | string | Não |  |
| `item_id` | string | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `subscription_ids` | string[] | Não | Bulk mode: multiple values for subscription_id |
| `item_ids` | string[] | Não | Bulk mode: multiple values for item_id |

#### `pagarme_transfers_get`

Transferências no Pagar.me V5. _(POST /api/pagarme/transfers/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `transfer_id` | string | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `transfer_ids` | string[] | Não | Bulk mode: multiple values for transfer_id |

#### `pagarme_transfers_list`

Transferências no Pagar.me V5. _(POST /api/pagarme/transfers/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `transfer_id` | string | Não |  |
| `page` | number | Não |  |
| `size` | number | Não |  |
| `data` | string | Não |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |
| `transfer_ids` | string[] | Não | Bulk mode: multiple values for transfer_id |

#### `pagarme_transfers_write`

Cria uma transferência no Pagar.me V5 (só sk_). data = JSON do corpo (amount, recipient_id, …). _(POST /api/pagarme/transfers/write)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `data` | string | Sim |  |
| `account` | string | Não | Quando houver múltiplas contas Pagar.me: id, label ou parcial. Veja pagarme_list_accounts. |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_pagarme` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).
