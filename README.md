# The Card API — MCP Server

> Real sold prices for trading cards, directly inside your AI.

Connect Claude, Cursor, Windsurf, ChatGPT, or any MCP-compatible client to **hundreds of thousands of true sold prices added daily** across eBay, Goldin, Heritage, Fanatics, and more — including **Best Offer prices** (the actual negotiated amount, which most data providers never show).

One URL. No setup beyond your API key. **Data updated daily.**

**[Get a free API key →](https://thecardapi.com)**

---

## Quickstart

**Claude Code**
```bash
claude mcp add thecardapi \
  --transport http \
  --url https://thecardapi.com/api/mcp \
  --header "Authorization: Bearer YOUR_API_KEY"
```

**Claude Desktop** (`~/Library/Application Support/Claude/claude_desktop_config.json`)
```json
{
  "mcpServers": {
    "thecardapi": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://thecardapi.com/api/mcp",
        "--header",
        "Authorization: Bearer YOUR_API_KEY"
      ]
    }
  }
}
```

**Cursor** (`~/.cursor/mcp.json`)
```json
{
  "mcpServers": {
    "thecardapi": {
      "url": "https://thecardapi.com/api/mcp",
      "headers": { "Authorization": "Bearer YOUR_API_KEY" }
    }
  }
}
```

**Windsurf** (`~/.codeium/windsurf/mcp_settings.json`)
```json
{
  "mcpServers": {
    "thecardapi": {
      "serverUrl": "https://thecardapi.com/api/mcp",
      "headers": { "Authorization": "Bearer YOUR_API_KEY" }
    }
  }
}
```

**LangChain (Python)**
```python
from langchain_mcp_adapters.client import MultiServerMCPClient

client = MultiServerMCPClient({
    "thecardapi": {
        "url": "https://thecardapi.com/api/mcp",
        "transport": "streamable_http",
        "headers": {"Authorization": "Bearer YOUR_API_KEY"},
    }
})
```

---

## Tools

### Market Data

| Tool | What it does |
|---|---|
| `search_cards` | Search hundreds of thousands of real sold prices added daily. Filter by card name, platform, grader, grade, listing type, date range, and price. Returns true Best Offer prices — the actual negotiated amount, not the list price. |
| `grade_impact_analysis` | Full PSA/BGS/SGC/CGC price ladder for any card — avg, median, and sale count per grade. Identifies the best-value grade: where the jump to the next grade up is steepest. |
| `grader_comparison` | PSA vs BGS vs SGC vs CGC for the same card and grade. Shows which grader commands the highest premium and by how much. |
| `grading_value_calculator` | Should you grade this card? Real cost math — all PSA/BGS/SGC/CGC tiers including bulk rates and shipping — vs actual market comps. Shows expected profit or loss at each grade. |
| `price_momentum` | Is this card trending up or down? Compares two equal time windows back-to-back and returns price change %, volume change %, and a momentum signal. |
| `seller_lookup` | Full profile on any seller: total sales, average price, feedback score, last active date, which grades they specialize in, and a trust signal. |
| `slab_lookup` | Enter a PSA/BGS/SGC/CGC serial number and see every time that specific physical card has sold, and how its price changed over time. Carfax for cards. |

### Want List

| Tool | What it does |
|---|---|
| `search_catalog` | Search a catalog of 9.7M+ cards by natural language. Returns ranked candidates with images. |
| `add_to_want_list` | Add a specific card to your want list with optional condition, grader, grade, and max price preferences. |
| `view_want_list` | View all cards currently on your want list. |
| `remove_from_want_list` | Remove a card from your want list. |

---

## Example prompts

```
What are PSA 10 Luka Doncic 2018 Prizm Silver rookies actually selling for
right now — true Best Offer prices, not just auctions?
```

```
I paid $6,500 for a raw 1986 Fleer Jordan. Is PSA grading it worth it,
and what grade do I need to break even?
```

```
For a grade 9 Wembanyama Prizm Silver, does PSA, CGC, or BGS command
the highest average sale price?
```

```
Pull the full transaction history for PSA cert 84566824 — every sale,
every price, has it appreciated?
```

```
Has the market for Charizard Base Set Holo PSA 10 been rising or falling
over the past two weeks — include volume.
```

```
Full seller profile on pwcc_auctions: total sales, average price,
what grades do they typically move.
```

---

## Why Best Offer prices matter

eBay hides the final accepted price on Best Offer listings. Most price trackers either skip these entirely or show the original list price — both of which distort the true market. The Card API captures the actual negotiated amount at time of sale, giving you a complete picture of what cards are really trading for.

---

## Data coverage

- **Platforms:** eBay (Auction, Fixed Price, Best Offer), Goldin, Heritage, Fanatics Vault, Pristine, REA, Alt, Sotheby's
- **Categories:** Baseball, basketball, football, hockey, soccer, Pokémon, Magic: The Gathering, Yu-Gi-Oh, and 30+ more
- **Graders:** PSA, BGS (Beckett), SGC, CGC
- **Updated:** Daily

---

## Authentication

All tools use the same API key as the REST API. Pass it as a Bearer token:

```
Authorization: Bearer tca_your_key_here
```

Your tier's rate limits apply automatically. The free tier is enough to explore all 11 tools.

**[Get your free key at thecardapi.com →](https://thecardapi.com)**

---

## Full documentation

REST API reference, response schemas, CSV export, and webhook docs:
**[thecardapi.com/docs](https://thecardapi.com/docs)**

MCP-specific setup for all clients:
**[thecardapi.com/mcp](https://thecardapi.com/mcp)**
