# HousingFeed MCP server: US rental listings and rent statistics

A hosted [Model Context Protocol](https://modelcontextprotocol.io) server that gives AI assistants live US rental data:
apartments, houses and rooms, collected from property managers' own software and websites and from portals, re-read
every week.

**Server URL:** `https://housingfeed.com/mcp` (Streamable HTTP, no install, no key needed for the free tools)

Listed in the official MCP Registry as `com.housingfeed/rental-listings`.

## Tools

| Tool | Key | What it does |
|---|---|---|
| `rent_summary` | no | What rent costs in a US city or ZIP: number of listings and the median, 25th and 75th percentile monthly asking rent, overall and by bedrooms (studio, 1, 2, 3, 4+). Listings verified at the source in the last 30 days. |
| `search_rentals_sample` | no | Up to 10 live listings for a state, city, rent range, bedroom range or map box: rent, beds, baths, size, address, coordinates, photo, days listed and a link to the source. |
| `feed_status` | yes | The current version of your licensed market feed and this week's change counts. |
| `search_my_feed` | yes | Search the listings in your licensed feed by city, ZIP, rent, bedrooms or map box. |
| `feed_changes` | yes | Listings added, changed or removed in the latest weekly update. |

Example questions: *"What does a 2-bedroom rent for in Austin?"*, *"Show me apartments under $2,000 in Brooklyn"*,
*"How many studios are listed in Chicago and what do they cost?"*

## Add it to your client

**Claude (claude.ai or Claude Desktop):** Settings, Connectors, Add custom connector, URL `https://housingfeed.com/mcp`.

**Claude Code:**
```bash
claude mcp add --transport http housingfeed https://housingfeed.com/mcp
```

**Cursor** (`~/.cursor/mcp.json`):
```json
{ "mcpServers": { "housingfeed": { "url": "https://housingfeed.com/mcp" } } }
```

**VS Code** (`.vscode/mcp.json`):
```json
{ "servers": { "housingfeed": { "type": "http", "url": "https://housingfeed.com/mcp" } } }
```

For the key-gated feed tools, send your HousingFeed key as `Authorization: Bearer <key>`.

## About the data

- US only; asking rents in USD, before move-in concessions.
- Statistics count listings verified at the source in the last 30 days, $300 to $30,000 a month, rooms in shared homes
  excluded. A unit listed on two sources can count twice.
- Free results are for research and answering questions. Showing listings to the public (a search site, an app, a
  chatbot) needs a display licence: [housingfeed.com/display-feed](https://housingfeed.com/display-feed).

More: [housingfeed.com](https://housingfeed.com) · hello@housingfeed.com

This repository holds documentation and the registry entry only; the server itself is hosted by HousingFeed.
