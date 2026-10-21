---
name: search-mzad
description: Search or browse Mzad Qatar public listings and auctions, find available category filters, compare returned prices and locations, or inspect a selected result. Use when the user asks to find something on Mzad Qatar or refers to a result from its marketplace.
---

# Search Mzad Qatar

Use the bundled `mzad-qatar` connector for its public marketplace tools. If the connector is not connected, explain the connection step instead of claiming a search ran. Follow the host's security and authorization requirements.

## Choose the tools

1. For a general browse such as “show the latest Mzad listings,” call `show_results` directly without a keyword or category constraint.
2. For a category, keyword, auction, or filtered request, call `catalog` in the user's language to resolve current categories and supported options. Use returned category IDs, filter names and exact option tokens; do not invent or reuse stale IDs/options.
3. Call `show_results` to display matches. Keyword display requires the resolved `category_id`. Use `search_scope=marketplace` only when the user explicitly requests a search across all categories. If the intended category is ambiguous, ask a focused question.
4. Use `search` when reusable data is needed for an explicit text comparison or analysis rather than listing cards. Preserve all user constraints; do not silently relax a price, category, location, or filter to obtain results. Explain unsupported filters.
5. For details, call `fetch` with the actual returned numeric-string `id` and its returned `kind`. Listings and auctions have separate ID namespaces. For auction requests, resolve the auction catalog and pass `kind=auction`.

## Present and refine

- Use `language=ar` for Arabic requests and `language=en` for English requests. Preserve Arabic text and RTL when the client supports it.
- When cards render, add at most a short summary in the user's language. Do not repeat every card in a second list or table unless the user asks for text or comparison.
- If the client cannot display cards, provide useful text and canonical links from returned structured data. A rendering failure is distinct from a failed search.
- Preserve query, language, price bounds, category, city, sort, kind and filters when paging. Follow returned `page`, `limit` and `has_more`; do not invent page counts. The app-only paging tool is for the widget. If the user asks for another page in chat, call `show_results` again with the retained criteria and requested page.
- Respect the backend result order. Matching paid VIP, Gold and Silver listings may precede normal listings; sort is secondary within those tiers. Do not describe promoted order as an unbiased price ranking.
- Report only returned facts, prices, currency, locations and links. Do not invent a price, stock, bid, seller detail or freshness timestamp. A new tool call reads the search index and does not guarantee instantaneous database state. Direct the user to the canonical listing for its current status.

## Empty, unavailable and unsupported actions

- An empty list is a valid no-results response: say no matches were returned and offer a useful refinement without an empty card box or fabricated inventory.
- For invalid filters, refresh `catalog` and make at most one corrected retry using valid bounded criteria. Keep the user's constraints or explain any unsupported value.
- If a selected listing is missing, say it is unavailable. If the search service fails, say it is temporarily unavailable. Do not present model memory or a silent database fallback as a successful current search.
- These tools are read-only. They do not expose private seller phone/email/WhatsApp or internal user IDs, post or edit ads, place bids, buy, pay, or send messages. Explain the limit and direct the user to Mzad's normal website/app for supported account actions.
- Do not call Mzad tools for unrelated questions such as weather.
