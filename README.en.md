# Cakto

### Your Cakto sales in Claude, ChatGPT and AI agents

Connect your Cakto account and read your sales in natural language: orders, revenue, subscriptions, churn, customers and products. Generate a Client ID and Client Secret with read scopes in the Cakto dashboard (under API) and connect in one click. Read-only, no tool changes anything in Cakto.

- 📊 **Orders and revenue**: list sales and read revenue analytics
- 🔁 **Subscriptions and churn**: track recurring revenue and cancellations
- 👥 **Customers and products**: query your base and catalog
- 🔒 **Read-only** · 🎁 **10 free calls per day**
- 🔑 **BYO connection**: Client ID + Client Secret from your Cakto dashboard
- 💬 **Works with any MCP client**: Claude Desktop, Cursor, VS Code, Cline, Continue

[Versão em português](README.md) · [Full docs (PT-BR)](docs/) · [Agent skill](skills/)

---

## One-click install

### Claude (Web and Desktop)

Anthropic unified MCP installation at `claude.ai/customize/connectors`. **The same link works for Claude Web and Claude Desktop** (just be logged in):

[➕ Open in Claude and connect](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

**Manual** (if the deeplink does not open): [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Add custom connector** → paste **Name** `Cakto` and **URL** `https://api.mcp.ai/p_cakto`.

### Cursor

[➕ Install Cakto in Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=cakto&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9jYWt0byJ9)

### VS Code (Copilot Chat)

[➕ Install Cakto in VS Code](vscode:mcp/install?name=cakto&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_cakto%22%7D)

### ChatGPT, Manus, OpenClaw and 40+ other clients

Works with any MCP client that speaks **MCP over HTTP**. The server URL is always:

```
https://api.mcp.ai/p_cakto
```

Per-client details: [INSTALL.md](INSTALL.md).

---

## Example prompts

```
How much did I sell on Cakto in the last 30 days?
List today's approved orders
What is the churn rate of my subscriptions?
What are my best-selling products?
```

---

## 10 tools available

| Tool | Description |
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

Details for each tool: [docs/ferramentas.md](docs/ferramentas.md) (PT-BR)

---

## Pricing

Plans start at a free tier. See [docs/precos.md](docs/precos.md) (PT-BR).

---

## Privacy & data protection

- **Read-only**, no tool changes data at the source.
- **Sub-processors**: Cakto, the LLM host you choose (Claude, ChatGPT, Cursor, your own agent). Full list in [docs/privacidade-lgpd.md](docs/privacidade-lgpd.md).
- Data returned by the tools is sent to **the LLM host you choose**, a sub-processor outside our control. We recommend plans with training opt-out.

---

## FAQ

**How do I connect?**
Generate a Client ID and Client Secret with read scopes in the Cakto dashboard (under API) and paste them into the connection. It is read-only.

**Does it change anything in my Cakto account?**
No. Every tool is read-only: orders, revenue analytics, subscriptions, churn, customers and products.

**How much does it cost?**
The first 10 calls per day are free. After that, by subscription (see docs/precos.md).

**Is the server open source?**
The server is proprietary (hosted). This repository is the public wrapper with manifests, docs and skills, all MIT.


---

## Support

- 📧 [cakto@mcp.ai](mailto:cakto@mcp.ai)
- 🐛 [GitHub Issues](https://github.com/mcp-dir/cakto-mcp/issues)
- 📄 [docs/](docs/)

---

## License

MIT — see [LICENSE](LICENSE). The MCP server at `api.mcp.ai/p_cakto` is proprietary (hosted); this repo (manifests, docs, skills) is MIT.
