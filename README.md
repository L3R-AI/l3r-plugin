# <img src=".claude-plugin/icon.png" alt="" width="40" height="40" align="absmiddle"> L3R Plugin

US property lookups for AI agents: the L3R MCP server plus a skill for using it.

1. **MCP server:** the read-only [L3R MCP Server](https://github.com/L3R-AI/l3r-mcp) at `https://mcp.l3r.io/mcp`. Property, zoning, hazard, Census and energy facts, with a map of the lot, for any US address or parcel number. If you already have the L3R connector, you see one set of tools, not two.
2. **Skill:** `l3r-property` tells Claude which tool answers which question, to look up one property per call, to show each answer card as returned, and to treat a missing value as not held.

Free, read-only, no account.

## Install

**Claude:** add **L3R** from the plugin directory, then connect it from the plugin's **Connectors** tab.

**Claude Code:**

```sh
claude --plugin-dir ./l3r-plugin
```

Tools, coverage and limits: [L3R MCP Server](https://github.com/L3R-AI/l3r-mcp).

## Data

The plugin runs no code and fetches nothing itself. When Claude calls an L3R tool, the address, parcel number or ID goes to `mcp.l3r.io`, which also sees your network address and does not log the address you typed. Addresses L3R doesn't hold are looked up with the U.S. Census Bureau's public geocoder. Answers come from public records and never include owners, values or sales.

[Terms of use](https://mcp.l3r.io/terms) and [privacy policy](https://mcp.l3r.io/privacy).

For municipal code, permits and rights, visit [3drights.com](https://3drights.com).

## Contact

- Feedback: [feedback@l3r.io](mailto:feedback@l3r.io)
- Questions: [mcp@l3r.io](mailto:mcp@l3r.io)

---

Built by L3R, Real Property Intelligence
