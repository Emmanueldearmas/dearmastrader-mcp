# DearmasTrader MCP server

Run and inspect crypto trading bots, and backtest strategies on years of history, by talking to Claude (or any MCP client).

- **Endpoint (Streamable HTTP):** `https://app.dearmastrader.com/api/mcp`
- **Auth:** OAuth 2.1 with dynamic client registration and PKCE (discovery at `/.well-known/oauth-protected-resource`), or an API key pair in the `X-API-Key` and `X-Secret-Key` headers, created in *My account → API keys*.
- **Website:** https://dearmastrader.com · **Free account:** https://app.dearmastrader.com
- **Transport:** stateless Streamable HTTP, JSON responses. Protocol versions 2025-06-18, 2025-03-26, 2024-11-05.

## What you can do

- **Bots:** list, inspect, create (DCA, grid, Spot and futures), validate, start, pause and stop bots; change take profit and stop loss; read orders, trades, executions and PnL.
- **Exchanges:** Binance, Bybit, MEXC, OKX and Bitget accounts; balances, tickers and each exchange's minimum order.
- **Backtest lab:** single DCA, grid and rotating multi-pair backtests; searches of up to 10,000 configurations ranked by the **validation period** (data the search did not fit), with an optional drawdown cap; saved conclusions and insights across searches.

## Safety

- Bots are created **stopped**. Starting or stopping a non-demo bot moves real money, so the server tells the assistant to do it only when the user explicitly asks.
- API keys are scoped: read-only, trading and lab permissions are separate, and keys can be limited to IP addresses.
- Exchange keys are stored encrypted and the platform only asks for trading permissions, never withdrawals.

## Tools (28)

`list_bots`, `get_bot`, `create_bot`, `validate_bot`, `start_bot`, `pause_bot`, `stop_bot`, `update_bot_targets`, `get_bot_pnl`, `list_bot_orders`, `list_bot_trades`, `list_bot_executions`, `list_exchange_accounts`, `get_balances`, `get_ticker`, `get_minimum_order`, `run_backtest`, `run_grid_backtest`, `run_rotating_backtest`, `get_lab_quota`, `start_lab_search`, `list_lab_searches`, `get_lab_results`, `cancel_lab_search`, `lab_insights`, `save_lab_conclusion`, `list_lab_conclusions`, `delete_lab_conclusion`

## Connect

**Claude (web, desktop, mobile):** Settings → Connectors → *Add custom connector* → URL `https://app.dearmastrader.com/api/mcp` → sign in to DearmasTrader and approve.

**Claude Code:**

```bash
claude mcp add --transport http dearmastrader https://app.dearmastrader.com/api/mcp
```

**Any MCP client with headers:** URL above plus the headers `X-API-Key: <your key>` and `X-Secret-Key: <your secret>`.

## Example prompts

- "Run a lab search for SOL/USDT with a 40% drawdown cap and show me the best setups in the validation period."
- "How are my bots doing today? Which one has the worst PnL?"
- "Create a demo DCA bot on BTC/USDT with the best setup from that search, but don't start it."

Trading crypto involves risk. Past results do not guarantee future results.

---

## Resumen en español

Servidor MCP de DearmasTrader: manejás tus bots de trading cripto (DCA y grilla, en Binance, Bybit, MEXC, OKX y Bitget) y corrés búsquedas en el laboratorio conversando con Claude. Se agrega en Claude como «conector personalizado» con la URL `https://app.dearmastrader.com/api/mcp` e inicio de sesión en DearmasTrader (OAuth). Los bots se crean detenidos y el servidor le indica al asistente que sólo los encienda o detenga si la persona lo pide.
