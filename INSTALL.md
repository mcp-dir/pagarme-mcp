# Instalação rápida

Pagar.me é um servidor MCP remoto hospedado em `https://api.mcp.ai/p_pagarme`. Você não baixa nem roda nada localmente — só aponta seu cliente pra essa URL.

A auth acontece em runtime: clientes com **OAuth 2.1** (Claude Desktop, Cursor, VS Code recentes) abrem o browser na 1ª chamada (magic-link). Clientes sem OAuth recebem a tool `authenticate` — abra `https://app.mcp.ai/agent-auth`, faça login, copie o JWT e cole no chat.

---

## Claude (Web e Desktop)

[➕ Abrir no Claude e conectar](https://claude.ai/customize/connectors?modal=add-custom-connector&mcpName=Pagar.me&mcpServerUrl=https%3A%2F%2Fapi.mcp.ai%2Fp_pagarme)

Manual: [claude.ai/customize/connectors](https://claude.ai/customize/connectors) → **+** → **Adicionar conector personalizado** → `Pagar.me` / `https://api.mcp.ai/p_pagarme`.

Config file (legado): `~/Library/Application Support/Claude/claude_desktop_config.json` (macOS) ou `%APPDATA%\Claude\claude_desktop_config.json` (Windows):

```json
{ "mcpServers": { "pagarme": { "type": "http", "url": "https://api.mcp.ai/p_pagarme" } } }
```

## Cursor

[➕ Instalar no Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=pagarme&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9wYWdhcm1lIn0=)

`.cursor/mcp.json`:
```json
{ "mcpServers": { "pagarme": { "url": "https://api.mcp.ai/p_pagarme" } } }
```

## VS Code (Copilot Chat)

[➕ Instalar no VS Code](vscode:mcp/install?name=pagarme&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_pagarme%22%7D)

`.vscode/mcp.json`:
```json
{ "servers": { "pagarme": { "type": "http", "url": "https://api.mcp.ai/p_pagarme" } } }
```

## Outros clientes MCP

Qualquer cliente com **MCP over HTTP**. URL fixa:

```
https://api.mcp.ai/p_pagarme
```

Dúvidas? [pagarme@mcp.ai](mailto:pagarme@mcp.ai)
