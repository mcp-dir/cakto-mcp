---
name: cakto-mcp
description: Lê os dados de vendas da Cakto (gateway de checkout pra infoprodutores) via API oficial: pedidos, analytics de faturamento, assinaturas, churn, clientes e produtos. Use quando o usuário pedir métricas de vendas, faturamento, recorrência ou base de clientes da Cakto. Orquestra cakto_orders, cakto_orders_analytics, cakto_subscriptions, cakto_subscription_churn, cakto_customers e cakto_products do servidor remoto em https://api.mcp.ai/p_cakto.
---

# Cakto — REST API skill

Você tem acesso à **Cakto** REST API na MCP.AI.

> Conecte sua conta Cakto e leia suas vendas por linguagem natural: pedidos, faturamento, assinaturas, churn, clientes e produtos. Gere um Client ID e um Client Secret com escopos de leitura no Painel Cakto (em API) e conecte em um clique. Somente leitura, nenhuma ferramenta altera dados na Cakto.

## Base URL

```
https://api.mcp.ai/api/cakto
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
curl -X POST https://api.mcp.ai/api/cakto/customers/get \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/cakto/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (10)

#### `cakto_customers_get`

Leitura de clientes na Cakto (para análise/CRM). _(POST /api/cakto/customers/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `customer_id` | string | Não | Obrigatório para get |
| `search` | string | Não | Busca por nome, email ou documento |
| `page` | integer | Não |  |
| `account` | string | Não | Opcional quando há várias contas Cakto vinculadas a este install (id, label ou trecho do client_id). Use cakto_list_accounts pra ver as opções; omita se só houver uma. |
| `customer_ids` | string[] | Não | Bulk mode: multiple values for customer_id |

#### `cakto_customers_list`

Leitura de clientes na Cakto (para análise/CRM). _(POST /api/cakto/customers/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `customer_id` | string | Não | Obrigatório para get |
| `search` | string | Não | Busca por nome, email ou documento |
| `page` | integer | Não |  |
| `account` | string | Não | Opcional quando há várias contas Cakto vinculadas a este install (id, label ou trecho do client_id). Use cakto_list_accounts pra ver as opções; omita se só houver uma. |
| `customer_ids` | string[] | Não | Bulk mode: multiple values for customer_id |

#### `cakto_list_accounts`

Lista contas Cakto (apps do painel) vinculadas a este install — id, label e apelido. _(POST /api/cakto/list/accounts)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Opcional quando há várias contas Cakto vinculadas a este install (id, label ou trecho do client_id). Use cakto_list_accounts pra ver as opções; omita se só houver uma. |

#### `cakto_orders_analytics`

Analytics de vendas na Cakto: métricas financeiras agregadas por canal/campanha. _(POST /api/cakto/orders/analytics)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `group_by` | string | Não | Dimensão de análise (utm_source, utm_medium, utm_campaign) |
| `start_date` | string | Não | Início (DD-MM-YYYY) |
| `end_date` | string | Não | Fim (DD-MM-YYYY) |
| `product` | string | Não | Filtra por produto |
| `offer` | string | Não | Filtra por oferta |
| `account` | string | Não | Opcional quando há várias contas Cakto vinculadas a este install (id, label ou trecho do client_id). Use cakto_list_accounts pra ver as opções; omita se só houver uma. |

#### `cakto_orders_get`

Leitura de pedidos na Cakto. _(POST /api/cakto/orders/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `order_id` | string | Não | Obrigatório para get |
| `status` | string | Não | Status, múltiplos separados por vírgula (ex: paid,refunded) |
| `type` | string | Não | Tipo do produto: unique ou subscription |
| `offer_type` | string | Não | main, upsell, downsell ou orderbump |
| `payment_method` | string | Não | Método de pagamento |
| `customer` | string | Não | Id, nome, email ou documento do cliente |
| `product` | string | Não | Id ou nome do produto |
| `paid_at_gte` | string | Não | Pago a partir de (YYYY-MM-DD) → paidAt__gte |
| `paid_at_lt` | string | Não | Pago antes de (YYYY-MM-DD) → paidAt__lt |
| `page` | integer | Não |  |
| `account` | string | Não | Opcional quando há várias contas Cakto vinculadas a este install (id, label ou trecho do client_id). Use cakto_list_accounts pra ver as opções; omita se só houver uma. |
| `order_ids` | string[] | Não | Bulk mode: multiple values for order_id |

#### `cakto_orders_list`

Leitura de pedidos na Cakto. _(POST /api/cakto/orders/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `order_id` | string | Não | Obrigatório para get |
| `status` | string | Não | Status, múltiplos separados por vírgula (ex: paid,refunded) |
| `type` | string | Não | Tipo do produto: unique ou subscription |
| `offer_type` | string | Não | main, upsell, downsell ou orderbump |
| `payment_method` | string | Não | Método de pagamento |
| `customer` | string | Não | Id, nome, email ou documento do cliente |
| `product` | string | Não | Id ou nome do produto |
| `paid_at_gte` | string | Não | Pago a partir de (YYYY-MM-DD) → paidAt__gte |
| `paid_at_lt` | string | Não | Pago antes de (YYYY-MM-DD) → paidAt__lt |
| `page` | integer | Não |  |
| `account` | string | Não | Opcional quando há várias contas Cakto vinculadas a este install (id, label ou trecho do client_id). Use cakto_list_accounts pra ver as opções; omita se só houver uma. |
| `order_ids` | string[] | Não | Bulk mode: multiple values for order_id |

#### `cakto_products`

Lista produtos da conta na Cakto (filtros opcionais: search, page). _(POST /api/cakto/products)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `search` | string | Não |  |
| `page` | integer | Não |  |
| `account` | string | Não | Opcional quando há várias contas Cakto vinculadas a este install (id, label ou trecho do client_id). Use cakto_list_accounts pra ver as opções; omita se só houver uma. |

#### `cakto_subscription_churn`

Assinaturas perdidas: lista canceladas/inativas do negócio + métricas agregadas (valor em risco, nº de clientes afetados). _(POST /api/cakto/subscription/churn)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `start_date` | string | Não | Início (YYYY-MM-DD) |
| `end_date` | string | Não | Fim (YYYY-MM-DD) |
| `page` | integer | Não |  |
| `account` | string | Não | Opcional quando há várias contas Cakto vinculadas a este install (id, label ou trecho do client_id). Use cakto_list_accounts pra ver as opções; omita se só houver uma. |

#### `cakto_subscriptions_get`

Leitura de assinaturas na Cakto. _(POST /api/cakto/subscriptions/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `subscription_id` | string | Não | Obrigatório para get |
| `status` | string | Não | Status da assinatura |
| `payment_method` | string | Não |  |
| `current_situation` | string | Não | new = recém-criada, renewed = já renovada (new, renewed) |
| `search` | string | Não | Busca por cliente, produto, oferta, pedido ou pagamento |
| `ordering` | string | Não | Ordenação (status|amount|paymentMethod|createdAt|updatedAt|canceledAt|next_payment_date) |
| `limit` | integer | Não |  |
| `page` | integer | Não |  |
| `account` | string | Não | Opcional quando há várias contas Cakto vinculadas a este install (id, label ou trecho do client_id). Use cakto_list_accounts pra ver as opções; omita se só houver uma. |
| `subscription_ids` | string[] | Não | Bulk mode: multiple values for subscription_id |

#### `cakto_subscriptions_list`

Leitura de assinaturas na Cakto. _(POST /api/cakto/subscriptions/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `subscription_id` | string | Não | Obrigatório para get |
| `status` | string | Não | Status da assinatura |
| `payment_method` | string | Não |  |
| `current_situation` | string | Não | new = recém-criada, renewed = já renovada (new, renewed) |
| `search` | string | Não | Busca por cliente, produto, oferta, pedido ou pagamento |
| `ordering` | string | Não | Ordenação (status|amount|paymentMethod|createdAt|updatedAt|canceledAt|next_payment_date) |
| `limit` | integer | Não |  |
| `page` | integer | Não |  |
| `account` | string | Não | Opcional quando há várias contas Cakto vinculadas a este install (id, label ou trecho do client_id). Use cakto_list_accounts pra ver as opções; omita se só houver uma. |
| `subscription_ids` | string[] | Não | Bulk mode: multiple values for subscription_id |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_cakto` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).
