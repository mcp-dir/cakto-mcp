# Cakto

### Suas vendas da Cakto no Claude, ChatGPT e agentes de IA

Conecte sua conta Cakto e leia suas vendas por linguagem natural: pedidos, faturamento, assinaturas, churn, clientes e produtos. Gere um Client ID e um Client Secret com escopos de leitura no Painel Cakto (em API) e conecte em um clique. Somente leitura, nenhuma ferramenta altera dados na Cakto.

- 📊 **Pedidos e faturamento**: liste vendas e veja analytics de receita
- 🔁 **Assinaturas e churn**: acompanhe recorrência e cancelamentos
- 👥 **Clientes e produtos**: consulte sua base e o catálogo
- 🔒 **Somente leitura** · 🎁 **10 chamadas grátis por dia**
- 🔑 **Conexão BYO**: Client ID + Client Secret gerados no seu Painel Cakto
- 💬 **Funciona com qualquer cliente MCP**: Claude Desktop, Cursor, VS Code, Cline, Continue

[English version](README.en.md) · [Documentação completa](docs/) · [Skill pra agentes](skills/)

---

## Instalar em 1 clique

### Claude (Web e Desktop)

A Anthropic unificou a instalação de MCPs em `claude.ai/customize/connectors`. **O mesmo link serve pra Claude Web e Claude Desktop** (basta estar logado):

[➕ Abrir no Claude e conectar](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

**Manual** (se o deeplink não abrir): [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Adicionar conector personalizado** → cole **Nome** `Cakto` e **URL** `https://api.mcp.ai/p_cakto`.

### Cursor

[➕ Instalar Cakto no Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=cakto&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9jYWt0byJ9)

### VS Code (Copilot Chat)

[➕ Instalar Cakto no VS Code](vscode:mcp/install?name=cakto&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_cakto%22%7D)

### ChatGPT, Manus, OpenClaw e mais 40+ clientes

Funciona em qualquer cliente MCP que suporte **MCP over HTTP**. A URL do servidor é sempre:

```
https://api.mcp.ai/p_cakto
```

Detalhes por cliente: [INSTALL.md](INSTALL.md).

---

## Exemplos de uso

```
Quanto vendi na Cakto nos últimos 30 dias?
Liste os pedidos aprovados de hoje
Qual a taxa de churn das minhas assinaturas?
Quais são meus produtos mais vendidos?
```

---

## 10 ferramentas disponíveis

| Tool | Descrição |
|---|---|
| `cakto_list_accounts` | Lista contas Cakto (apps do painel) vinculadas a este install — id, label e apelido. |
| `cakto_orders_list` | Leitura de pedidos na Cakto. Ações: - list: lista pedidos (filtros: status csv ex "paid,refunded", type unique|subscription, offer_type main|upsell|downsell|orderbump, payment_method, customer, product, paid_at_gte/pa… |
| `cakto_orders_get` | Leitura de pedidos na Cakto. Ações: - list: lista pedidos (filtros: status csv ex "paid,refunded", type unique|subscription, offer_type main|upsell|downsell|orderbump, payment_method, customer, product, paid_at_gte/pa… |
| `cakto_orders_analytics` | Analytics de vendas na Cakto: métricas financeiras agregadas por canal/campanha. |
| `cakto_subscriptions_list` | Leitura de assinaturas na Cakto. |
| `cakto_subscriptions_get` | Leitura de assinaturas na Cakto. |
| `cakto_subscription_churn` | Assinaturas perdidas: lista canceladas/inativas do negócio + métricas agregadas (valor em risco, nº de clientes afetados). |
| `cakto_customers_list` | Leitura de clientes na Cakto (para análise/CRM). |
| `cakto_customers_get` | Leitura de clientes na Cakto (para análise/CRM). |
| `cakto_products` | Lista produtos da conta na Cakto (filtros opcionais: search, page). |

Detalhe de cada tool: [docs/ferramentas.md](docs/ferramentas.md)

---

## Preços

Planos a partir do tier grátis. Veja [docs/precos.md](docs/precos.md).

---

## Privacidade & LGPD

- **Somente leitura**, nenhuma ferramenta altera dados na origem.
- **Sub-processadores**: Cakto, o LLM host que você escolher (Claude, ChatGPT, Cursor, agente próprio). Lista completa em [docs/privacidade-lgpd.md](docs/privacidade-lgpd.md).
- Os dados retornados pelas tools são enviados ao **LLM host que você escolher**, sub-processador fora do nosso controle. Recomendamos planos com opt-out de treinamento.

---

## Perguntas frequentes

**Como conecto?**
Gere um Client ID e um Client Secret com escopos de leitura no Painel Cakto, em API, e cole na conexão. A conexão é somente leitura.

**Altera algo na minha conta Cakto?**
Não. Todas as ferramentas são somente leitura: pedidos, analytics de faturamento, assinaturas, churn, clientes e produtos.

**Quanto custa?**
As 10 primeiras chamadas por dia são grátis. Depois, por assinatura (veja docs/precos.md).

**O servidor é open source?**
O servidor é proprietário (hosted). Este repositório é o wrapper público com manifestos, docs e skills, tudo MIT.


---

## Suporte

- 📧 [cakto@mcp.ai](mailto:cakto@mcp.ai)
- 🐛 [GitHub Issues](https://github.com/mcp-dir/cakto-mcp/issues)
- 📄 [docs/](docs/)

---

## Licença

MIT — veja [LICENSE](LICENSE). O servidor MCP em `api.mcp.ai/p_cakto` é proprietário (hosted); este repositório (manifestos, docs, skills) é MIT.
