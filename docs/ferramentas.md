# Ferramentas

Pagar.me expõe 80 ferramentas.

### 1. `pagarme_list_accounts`
**Input**: `account` (opcional)

Lista as contas Pagar.me (chaves) conectadas a este install — id, label e versão (V5 ou legado V1–V4).

### 2. `pagarme_orders_list`
**Input**: `order_id` (opcional), `order_ids` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional)

Pedidos (orders) no Pagar.me V5. Ações: - list: lista paginada (page, size, code, status, customer_id, created_since, created_until). - get: detalhe por order_id. - get_many: busca vários por order_ids (lote, retorna { results, errors }). [Flattened action: list]

### 3. `pagarme_orders_get`
**Input**: `order_id` (opcional), `order_ids` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional)

Pedidos (orders) no Pagar.me V5. Ações: - list: lista paginada (page, size, code, status, customer_id, created_since, created_until). - get: detalhe por order_id. - get_many: busca vários por order_ids (lote, retorna { results, errors }). [Flattened action: get]

### 4. `pagarme_orders_get_many`
**Input**: `order_id` (opcional), `order_ids` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional)

Pedidos (orders) no Pagar.me V5. Ações: - list: lista paginada (page, size, code, status, customer_id, created_since, created_until). - get: detalhe por order_id. - get_many: busca vários por order_ids (lote, retorna { results, errors }). [Flattened action: get_many]

### 5. `pagarme_orders_write_create`
**Input**: `order_id` (opcional), `closed` (opcional), `data` (opcional), `account` (opcional), `order_ids` (opcional)

Criar/atualizar/fechar pedidos no Pagar.me V5 (só contas sk_). Ações: - create: cria pedido. data = JSON do pedido (customer/customer_id, items[], payments[]). - update: atualiza pedido (requer order_id). data = campos a alterar. - close: fecha (closed:true) ou reabre (closed:false) o pedido (requer order_id). [Flattened action: create] Bulk support: accepts order_ids for batched execution.

### 6. `pagarme_orders_write_update`
**Input**: `order_id` (opcional), `closed` (opcional), `data` (opcional), `account` (opcional), `order_ids` (opcional)

Criar/atualizar/fechar pedidos no Pagar.me V5 (só contas sk_). Ações: - create: cria pedido. data = JSON do pedido (customer/customer_id, items[], payments[]). - update: atualiza pedido (requer order_id). data = campos a alterar. - close: fecha (closed:true) ou reabre (closed:false) o pedido (requer order_id). [Flattened action: update] Bulk support: accepts order_ids for batched execution.

### 7. `pagarme_orders_write_close`
**Input**: `order_id` (opcional), `closed` (opcional), `data` (opcional), `account` (opcional), `order_ids` (opcional)

Criar/atualizar/fechar pedidos no Pagar.me V5 (só contas sk_). Ações: - create: cria pedido. data = JSON do pedido (customer/customer_id, items[], payments[]). - update: atualiza pedido (requer order_id). data = campos a alterar. - close: fecha (closed:true) ou reabre (closed:false) o pedido (requer order_id). [Flattened action: close] Bulk support: accepts order_ids for batched execution.

### 8. `pagarme_charges_list`
**Input**: `charge_id` (opcional), `charge_ids` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional)

Cobranças (charges) no Pagar.me V5. Ações: - list: lista paginada (page, size; filtros via data: status, payment_method, customer_id, order_id, created_since/until). - summary: agregado de cobranças (data: status, created_since/until). - get: detalhe por charge_id. - get_many: vários por charge_ids (lote). [Flattened action: list]

### 9. `pagarme_charges_summary`
**Input**: `charge_id` (opcional), `charge_ids` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional)

Cobranças (charges) no Pagar.me V5. Ações: - list: lista paginada (page, size; filtros via data: status, payment_method, customer_id, order_id, created_since/until). - summary: agregado de cobranças (data: status, created_since/until). - get: detalhe por charge_id. - get_many: vários por charge_ids (lote). [Flattened action: summary]

### 10. `pagarme_charges_get`
**Input**: `charge_id` (opcional), `charge_ids` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional)

Cobranças (charges) no Pagar.me V5. Ações: - list: lista paginada (page, size; filtros via data: status, payment_method, customer_id, order_id, created_since/until). - summary: agregado de cobranças (data: status, created_since/until). - get: detalhe por charge_id. - get_many: vários por charge_ids (lote). [Flattened action: get]

### 11. `pagarme_charges_get_many`
**Input**: `charge_id` (opcional), `charge_ids` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional)

Cobranças (charges) no Pagar.me V5. Ações: - list: lista paginada (page, size; filtros via data: status, payment_method, customer_id, order_id, created_since/until). - summary: agregado de cobranças (data: status, created_since/until). - get: detalhe por charge_id. - get_many: vários por charge_ids (lote). [Flattened action: get_many]

### 12. `pagarme_charges_write_capture`
**Input**: `charge_id`, `data` (opcional), `account` (opcional), `charge_ids` (opcional)

Operar cobranças no Pagar.me V5 (só contas sk_; não-destrutivas). Ações (requerem charge_id): - capture: captura (data opcional: amount). - retry: reprocessa. - confirm: confirma pagamento (cash/voucher; data opcional). - update_due_date: altera vencimento (data: { due_at }). - update_payment_method: altera meio de pagamento (data). - update_card: altera cartão (data). [Flattened action: capture] Bulk support: accepts charge_ids for batched execution.

### 13. `pagarme_charges_write_retry`
**Input**: `charge_id`, `data` (opcional), `account` (opcional), `charge_ids` (opcional)

Operar cobranças no Pagar.me V5 (só contas sk_; não-destrutivas). Ações (requerem charge_id): - capture: captura (data opcional: amount). - retry: reprocessa. - confirm: confirma pagamento (cash/voucher; data opcional). - update_due_date: altera vencimento (data: { due_at }). - update_payment_method: altera meio de pagamento (data). - update_card: altera cartão (data). [Flattened action: retry] Bulk support: accepts charge_ids for batched execution.

### 14. `pagarme_charges_write_confirm`
**Input**: `charge_id`, `data` (opcional), `account` (opcional), `charge_ids` (opcional)

Operar cobranças no Pagar.me V5 (só contas sk_; não-destrutivas). Ações (requerem charge_id): - capture: captura (data opcional: amount). - retry: reprocessa. - confirm: confirma pagamento (cash/voucher; data opcional). - update_due_date: altera vencimento (data: { due_at }). - update_payment_method: altera meio de pagamento (data). - update_card: altera cartão (data). [Flattened action: confirm] Bulk support: accepts charge_ids for batched execution.

### 15. `pagarme_charges_write_update_due_date`
**Input**: `charge_id`, `data` (opcional), `account` (opcional), `charge_ids` (opcional)

Operar cobranças no Pagar.me V5 (só contas sk_; não-destrutivas). Ações (requerem charge_id): - capture: captura (data opcional: amount). - retry: reprocessa. - confirm: confirma pagamento (cash/voucher; data opcional). - update_due_date: altera vencimento (data: { due_at }). - update_payment_method: altera meio de pagamento (data). - update_card: altera cartão (data). [Flattened action: update_due_date] Bulk support: accepts charge_ids for batched execution.

### 16. `pagarme_charges_write_update_payment_method`
**Input**: `charge_id`, `data` (opcional), `account` (opcional), `charge_ids` (opcional)

Operar cobranças no Pagar.me V5 (só contas sk_; não-destrutivas). Ações (requerem charge_id): - capture: captura (data opcional: amount). - retry: reprocessa. - confirm: confirma pagamento (cash/voucher; data opcional). - update_due_date: altera vencimento (data: { due_at }). - update_payment_method: altera meio de pagamento (data). - update_card: altera cartão (data). [Flattened action: update_payment_method] Bulk support: accepts charge_ids for batched execution.

### 17. `pagarme_charges_write_update_card`
**Input**: `charge_id`, `data` (opcional), `account` (opcional), `charge_ids` (opcional)

Operar cobranças no Pagar.me V5 (só contas sk_; não-destrutivas). Ações (requerem charge_id): - capture: captura (data opcional: amount). - retry: reprocessa. - confirm: confirma pagamento (cash/voucher; data opcional). - update_due_date: altera vencimento (data: { due_at }). - update_payment_method: altera meio de pagamento (data). - update_card: altera cartão (data). [Flattened action: update_card] Bulk support: accepts charge_ids for batched execution.

### 18. `pagarme_charges_cancel`
**Input**: `charge_id`, `data` (opcional), `account` (opcional), `charge_ids` (opcional)

Cancela/estorna uma cobrança no Pagar.me V5 (requer charge_id; data opcional com amount p/ estorno parcial). Irreversível. Bulk support: accepts charge_ids for batched execution.

### 19. `pagarme_customers_list`
**Input**: `customer_id` (opcional), `address_id` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional), `customer_ids` (opcional), `address_ids` (opcional)

Clientes e endereços no Pagar.me V5. Ações: - list: lista clientes (page, size; data: name, email, document, code). - get: cliente por customer_id. - list_addresses: endereços do cliente (requer customer_id). - get_address: endereço (requer customer_id + address_id). [Flattened action: list] Bulk support: accepts customer_ids, address_ids for batched execution.

### 20. `pagarme_customers_get`
**Input**: `customer_id` (opcional), `address_id` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional), `customer_ids` (opcional), `address_ids` (opcional)

Clientes e endereços no Pagar.me V5. Ações: - list: lista clientes (page, size; data: name, email, document, code). - get: cliente por customer_id. - list_addresses: endereços do cliente (requer customer_id). - get_address: endereço (requer customer_id + address_id). [Flattened action: get] Bulk support: accepts customer_ids, address_ids for batched execution.

### 21. `pagarme_customers_list_addresses`
**Input**: `customer_id` (opcional), `address_id` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional), `customer_ids` (opcional), `address_ids` (opcional)

Clientes e endereços no Pagar.me V5. Ações: - list: lista clientes (page, size; data: name, email, document, code). - get: cliente por customer_id. - list_addresses: endereços do cliente (requer customer_id). - get_address: endereço (requer customer_id + address_id). [Flattened action: list_addresses] Bulk support: accepts customer_ids, address_ids for batched execution.

### 22. `pagarme_customers_get_address`
**Input**: `customer_id` (opcional), `address_id` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional), `customer_ids` (opcional), `address_ids` (opcional)

Clientes e endereços no Pagar.me V5. Ações: - list: lista clientes (page, size; data: name, email, document, code). - get: cliente por customer_id. - list_addresses: endereços do cliente (requer customer_id). - get_address: endereço (requer customer_id + address_id). [Flattened action: get_address] Bulk support: accepts customer_ids, address_ids for batched execution.

### 23. `pagarme_customers_write_create`
**Input**: `customer_id` (opcional), `address_id` (opcional), `data` (opcional), `account` (opcional), `customer_ids` (opcional), `address_ids` (opcional)

Criar/atualizar clientes e endereços no Pagar.me V5 (só sk_). Ações: - create: cria cliente (data: name, email, document, type, …). - update: atualiza cliente (requer customer_id; data). - create_address: cria endereço (requer customer_id; data). - update_address: atualiza endereço (requer customer_id + address_id; data). - delete_address: remove endereço (requer customer_id + address_id). [Flattened action: create] Bulk support: accepts customer_ids, address_ids for batched execution.

### 24. `pagarme_customers_write_update`
**Input**: `customer_id` (opcional), `address_id` (opcional), `data` (opcional), `account` (opcional), `customer_ids` (opcional), `address_ids` (opcional)

Criar/atualizar clientes e endereços no Pagar.me V5 (só sk_). Ações: - create: cria cliente (data: name, email, document, type, …). - update: atualiza cliente (requer customer_id; data). - create_address: cria endereço (requer customer_id; data). - update_address: atualiza endereço (requer customer_id + address_id; data). - delete_address: remove endereço (requer customer_id + address_id). [Flattened action: update] Bulk support: accepts customer_ids, address_ids for batched execution.

### 25. `pagarme_customers_write_create_address`
**Input**: `customer_id` (opcional), `address_id` (opcional), `data` (opcional), `account` (opcional), `customer_ids` (opcional), `address_ids` (opcional)

Criar/atualizar clientes e endereços no Pagar.me V5 (só sk_). Ações: - create: cria cliente (data: name, email, document, type, …). - update: atualiza cliente (requer customer_id; data). - create_address: cria endereço (requer customer_id; data). - update_address: atualiza endereço (requer customer_id + address_id; data). - delete_address: remove endereço (requer customer_id + address_id). [Flattened action: create_address] Bulk support: accepts customer_ids, address_ids for batched execution.

### 26. `pagarme_customers_write_update_address`
**Input**: `customer_id` (opcional), `address_id` (opcional), `data` (opcional), `account` (opcional), `customer_ids` (opcional), `address_ids` (opcional)

Criar/atualizar clientes e endereços no Pagar.me V5 (só sk_). Ações: - create: cria cliente (data: name, email, document, type, …). - update: atualiza cliente (requer customer_id; data). - create_address: cria endereço (requer customer_id; data). - update_address: atualiza endereço (requer customer_id + address_id; data). - delete_address: remove endereço (requer customer_id + address_id). [Flattened action: update_address] Bulk support: accepts customer_ids, address_ids for batched execution.

### 27. `pagarme_customers_write_delete_address`
**Input**: `customer_id` (opcional), `address_id` (opcional), `data` (opcional), `account` (opcional), `customer_ids` (opcional), `address_ids` (opcional)

Criar/atualizar clientes e endereços no Pagar.me V5 (só sk_). Ações: - create: cria cliente (data: name, email, document, type, …). - update: atualiza cliente (requer customer_id; data). - create_address: cria endereço (requer customer_id; data). - update_address: atualiza endereço (requer customer_id + address_id; data). - delete_address: remove endereço (requer customer_id + address_id). [Flattened action: delete_address] Bulk support: accepts customer_ids, address_ids for batched execution.

### 28. `pagarme_cards_list`
**Input**: `customer_id`, `card_id` (opcional), `account` (opcional), `customer_ids` (opcional), `card_ids` (opcional)

Cartões salvos de um cliente no Pagar.me V5. Ações (requerem customer_id): - list: lista cartões. - get: cartão por card_id. [Flattened action: list] Bulk support: accepts customer_ids, card_ids for batched execution.

### 29. `pagarme_cards_get`
**Input**: `customer_id`, `card_id` (opcional), `account` (opcional), `customer_ids` (opcional), `card_ids` (opcional)

Cartões salvos de um cliente no Pagar.me V5. Ações (requerem customer_id): - list: lista cartões. - get: cartão por card_id. [Flattened action: get] Bulk support: accepts customer_ids, card_ids for batched execution.

### 30. `pagarme_cards_write_create`
**Input**: `customer_id`, `card_id` (opcional), `data` (opcional), `account` (opcional), `customer_ids` (opcional), `card_ids` (opcional)

Criar/renovar cartões de um cliente no Pagar.me V5 (só sk_; requer customer_id). Ações: - create: tokeniza/salva cartão (data: number, holder_name, exp_month, exp_year, cvv ou card_token). - renew: renova cartão (requer card_id). [Flattened action: create] Bulk support: accepts customer_ids, card_ids for batched execution.

### 31. `pagarme_cards_write_renew`
**Input**: `customer_id`, `card_id` (opcional), `data` (opcional), `account` (opcional), `customer_ids` (opcional), `card_ids` (opcional)

Criar/renovar cartões de um cliente no Pagar.me V5 (só sk_; requer customer_id). Ações: - create: tokeniza/salva cartão (data: number, holder_name, exp_month, exp_year, cvv ou card_token). - renew: renova cartão (requer card_id). [Flattened action: renew] Bulk support: accepts customer_ids, card_ids for batched execution.

### 32. `pagarme_cards_delete`
**Input**: `customer_id`, `card_id`, `account` (opcional), `customer_ids` (opcional), `card_ids` (opcional)

Remove um cartão salvo do cliente no Pagar.me V5 (requer customer_id + card_id). Irreversível. Bulk support: accepts customer_ids, card_ids for batched execution.

### 33. `pagarme_plans_list`
**Input**: `plan_id` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional), `plan_ids` (opcional)

Planos de assinatura no Pagar.me V5. Ações: - list: lista planos (page, size; data: name, status). - get: plano por plan_id. [Flattened action: list] Bulk support: accepts plan_ids for batched execution.

### 34. `pagarme_plans_get`
**Input**: `plan_id` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional), `plan_ids` (opcional)

Planos de assinatura no Pagar.me V5. Ações: - list: lista planos (page, size; data: name, status). - get: plano por plan_id. [Flattened action: get] Bulk support: accepts plan_ids for batched execution.

### 35. `pagarme_plans_write_create`
**Input**: `plan_id` (opcional), `data` (opcional), `account` (opcional), `plan_ids` (opcional)

Criar/atualizar planos no Pagar.me V5 (só sk_). Ações: - create: cria plano (data: name, interval, interval_count, items[], …). - update: atualiza plano (requer plan_id; data). [Flattened action: create] Bulk support: accepts plan_ids for batched execution.

### 36. `pagarme_plans_write_update`
**Input**: `plan_id` (opcional), `data` (opcional), `account` (opcional), `plan_ids` (opcional)

Criar/atualizar planos no Pagar.me V5 (só sk_). Ações: - create: cria plano (data: name, interval, interval_count, items[], …). - update: atualiza plano (requer plan_id; data). [Flattened action: update] Bulk support: accepts plan_ids for batched execution.

### 37. `pagarme_plans_delete`
**Input**: `plan_id`, `account` (opcional), `plan_ids` (opcional)

Remove um plano no Pagar.me V5 (requer plan_id). Irreversível. Bulk support: accepts plan_ids for batched execution.

### 38. `pagarme_subscriptions_list`
**Input**: `subscription_id` (opcional), `item_id` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional), `subscription_ids` (opcional), `item_ids` (opcional)

Assinaturas no Pagar.me V5. Ações: - list: lista assinaturas (page, size; data: customer_id, plan_id, status, created_since/until). - get: assinatura por subscription_id. - items: itens da assinatura (requer subscription_id). - cycles: ciclos da assinatura (requer subscription_id). - usages: usos de um item medido (requer subscription_id + item_id). [Flattened action: list] Bulk support: accepts subscription_ids, item_ids for batched execution.

### 39. `pagarme_subscriptions_get`
**Input**: `subscription_id` (opcional), `item_id` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional), `subscription_ids` (opcional), `item_ids` (opcional)

Assinaturas no Pagar.me V5. Ações: - list: lista assinaturas (page, size; data: customer_id, plan_id, status, created_since/until). - get: assinatura por subscription_id. - items: itens da assinatura (requer subscription_id). - cycles: ciclos da assinatura (requer subscription_id). - usages: usos de um item medido (requer subscription_id + item_id). [Flattened action: get] Bulk support: accepts subscription_ids, item_ids for batched execution.

### 40. `pagarme_subscriptions_items`
**Input**: `subscription_id` (opcional), `item_id` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional), `subscription_ids` (opcional), `item_ids` (opcional)

Assinaturas no Pagar.me V5. Ações: - list: lista assinaturas (page, size; data: customer_id, plan_id, status, created_since/until). - get: assinatura por subscription_id. - items: itens da assinatura (requer subscription_id). - cycles: ciclos da assinatura (requer subscription_id). - usages: usos de um item medido (requer subscription_id + item_id). [Flattened action: items] Bulk support: accepts subscription_ids, item_ids for batched execution.

### 41. `pagarme_subscriptions_cycles`
**Input**: `subscription_id` (opcional), `item_id` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional), `subscription_ids` (opcional), `item_ids` (opcional)

Assinaturas no Pagar.me V5. Ações: - list: lista assinaturas (page, size; data: customer_id, plan_id, status, created_since/until). - get: assinatura por subscription_id. - items: itens da assinatura (requer subscription_id). - cycles: ciclos da assinatura (requer subscription_id). - usages: usos de um item medido (requer subscription_id + item_id). [Flattened action: cycles] Bulk support: accepts subscription_ids, item_ids for batched execution.

### 42. `pagarme_subscriptions_usages`
**Input**: `subscription_id` (opcional), `item_id` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional), `subscription_ids` (opcional), `item_ids` (opcional)

Assinaturas no Pagar.me V5. Ações: - list: lista assinaturas (page, size; data: customer_id, plan_id, status, created_since/until). - get: assinatura por subscription_id. - items: itens da assinatura (requer subscription_id). - cycles: ciclos da assinatura (requer subscription_id). - usages: usos de um item medido (requer subscription_id + item_id). [Flattened action: usages] Bulk support: accepts subscription_ids, item_ids for batched execution.

### 43. `pagarme_subscriptions_write_create`
**Input**: `subscription_id` (opcional), `item_id` (opcional), `data` (opcional), `account` (opcional), `subscription_ids` (opcional), `item_ids` (opcional)

Criar/operar assinaturas no Pagar.me V5 (só sk_; não-destrutivas). Ações: - create: cria assinatura (data: customer_id/customer, plan_id ou items[], payment_method, card_id, …). - update_card: altera cartão (requer subscription_id; data). - update_payment_method: altera meio de pagamento (requer subscription_id; data). - update_billing_date: altera data de cobrança (requer subscription_id; data). - add_item: adiciona item (requer subscription_id; data). - add_usage: registra uso de item medido (requer subscription_id + item_id; data opcional). [Flattened action: create] Bulk support: accepts subscription_ids, item_ids for batched execution.

### 44. `pagarme_subscriptions_write_update_card`
**Input**: `subscription_id` (opcional), `item_id` (opcional), `data` (opcional), `account` (opcional), `subscription_ids` (opcional), `item_ids` (opcional)

Criar/operar assinaturas no Pagar.me V5 (só sk_; não-destrutivas). Ações: - create: cria assinatura (data: customer_id/customer, plan_id ou items[], payment_method, card_id, …). - update_card: altera cartão (requer subscription_id; data). - update_payment_method: altera meio de pagamento (requer subscription_id; data). - update_billing_date: altera data de cobrança (requer subscription_id; data). - add_item: adiciona item (requer subscription_id; data). - add_usage: registra uso de item medido (requer subscription_id + item_id; data opcional). [Flattened action: update_card] Bulk support: accepts subscription_ids, item_ids for batched execution.

### 45. `pagarme_subscriptions_write_update_payment_method`
**Input**: `subscription_id` (opcional), `item_id` (opcional), `data` (opcional), `account` (opcional), `subscription_ids` (opcional), `item_ids` (opcional)

Criar/operar assinaturas no Pagar.me V5 (só sk_; não-destrutivas). Ações: - create: cria assinatura (data: customer_id/customer, plan_id ou items[], payment_method, card_id, …). - update_card: altera cartão (requer subscription_id; data). - update_payment_method: altera meio de pagamento (requer subscription_id; data). - update_billing_date: altera data de cobrança (requer subscription_id; data). - add_item: adiciona item (requer subscription_id; data). - add_usage: registra uso de item medido (requer subscription_id + item_id; data opcional). [Flattened action: update_payment_method] Bulk support: accepts subscription_ids, item_ids for batched execution.

### 46. `pagarme_subscriptions_write_update_billing_date`
**Input**: `subscription_id` (opcional), `item_id` (opcional), `data` (opcional), `account` (opcional), `subscription_ids` (opcional), `item_ids` (opcional)

Criar/operar assinaturas no Pagar.me V5 (só sk_; não-destrutivas). Ações: - create: cria assinatura (data: customer_id/customer, plan_id ou items[], payment_method, card_id, …). - update_card: altera cartão (requer subscription_id; data). - update_payment_method: altera meio de pagamento (requer subscription_id; data). - update_billing_date: altera data de cobrança (requer subscription_id; data). - add_item: adiciona item (requer subscription_id; data). - add_usage: registra uso de item medido (requer subscription_id + item_id; data opcional). [Flattened action: update_billing_date] Bulk support: accepts subscription_ids, item_ids for batched execution.

### 47. `pagarme_subscriptions_write_add_item`
**Input**: `subscription_id` (opcional), `item_id` (opcional), `data` (opcional), `account` (opcional), `subscription_ids` (opcional), `item_ids` (opcional)

Criar/operar assinaturas no Pagar.me V5 (só sk_; não-destrutivas). Ações: - create: cria assinatura (data: customer_id/customer, plan_id ou items[], payment_method, card_id, …). - update_card: altera cartão (requer subscription_id; data). - update_payment_method: altera meio de pagamento (requer subscription_id; data). - update_billing_date: altera data de cobrança (requer subscription_id; data). - add_item: adiciona item (requer subscription_id; data). - add_usage: registra uso de item medido (requer subscription_id + item_id; data opcional). [Flattened action: add_item] Bulk support: accepts subscription_ids, item_ids for batched execution.

### 48. `pagarme_subscriptions_write_add_usage`
**Input**: `subscription_id` (opcional), `item_id` (opcional), `data` (opcional), `account` (opcional), `subscription_ids` (opcional), `item_ids` (opcional)

Criar/operar assinaturas no Pagar.me V5 (só sk_; não-destrutivas). Ações: - create: cria assinatura (data: customer_id/customer, plan_id ou items[], payment_method, card_id, …). - update_card: altera cartão (requer subscription_id; data). - update_payment_method: altera meio de pagamento (requer subscription_id; data). - update_billing_date: altera data de cobrança (requer subscription_id; data). - add_item: adiciona item (requer subscription_id; data). - add_usage: registra uso de item medido (requer subscription_id + item_id; data opcional). [Flattened action: add_usage] Bulk support: accepts subscription_ids, item_ids for batched execution.

### 49. `pagarme_subscriptions_cancel`
**Input**: `subscription_id`, `data` (opcional), `account` (opcional), `subscription_ids` (opcional)

Cancela uma assinatura no Pagar.me V5 (requer subscription_id; data opcional: { cancel_pending_invoices }). Irreversível. Bulk support: accepts subscription_ids for batched execution.

### 50. `pagarme_recipients_list`
**Input**: `recipient_id` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional), `recipient_ids` (opcional)

Recebedores (split/marketplace) no Pagar.me V5. Ações: - list: lista recebedores (page, size). - get: recebedor por recipient_id. - default: recebedor padrão (a própria conta). - balance: saldo do recebedor (requer recipient_id). - transfers: transferências do recebedor (requer recipient_id). - withdrawals: saques do recebedor (requer recipient_id). - anticipations: antecipações do recebedor (requer recipient_id). - anticipation_limits: limites de antecipação (requer recipient_id). [Flattened action: list] Bulk support: accepts recipient_ids for batched execution.

### 51. `pagarme_recipients_get`
**Input**: `recipient_id` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional), `recipient_ids` (opcional)

Recebedores (split/marketplace) no Pagar.me V5. Ações: - list: lista recebedores (page, size). - get: recebedor por recipient_id. - default: recebedor padrão (a própria conta). - balance: saldo do recebedor (requer recipient_id). - transfers: transferências do recebedor (requer recipient_id). - withdrawals: saques do recebedor (requer recipient_id). - anticipations: antecipações do recebedor (requer recipient_id). - anticipation_limits: limites de antecipação (requer recipient_id). [Flattened action: get] Bulk support: accepts recipient_ids for batched execution.

### 52. `pagarme_recipients_default`
**Input**: `recipient_id` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional), `recipient_ids` (opcional)

Recebedores (split/marketplace) no Pagar.me V5. Ações: - list: lista recebedores (page, size). - get: recebedor por recipient_id. - default: recebedor padrão (a própria conta). - balance: saldo do recebedor (requer recipient_id). - transfers: transferências do recebedor (requer recipient_id). - withdrawals: saques do recebedor (requer recipient_id). - anticipations: antecipações do recebedor (requer recipient_id). - anticipation_limits: limites de antecipação (requer recipient_id). [Flattened action: default] Bulk support: accepts recipient_ids for batched execution.

### 53. `pagarme_recipients_balance`
**Input**: `recipient_id` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional), `recipient_ids` (opcional)

Recebedores (split/marketplace) no Pagar.me V5. Ações: - list: lista recebedores (page, size). - get: recebedor por recipient_id. - default: recebedor padrão (a própria conta). - balance: saldo do recebedor (requer recipient_id). - transfers: transferências do recebedor (requer recipient_id). - withdrawals: saques do recebedor (requer recipient_id). - anticipations: antecipações do recebedor (requer recipient_id). - anticipation_limits: limites de antecipação (requer recipient_id). [Flattened action: balance] Bulk support: accepts recipient_ids for batched execution.

### 54. `pagarme_recipients_transfers`
**Input**: `recipient_id` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional), `recipient_ids` (opcional)

Recebedores (split/marketplace) no Pagar.me V5. Ações: - list: lista recebedores (page, size). - get: recebedor por recipient_id. - default: recebedor padrão (a própria conta). - balance: saldo do recebedor (requer recipient_id). - transfers: transferências do recebedor (requer recipient_id). - withdrawals: saques do recebedor (requer recipient_id). - anticipations: antecipações do recebedor (requer recipient_id). - anticipation_limits: limites de antecipação (requer recipient_id). [Flattened action: transfers] Bulk support: accepts recipient_ids for batched execution.

### 55. `pagarme_recipients_withdrawals`
**Input**: `recipient_id` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional), `recipient_ids` (opcional)

Recebedores (split/marketplace) no Pagar.me V5. Ações: - list: lista recebedores (page, size). - get: recebedor por recipient_id. - default: recebedor padrão (a própria conta). - balance: saldo do recebedor (requer recipient_id). - transfers: transferências do recebedor (requer recipient_id). - withdrawals: saques do recebedor (requer recipient_id). - anticipations: antecipações do recebedor (requer recipient_id). - anticipation_limits: limites de antecipação (requer recipient_id). [Flattened action: withdrawals] Bulk support: accepts recipient_ids for batched execution.

### 56. `pagarme_recipients_anticipations`
**Input**: `recipient_id` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional), `recipient_ids` (opcional)

Recebedores (split/marketplace) no Pagar.me V5. Ações: - list: lista recebedores (page, size). - get: recebedor por recipient_id. - default: recebedor padrão (a própria conta). - balance: saldo do recebedor (requer recipient_id). - transfers: transferências do recebedor (requer recipient_id). - withdrawals: saques do recebedor (requer recipient_id). - anticipations: antecipações do recebedor (requer recipient_id). - anticipation_limits: limites de antecipação (requer recipient_id). [Flattened action: anticipations] Bulk support: accepts recipient_ids for batched execution.

### 57. `pagarme_recipients_anticipation_limits`
**Input**: `recipient_id` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional), `recipient_ids` (opcional)

Recebedores (split/marketplace) no Pagar.me V5. Ações: - list: lista recebedores (page, size). - get: recebedor por recipient_id. - default: recebedor padrão (a própria conta). - balance: saldo do recebedor (requer recipient_id). - transfers: transferências do recebedor (requer recipient_id). - withdrawals: saques do recebedor (requer recipient_id). - anticipations: antecipações do recebedor (requer recipient_id). - anticipation_limits: limites de antecipação (requer recipient_id). [Flattened action: anticipation_limits] Bulk support: accepts recipient_ids for batched execution.

### 58. `pagarme_recipients_write_create`
**Input**: `recipient_id` (opcional), `data` (opcional), `account` (opcional), `recipient_ids` (opcional)

Criar/operar recebedores no Pagar.me V5 (só sk_). Ações: - create: cria recebedor (data). - update: atualiza recebedor (requer recipient_id; data). - update_bank_account: atualiza conta bancária (requer recipient_id; data). - create_withdrawal: cria saque (requer recipient_id; data: { amount }). - create_anticipation: cria antecipação (requer recipient_id; data). [Flattened action: create] Bulk support: accepts recipient_ids for batched execution.

### 59. `pagarme_recipients_write_update`
**Input**: `recipient_id` (opcional), `data` (opcional), `account` (opcional), `recipient_ids` (opcional)

Criar/operar recebedores no Pagar.me V5 (só sk_). Ações: - create: cria recebedor (data). - update: atualiza recebedor (requer recipient_id; data). - update_bank_account: atualiza conta bancária (requer recipient_id; data). - create_withdrawal: cria saque (requer recipient_id; data: { amount }). - create_anticipation: cria antecipação (requer recipient_id; data). [Flattened action: update] Bulk support: accepts recipient_ids for batched execution.

### 60. `pagarme_recipients_write_update_bank_account`
**Input**: `recipient_id` (opcional), `data` (opcional), `account` (opcional), `recipient_ids` (opcional)

Criar/operar recebedores no Pagar.me V5 (só sk_). Ações: - create: cria recebedor (data). - update: atualiza recebedor (requer recipient_id; data). - update_bank_account: atualiza conta bancária (requer recipient_id; data). - create_withdrawal: cria saque (requer recipient_id; data: { amount }). - create_anticipation: cria antecipação (requer recipient_id; data). [Flattened action: update_bank_account] Bulk support: accepts recipient_ids for batched execution.

### 61. `pagarme_recipients_write_create_withdrawal`
**Input**: `recipient_id` (opcional), `data` (opcional), `account` (opcional), `recipient_ids` (opcional)

Criar/operar recebedores no Pagar.me V5 (só sk_). Ações: - create: cria recebedor (data). - update: atualiza recebedor (requer recipient_id; data). - update_bank_account: atualiza conta bancária (requer recipient_id; data). - create_withdrawal: cria saque (requer recipient_id; data: { amount }). - create_anticipation: cria antecipação (requer recipient_id; data). [Flattened action: create_withdrawal] Bulk support: accepts recipient_ids for batched execution.

### 62. `pagarme_recipients_write_create_anticipation`
**Input**: `recipient_id` (opcional), `data` (opcional), `account` (opcional), `recipient_ids` (opcional)

Criar/operar recebedores no Pagar.me V5 (só sk_). Ações: - create: cria recebedor (data). - update: atualiza recebedor (requer recipient_id; data). - update_bank_account: atualiza conta bancária (requer recipient_id; data). - create_withdrawal: cria saque (requer recipient_id; data: { amount }). - create_anticipation: cria antecipação (requer recipient_id; data). [Flattened action: create_anticipation] Bulk support: accepts recipient_ids for batched execution.

### 63. `pagarme_transfers_list`
**Input**: `transfer_id` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional), `transfer_ids` (opcional)

Transferências no Pagar.me V5. Ações: - list: lista transferências (page, size; data: filtros). - get: transferência por transfer_id. [Flattened action: list] Bulk support: accepts transfer_ids for batched execution.

### 64. `pagarme_transfers_get`
**Input**: `transfer_id` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional), `transfer_ids` (opcional)

Transferências no Pagar.me V5. Ações: - list: lista transferências (page, size; data: filtros). - get: transferência por transfer_id. [Flattened action: get] Bulk support: accepts transfer_ids for batched execution.

### 65. `pagarme_transfers_write`
**Input**: `data`, `account` (opcional)

Cria uma transferência no Pagar.me V5 (só sk_). data = JSON do corpo (amount, recipient_id, …).

### 66. `pagarme_payables_list`
**Input**: `payable_id` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional), `payable_ids` (opcional)

Recebíveis (payables) no Pagar.me V5. Ações: - list: lista recebíveis (page, size; data: status, payment_date, type, …). - get: recebível por payable_id. [Flattened action: list] Bulk support: accepts payable_ids for batched execution.

### 67. `pagarme_payables_get`
**Input**: `payable_id` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional), `payable_ids` (opcional)

Recebíveis (payables) no Pagar.me V5. Ações: - list: lista recebíveis (page, size; data: status, payment_date, type, …). - get: recebível por payable_id. [Flattened action: get] Bulk support: accepts payable_ids for batched execution.

### 68. `pagarme_invoices_list`
**Input**: `invoice_id` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional), `invoice_ids` (opcional)

Faturas (invoices) de assinatura no Pagar.me V5. Ações: - list: lista faturas (page, size; data: subscription_id, customer_id, status, due_since/until). - get: fatura por invoice_id. [Flattened action: list] Bulk support: accepts invoice_ids for batched execution.

### 69. `pagarme_invoices_get`
**Input**: `invoice_id` (opcional), `page` (opcional), `size` (opcional), `data` (opcional), `account` (opcional), `invoice_ids` (opcional)

Faturas (invoices) de assinatura no Pagar.me V5. Ações: - list: lista faturas (page, size; data: subscription_id, customer_id, status, due_since/until). - get: fatura por invoice_id. [Flattened action: get] Bulk support: accepts invoice_ids for batched execution.

### 70. `pagarme_invoices_write`
**Input**: `invoice_id`, `status`, `account` (opcional), `invoice_ids` (opcional)

Altera o status de uma fatura no Pagar.me V5 (requer invoice_id + status, ex.: 'paid', 'canceled'). Bulk support: accepts invoice_ids for batched execution.

### 71. `pagarme_invoices_cancel`
**Input**: `invoice_id`, `account` (opcional), `invoice_ids` (opcional)

Cancela uma fatura no Pagar.me V5 (requer invoice_id). Irreversível. Bulk support: accepts invoice_ids for batched execution.

### 72. `pagarme_legacy_list_transactions`
**Input**: `transaction_id` (opcional), `data` (opcional), `account` (opcional), `transaction_ids` (opcional)

Leitura da API LEGADA V1–V4 do Pagar.me (modelo "transactions"). Ativa quando a conexão usa uma chave ak_… (contas ainda não migradas pra V5). As 4 versões legadas compartilham estes endpoints; diferenças de campo entre V1/V2/V3/V4 vêm cruas no payload. Ações: - list_transactions / get_transaction (requer transaction_id) - list_subscriptions / list_plans / list_payables / list_recipients / list_customers / list_transfers - balance: saldo da conta Filtros de lista (count, page, status, …) via data (JSON). [Flattened action: list_transactions] Bulk support: accepts transaction_ids for batched execution.

### 73. `pagarme_legacy_get_transaction`
**Input**: `transaction_id` (opcional), `data` (opcional), `account` (opcional), `transaction_ids` (opcional)

Leitura da API LEGADA V1–V4 do Pagar.me (modelo "transactions"). Ativa quando a conexão usa uma chave ak_… (contas ainda não migradas pra V5). As 4 versões legadas compartilham estes endpoints; diferenças de campo entre V1/V2/V3/V4 vêm cruas no payload. Ações: - list_transactions / get_transaction (requer transaction_id) - list_subscriptions / list_plans / list_payables / list_recipients / list_customers / list_transfers - balance: saldo da conta Filtros de lista (count, page, status, …) via data (JSON). [Flattened action: get_transaction] Bulk support: accepts transaction_ids for batched execution.

### 74. `pagarme_legacy_list_subscriptions`
**Input**: `transaction_id` (opcional), `data` (opcional), `account` (opcional), `transaction_ids` (opcional)

Leitura da API LEGADA V1–V4 do Pagar.me (modelo "transactions"). Ativa quando a conexão usa uma chave ak_… (contas ainda não migradas pra V5). As 4 versões legadas compartilham estes endpoints; diferenças de campo entre V1/V2/V3/V4 vêm cruas no payload. Ações: - list_transactions / get_transaction (requer transaction_id) - list_subscriptions / list_plans / list_payables / list_recipients / list_customers / list_transfers - balance: saldo da conta Filtros de lista (count, page, status, …) via data (JSON). [Flattened action: list_subscriptions] Bulk support: accepts transaction_ids for batched execution.

### 75. `pagarme_legacy_list_plans`
**Input**: `transaction_id` (opcional), `data` (opcional), `account` (opcional), `transaction_ids` (opcional)

Leitura da API LEGADA V1–V4 do Pagar.me (modelo "transactions"). Ativa quando a conexão usa uma chave ak_… (contas ainda não migradas pra V5). As 4 versões legadas compartilham estes endpoints; diferenças de campo entre V1/V2/V3/V4 vêm cruas no payload. Ações: - list_transactions / get_transaction (requer transaction_id) - list_subscriptions / list_plans / list_payables / list_recipients / list_customers / list_transfers - balance: saldo da conta Filtros de lista (count, page, status, …) via data (JSON). [Flattened action: list_plans] Bulk support: accepts transaction_ids for batched execution.

### 76. `pagarme_legacy_list_payables`
**Input**: `transaction_id` (opcional), `data` (opcional), `account` (opcional), `transaction_ids` (opcional)

Leitura da API LEGADA V1–V4 do Pagar.me (modelo "transactions"). Ativa quando a conexão usa uma chave ak_… (contas ainda não migradas pra V5). As 4 versões legadas compartilham estes endpoints; diferenças de campo entre V1/V2/V3/V4 vêm cruas no payload. Ações: - list_transactions / get_transaction (requer transaction_id) - list_subscriptions / list_plans / list_payables / list_recipients / list_customers / list_transfers - balance: saldo da conta Filtros de lista (count, page, status, …) via data (JSON). [Flattened action: list_payables] Bulk support: accepts transaction_ids for batched execution.

### 77. `pagarme_legacy_list_recipients`
**Input**: `transaction_id` (opcional), `data` (opcional), `account` (opcional), `transaction_ids` (opcional)

Leitura da API LEGADA V1–V4 do Pagar.me (modelo "transactions"). Ativa quando a conexão usa uma chave ak_… (contas ainda não migradas pra V5). As 4 versões legadas compartilham estes endpoints; diferenças de campo entre V1/V2/V3/V4 vêm cruas no payload. Ações: - list_transactions / get_transaction (requer transaction_id) - list_subscriptions / list_plans / list_payables / list_recipients / list_customers / list_transfers - balance: saldo da conta Filtros de lista (count, page, status, …) via data (JSON). [Flattened action: list_recipients] Bulk support: accepts transaction_ids for batched execution.

### 78. `pagarme_legacy_list_customers`
**Input**: `transaction_id` (opcional), `data` (opcional), `account` (opcional), `transaction_ids` (opcional)

Leitura da API LEGADA V1–V4 do Pagar.me (modelo "transactions"). Ativa quando a conexão usa uma chave ak_… (contas ainda não migradas pra V5). As 4 versões legadas compartilham estes endpoints; diferenças de campo entre V1/V2/V3/V4 vêm cruas no payload. Ações: - list_transactions / get_transaction (requer transaction_id) - list_subscriptions / list_plans / list_payables / list_recipients / list_customers / list_transfers - balance: saldo da conta Filtros de lista (count, page, status, …) via data (JSON). [Flattened action: list_customers] Bulk support: accepts transaction_ids for batched execution.

### 79. `pagarme_legacy_list_transfers`
**Input**: `transaction_id` (opcional), `data` (opcional), `account` (opcional), `transaction_ids` (opcional)

Leitura da API LEGADA V1–V4 do Pagar.me (modelo "transactions"). Ativa quando a conexão usa uma chave ak_… (contas ainda não migradas pra V5). As 4 versões legadas compartilham estes endpoints; diferenças de campo entre V1/V2/V3/V4 vêm cruas no payload. Ações: - list_transactions / get_transaction (requer transaction_id) - list_subscriptions / list_plans / list_payables / list_recipients / list_customers / list_transfers - balance: saldo da conta Filtros de lista (count, page, status, …) via data (JSON). [Flattened action: list_transfers] Bulk support: accepts transaction_ids for batched execution.

### 80. `pagarme_legacy_balance`
**Input**: `transaction_id` (opcional), `data` (opcional), `account` (opcional), `transaction_ids` (opcional)

Leitura da API LEGADA V1–V4 do Pagar.me (modelo "transactions"). Ativa quando a conexão usa uma chave ak_… (contas ainda não migradas pra V5). As 4 versões legadas compartilham estes endpoints; diferenças de campo entre V1/V2/V3/V4 vêm cruas no payload. Ações: - list_transactions / get_transaction (requer transaction_id) - list_subscriptions / list_plans / list_payables / list_recipients / list_customers / list_transfers - balance: saldo da conta Filtros de lista (count, page, status, …) via data (JSON). [Flattened action: balance] Bulk support: accepts transaction_ids for batched execution.

## Prompts de exemplo

```
Liste as cobranças pagas dos últimos 7 dias
Mostre as assinaturas ativas e suas próximas faturas
Qual o saldo do recebedor padrão e os próximos recebíveis?
```
