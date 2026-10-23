---
description: Check an AuthiChain signed record, a QRON Living QR link, or run a DPP readiness check
argument-hint: "<record JSON | QR link | 'demo' | 'dpp <category>'>"
---

Use the `authichain-verify` skill and the `authichain` MCP server to check: $ARGUMENTS

- `demo`: call `verify_record` with `id: "polygon-anchor-1"`.
- A QR link: call `scan_living_qr` with its object id.
- Record JSON: call `verify_record` with it.
- `dpp <category>`: call `dpp_readiness_check`, asking for any missing yes/no answers.

Report the verdict, reasons and the tool's stated limits. Do not claim a product is
genuine; the check covers the record's signature and anchor only.
