# Contributing

Foundry is an early beta. Focus contributions on a precise, dependable design-in-code loop: inspect, review, apply, rebuild, and verify.

## CI runner contract

The existing `validate` job uses Boat's compatible Linux runner. Its triggers,
read-only permissions and complete check/artifact chain are unchanged. Public
Boat execution is approved for owner `BumpyClock` only. Outside contributors and
bots remain blocked by account policy. No workflow was dispatched during migration.

The `publish` job remains on `ubuntu-latest`. Its npm trusted-publisher/OIDC and
provenance contracts require a GitHub-hosted runner. [npm's supported-provider
requirements](https://docs.npmjs.com/trusted-publishers/) exclude self-hosted
runners. Do not weaken provenance or replace authentication to move that job.
The protected `npm` environment, source-freshness checks and registry mutation
ordering remain unchanged. Local or sandbox checks never publish a release.

## Local development

1. Install Node.js 20 or newer and pnpm 10.
2. Run `pnpm install`.
3. Run `pnpm check` before proposing a change.
4. For browser-facing changes, run the web fixture and verify the complete review, apply, and rendered-result workflow.

Keep the runtime loopback-only, preserve explicit user review before source application, and never add telemetry or a cloud dependency without prior product discussion.

Open an issue before a large architectural change so the approach can be agreed before implementation.
