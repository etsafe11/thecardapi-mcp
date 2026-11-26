# The Card API MCP server

Connect an MCP client to The Card API with the API key you already use.

**Endpoint:** `https://www.thecardapi.com/api/mcp`

The server name is `thecardapi-mcp`, version 2.0.0. It exposes two tools.

## Tools

`find_catalog_cards` finds possible printings. Compare the candidates before treating one as the card. `query` is required. Optional arguments are `set_name`, `card_number`, `year`, and `limit` (maximum 12).

`search_sales` returns dated sales for a title search. `query` is required. Optional arguments are `grader`, `grade`, `graded`, `platform`, `listing_type`, `date_from`, `date_to`, and `limit` (maximum 100). A result is a title match. It does not by itself prove that every row is one exact printing.

Use a price in a paid-price comparison only when `price_confirmed` is true. An amount with `price_confirmed` false is not a confirmed paid price. `id` is the sale record. `listing_id` is the marketplace listing.

The response does not include card images.

Your key’s plan applies. The history window and the daily row allowance are the same ones the API enforces. When the allowance or request limit is reached, the tool result has `isError: true`. That result is not sales data.

Only these two tools are available. The server rejects any other name, including `search_cards`, `grade_impact_analysis`, `grader_comparison`, `price_momentum`, and `grading_value_calculator`.

## Claude Desktop

Add this block to `~/Library/Application Support/Claude/claude_desktop_config.json`.

```json
{
  "mcpServers": {
    "thecardapi": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://www.thecardapi.com/api/mcp",
        "--header",
        "Authorization: Bearer YOUR_API_KEY"
      ]
    }
  }
}
```

## Claude Code

```bash
claude mcp add --transport http thecardapi \
  https://www.thecardapi.com/api/mcp \
  --header "Authorization: Bearer YOUR_API_KEY"
```

## Cursor

Add this block to `~/.cursor/mcp.json`.

```json
{
  "mcpServers": {
    "thecardapi": {
      "url": "https://www.thecardapi.com/api/mcp",
      "headers": {
        "Authorization": "Bearer YOUR_API_KEY"
      }
    }
  }
}
```

## Windsurf

Add this block to `~/.codeium/windsurf/mcp_settings.json`.

```json
{
  "mcpServers": {
    "thecardapi": {
      "serverUrl": "https://www.thecardapi.com/api/mcp",
      "headers": {
        "Authorization": "Bearer YOUR_API_KEY"
      }
    }
  }
}
```

## Authentication

Pass the same API key you use for the REST API:

```
Authorization: Bearer YOUR_API_KEY
```

Availability and freshness vary by platform and date. Current data state: [thecardapi.com/status](https://www.thecardapi.com/status).

Setup for ChatGPT and LangChain, plus example prompts: [thecardapi.com/mcp](https://www.thecardapi.com/mcp).

API reference: [thecardapi.com/docs](https://www.thecardapi.com/docs).
