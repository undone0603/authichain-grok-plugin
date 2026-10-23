# AuthiChain plugin for Grok Build

Check AuthiChain signed provenance records and QRON Living QR codes, and run a free
EU Digital Product Passport (DPP) readiness check, from inside Grok Build.

## Install

In Grok Build, open `/plugin`, search for **AuthiChain**, and install (once listed).

## What you get

- **MCP server** `authichain` at `https://authichain.com/mcp/free` (Streamable HTTP, no auth).
  Tools: `verify_record`, `scan_living_qr`, `query_provenance`, `dpp_readiness_check`,
  `get_pricing`, and a legacy `verify` tool the skill tells Grok not to use.
- **Skill** `authichain-verify`: when and how to call the tools, and what a result
  does and does not mean.
- **Command** `/authichain-verify <record JSON | QR link | demo | dpp <category>>`.

## Example prompts

- "/authichain-verify demo"
- "Check this AuthiChain record: { ... }"
- "Is my e-bike battery ready for the EU battery passport?"

## Network endpoints and credentials

- Calls only `https://authichain.com/mcp/free`. No credentials, no API key, no telemetry.
- Record JSON you pass is sent to that endpoint to be checked.
- No hooks, no shell commands, no local code execution.

## Limits

A check covers a record's Ed25519 signature and, if present, that the Polygon
transaction carries the record hash. It does not inspect a physical product or prove
a product is genuine. DPP readiness output is not legal advice. This plugin is made by
AuthiChain; it is not made, endorsed or reviewed by xAI.

## Links

- Reference verifier: https://github.com/undone0603/authichain-verify (npm `authichain-verify`)
- Record spec: https://github.com/undone0603/authichain-spec
- MCP Registry: `com.authichain/authichain`
- Contact: hello@authichain.com

## License

Apache-2.0. See `LICENSE`.
