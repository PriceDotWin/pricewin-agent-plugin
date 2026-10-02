# PriceWin plugin for coding agents

Live hotel and flight prices compared across Booking.com, Agoda, Trip.com and
Traveloka, in USD, from inside your coding agent. One package bundles:

- **`.mcp.json`**: the PriceWin MCP server, `https://mcp.price.win/mcp`
  (Streamable HTTP, no account, no API key);
- **`skills/pricewin-travel-search`**: how to run a search (results arrive in
  two steps), what to ask when the trip details are incomplete, and how to read
  prices and links.

The same files load in Claude Code, Codex CLI and ZCode: all three read
`.claude-plugin/plugin.json`, the plugin-root `.mcp.json` and `skills/`.

## Install

### Claude Code

```
/plugin marketplace add PriceDotWin/pricewin-agent-plugin
/plugin install pricewin@pricewin
```

### Codex CLI

```bash
codex plugin marketplace add PriceDotWin/pricewin-agent-plugin
codex plugin add pricewin@pricewin
```

Codex asks for approval before PriceWin calls: the search and booking tools
reach outside services, and their annotations say so (`openWorldHint: true`).

### ZCode

ZCode reads this package format. A listing in the ZCode plugin marketplace is
pending; this README will give the install step once it is live.

Then ask, for example:

> Compare hotel prices in Da Nang for 2 adults from November 10 to 12.

## Tools

| Tool | What it does |
|---|---|
| `search_hotels_live`, `poll_search_results` | Search a city's hotels across the OTAs and OpenTravel partner hotels; results arrive in two steps |
| `search_flights_live`, `poll_flight_results` | Search one-way or per-leg round-trip fares |
| `get_ota_hotel_detail` | Rooms, live prices, facilities and reviews for one named hotel (Booking.com) |
| `get_hotel_detail`, `get_hotel_info` | Rooms and prices, or facilities and policies, of an OpenTravel partner hotel |
| `get_cancellation_policy` | Refund terms for one rate |
| `request_booking`, `check_booking_status` | Send a booking request to a partner hotel and read its status |
| `request_cancel_token`, `cancel_booking` | Cancel such a booking, in two steps |

**Booking takes no money.** `request_booking` sends the guest's name, phone and
email to the hotel, which confirms the request; no room is held and the guest
pays at the property. Cancelling needs a single-use token that is emailed to the
address on the booking, so nothing is cancelled without the guest's own inbox.

## Data

Prices and links come from live searches of Booking.com, Agoda, Trip.com and
Traveloka, and from OpenTravel partner hotels. They are time-sensitive; book
through the link a result carries. No account is needed and no payment data is
ever requested. See the [privacy policy](https://www.price.win/en/privacy-policy)
and [terms of service](https://www.price.win/en/terms-of-service).

## Support

[mcp.price.win/support](https://mcp.price.win/support) · support@price.win ·
[tool reference](https://mcp.price.win/docs)

## License

MIT
