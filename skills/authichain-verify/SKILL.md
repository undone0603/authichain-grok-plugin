---
name: authichain-verify
description: >-
  Check an AuthiChain signed provenance record, a QRON Living QR code, or EU Digital
  Product Passport readiness with the AuthiChain MCP server. Use when the user mentions
  AuthiChain, QRON, an authichain.com or qron.space link, an AuthiChain record JSON, or
  asks for an AuthiChain DPP readiness check.
---

# AuthiChain record and QR checks

The bundled `authichain` MCP server (`https://authichain.com/mcp/free`) exposes free tools.
No account, API key or payment is needed.

| Task | Tool |
|---|---|
| Check an Ed25519 signed provenance record and its optional Polygon anchor | `verify_record` |
| Read a stored QRON Living QR (from a `qron/r/{object_id}` link) | `scan_living_qr` |
| Look up a published asset id, seal or QR token | `query_provenance` |
| Score EU Digital Product Passport readiness for a product category | `dpp_readiness_check` |

## How to use

1. If the user gives a record JSON, pass it as `record` (and `anchor` if present) to
   `verify_record`. To try the published demonstration record, pass `id: "polygon-anchor-1"`.
2. If the user gives a QRON / AuthiChain QR link, extract the `object_id` and call
   `scan_living_qr`.
3. For DPP readiness, ask for the product category and the yes/no answers the tool
   accepts, then call `dpp_readiness_check`.
4. Report the verdict exactly as returned (`verified`, `valid-unanchored`, `invalid`,
   or `unknown`), the reasons, and the tool's `limits` text.

## What a result does and does not mean

- A `verified` verdict means the record's signature checks out against the listed
  signer key and, if anchored, the blockchain transaction carries the record hash.
- It does **not** inspect a physical product, prove a product is genuine, or say
  anything about who the signer is beyond the key. Records marked `demonstration`
  are examples, not production issuers.
- DPP readiness scores are a self-assessment aid, not legal advice.
- Do not call the legacy `verify` (x402) tool; use `verify_record` instead.

Open-source reference verifier: https://github.com/undone0603/authichain-verify
(npm `authichain-verify`). Record format: https://github.com/undone0603/authichain-spec
