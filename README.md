# ElevenLabs MCP server

Search voice metadata and inspect model language/capability metadata to prepare a compatible audio workflow. Audio generation remains in the provider SDK, not this JSON connector.

A direct-provider MCP server with useful local execution. No PipMCP account is required for local use. Provider API access and any provider charges are your responsibility.

## Quick start

Requires Node.js22+. Clone this repository, then run:

```sh
npm ci --ignore-scripts
npm test
npm start
```

The default command inspects the tools offline. Configure your own credentials in your environment:

- `ELEVENLABS_API_KEY`



Credential help: https://api.elevenlabs.io/openapi.json

## Execute a real read

Replace example record IDs with records you are authorized to access.

```sh
npm start -- --call list_voices '{"search":"narration","page_size":10}'
```

## Use with an MCP client

Launch `node /absolute/path/elevenlabs-mcp/server.mjs` using stdio transport; pass credentials through the client environment. Stdout is reserved for JSON-RPC.

## Tools

| Tool | Effect | Purpose |
| --- | --- | --- |
| list_voices | Read | Search available voices with an explicit next-page token. |
| list_models | Read | Compare model capabilities and supported languages before selecting a voice workflow. |

## Concrete workflow

Search voice metadata and inspect model language/capability metadata to prepare a compatible audio workflow. Audio generation remains in the provider SDK, not this JSON connector.

1. list_voices
2. list_models

## Optional writes

Writes are disabled by default. Set CONNECTOR_ALLOW_WRITES=true and supply `_approval: {approved:true,idempotencyKey:"unique-request-id"}` on the specific call. Do not reuse a key for a different request. Uncertain outcomes are never automatically replayed; inspect the provider before another attempt.

## Capability evidence

Local: **Tested — HTTP fixtures and real stdio tools/call**. Managed: **Documented**. Provider authentication and live operations have not been established by these fixture tests. Evidence applies per operation and execution mode; setup discovery does not imply provider execution.

## Managed production

[Activate with PipMCP](https://pipmcp.com/github/start?app=elevenlabs&integration=elevenlabs-mcp&utm_source=github&utm_campaign=github-elevenlabs-mcp&utm_content=readme) when you want the hosted service.  Local credentials are not uploaded by this code. Review provider permissions in the managed onboarding. [Directory and related projects](https://jannikco.github.io/pipmcp-connectors/integrations/elevenlabs/).

## Provenance and maintenance

- https://api.elevenlabs.io/openapi.json

Maintainer:jannikco. MIT license for this code. See connector.json for selected operations and integration.json for evidence. Runtime dependencies retain their own licenses. Report sensitive issues through https://pipmcp.com/contact; do not post credentials or customer data in public issues.
