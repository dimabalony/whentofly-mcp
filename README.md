# whentofly — flight search for AI agents (MCP)

**[whentofly.io](https://whentofly.io)** is a flexible-date flight search your AI agent can
use directly. Ask your agent *"cheapest round trip from Singapore to Tokyo in October,
5–9 days"* — it searches a whole date window, returns the cheapest real fares with booking
links, and tells you **whether the price is actually good** for that route (a verdict built
from historical price bands).

No API key. No signup. One tool, hosted remotely — nothing to run locally.

## Install

**Claude Code**
```bash
claude mcp add flights https://whentofly.io/mcp?ch=github
```

**Claude Desktop / claude.ai** — Settings → Connectors → *Add custom connector* →
`https://whentofly.io/mcp?ch=github`

**Cursor** — add to `mcp.json`:
```json
{
  "mcpServers": {
    "flights": { "url": "https://whentofly.io/mcp?ch=github" }
  }
}
```

**Any other MCP client** with remote (streamable HTTP) support: point it at
`https://whentofly.io/mcp`.

**ChatGPT** — use the [whentofly Custom GPT](https://whentofly.io) (MCP connectors are
Claude/Cursor-side for now).

## What the tool does

`search_flights` — find the cheapest round-trip in a flexible date window:

- **Flexible dates**: give a month or date range + min/max trip length (e.g. "5–9 days in
  October") — it scans every valid depart/return combination and sorts by price.
- **Price verdict**: each result is scored against the route's historical price bands —
  *good / typical / high* — so your agent can answer "should I buy now?", not just "what
  does it cost?".
- **Anywhere mode**: omit the destination (or say "anywhere") to get the cheapest
  destinations from your origin — "where can I fly cheapest from Berlin in September?"
- **Booking links** for every fare, airline names resolved, prices cross-checked against
  live Google Flights data on fresh searches.

### Example prompts

- "Find the cheapest round trip Singapore → Tokyo in October, 5 to 9 days."
- "Where can I fly the cheapest from Berlin for a week in September?"
- "Is $450 a good price for NYC → Lisbon in November? Check flexible dates."
- "Plan me the cheapest 10–14 day trip to Japan in the next 3 months."

## How it's funded (honesty section)

Free to use. Booking links are affiliate links (Aviasales/Kiwi) — if you book through
one, whentofly earns a small commission at no cost to you. Prices come from cached
airline-ticket data (Travelpayouts) cross-checked against Google Flights; always verify
the final price on the booking page.

## For developers

The same search is available as a plain JSON API — `https://whentofly.io/search`
([docs](https://whentofly.io/docs)). This repo hosts documentation for the hosted MCP
server; the service itself is closed-source.

Questions / feedback: [hello@whentofly.io](mailto:hello@whentofly.io) or open an issue here.
