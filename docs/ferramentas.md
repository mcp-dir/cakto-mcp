# Ferramentas

Cakto expõe 10 ferramentas (todas somente leitura).

### 1. `cakto_list_accounts`
**Input**: `account` (opcional)

Lista contas Cakto (apps do painel) vinculadas a este install — id, label e apelido.

### 2. `cakto_orders_list`
**Input**: `order_id` (opcional), `status` (opcional), `type` (opcional), `offer_type` (opcional), `payment_method` (opcional), `customer` (opcional), `product` (opcional), `paid_at_gte` (opcional), `paid_at_lt` (opcional), `page` (opcional), `account` (opcional), `order_ids` (opcional)

Leitura de pedidos na Cakto. Ações: - list: lista pedidos (filtros: status csv ex "paid,refunded", type unique|subscription, offer_type main|upsell|downsell|orderbump, payment_method, customer, product, paid_at_gte/pa…

### 3. `cakto_orders_get`
**Input**: `order_id` (opcional), `status` (opcional), `type` (opcional), `offer_type` (opcional), `payment_method` (opcional), `customer` (opcional), `product` (opcional), `paid_at_gte` (opcional), `paid_at_lt` (opcional), `page` (opcional), `account` (opcional), `order_ids` (opcional)

Leitura de pedidos na Cakto. Ações: - list: lista pedidos (filtros: status csv ex "paid,refunded", type unique|subscription, offer_type main|upsell|downsell|orderbump, payment_method, customer, product, paid_at_gte/pa…

### 4. `cakto_orders_analytics`
**Input**: `group_by` (opcional), `start_date` (opcional), `end_date` (opcional), `product` (opcional), `offer` (opcional), `account` (opcional)

Analytics de vendas na Cakto: métricas financeiras agregadas por canal/campanha.

### 5. `cakto_subscriptions_list`
**Input**: `subscription_id` (opcional), `status` (opcional), `payment_method` (opcional), `current_situation` (opcional), `search` (opcional), `ordering` (opcional), `limit` (opcional), `page` (opcional), `account` (opcional), `subscription_ids` (opcional)

Leitura de assinaturas na Cakto.

### 6. `cakto_subscriptions_get`
**Input**: `subscription_id` (opcional), `status` (opcional), `payment_method` (opcional), `current_situation` (opcional), `search` (opcional), `ordering` (opcional), `limit` (opcional), `page` (opcional), `account` (opcional), `subscription_ids` (opcional)

Leitura de assinaturas na Cakto.

### 7. `cakto_subscription_churn`
**Input**: `start_date` (opcional), `end_date` (opcional), `page` (opcional), `account` (opcional)

Assinaturas perdidas: lista canceladas/inativas do negócio + métricas agregadas (valor em risco, nº de clientes afetados).

### 8. `cakto_customers_list`
**Input**: `customer_id` (opcional), `search` (opcional), `page` (opcional), `account` (opcional), `customer_ids` (opcional)

Leitura de clientes na Cakto (para análise/CRM).

### 9. `cakto_customers_get`
**Input**: `customer_id` (opcional), `search` (opcional), `page` (opcional), `account` (opcional), `customer_ids` (opcional)

Leitura de clientes na Cakto (para análise/CRM).

### 10. `cakto_products`
**Input**: `search` (opcional), `page` (opcional), `account` (opcional)

Lista produtos da conta na Cakto (filtros opcionais: search, page).

## Prompts de exemplo

```
Quanto vendi na Cakto nos últimos 30 dias?
Liste os pedidos aprovados de hoje
Qual a taxa de churn das minhas assinaturas?
Quais são meus produtos mais vendidos?
```
