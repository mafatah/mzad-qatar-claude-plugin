# Mzad Qatar for Claude

![Mzad Qatar](assets/mzad-qatar-logo.jpg)

Search public Mzad Qatar listings and auctions in Arabic or English. This plugin bundles the existing remote marketplace connector with a workflow skill for resolving current category filters, browsing results, comparing returned public details, and opening a selected listing on Mzad Qatar.

## Install and connect

1. In Claude, open **Customize → Plugins → Add → Upload plugin** and choose the package ZIP. The archive must contain `.claude-plugin/plugin.json` at its root, or inside one top-level plugin folder.
2. Open the installed plugin's **Connectors** tab and add or connect **mzad-qatar**. The remote endpoint is `https://chatgpt.mzadqatar.com/mcp`.
3. Open a conversation and ask for public listings. Account, organization, region, and platform policies still apply. An organization owner may need to enable the connector first.

The same plugin structure is compatible with Claude Code's plugin loading mechanism. Interactive cards depend on the host's MCP App support; text and returned listing links are the fallback. Installing a package does not itself prove connection or tool availability.

## Example requests

- “Show me the latest listings on Mzad Qatar.”
- “Find Toyota cars on Mzad Qatar and show the available filters.”
- “اعرض لي آيفون في مزاد قطر مع الفلاتر المتاحة.”
- “Show current auctions, then tell me more about the first result.”

## Scope and limitations

The connector reads public marketplace data. It does not provide private seller contact details, publish or edit ads, bid, buy, pay, or send messages. The existing backend supplies category IDs, filter options, result order and pagination. Matching VIP, Gold and Silver promoted listings may receive priority before normal listings.

Search results come from a synchronized index and may lag listing changes. Open the canonical Mzad listing to check its current status. Empty results, unavailable items, service errors and unsupported filters are reported explicitly; no inventory, price or freshness timestamp should be invented.

Search queries and selected result identifiers are sent to the declared Mzad MCP service to answer the request. The package contains configuration and Markdown instructions, with no executable hooks, local credential collection or additional destinations. Service data handling is governed by Mzad's published policy; this package does not assert that the remote service keeps no operational logs.

## Product and support

- [Mzad Qatar website](https://mzadqatar.com/)
- [Privacy policy](https://mzadqatar.com/en/privacy)
- [Support](https://mzadqatar.com/en/contact)
- [Terms](https://mzadqatar.com/en/terms)

These are the product's existing published links. Publication and compatibility checks are tracked separately from this package; this README does not claim directory approval or completion of client testing.

Copyright © 2026 EBDAA DIGITAL TECHNOLOGY WLL. Proprietary. All rights reserved.
