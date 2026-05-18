# Cycode public demo flows

Runnable GitHub Actions examples for [Cycode Cimon](https://github.com/CycodeLabs/cimon). Copy a workflow into your own repo, set the two secrets, dispatch.

Full Cimon documentation: [docs.cimon.build](https://docs.cimon.build/).

## Flows

### Attestation

- **Windows L3 attestation** — SLSA Build Level 3 provenance on a GitHub-hosted `windows-latest` runner. Two equivalent workflows: [`ci-attest-windows-l3.yml`](.github/workflows/ci-attest-windows-l3.yml) (via [`cycodelabs/cimon-action/attest@v1`](https://github.com/CycodeLabs/cimon-action)) and [`ci-attest-windows-l3-direct-exe.yml`](.github/workflows/ci-attest-windows-l3-direct-exe.yml) (direct `cimon.exe`). Identical signed envelopes; different install mechanisms.

### Prevent-mode hardening

Three dispatch-only workflows. Each is expected to fail red — that's the demonstration. The cimon job summary on the failed run shows what was blocked.

- [`prevent-block-network.yml`](.github/workflows/prevent-block-network.yml) — outbound call to a non-allowlisted host.
- [`prevent-block-base64-exec.yml`](.github/workflows/prevent-block-base64-exec.yml) — base64-decoded payload piped into a shell.
- [`prevent-block-secret-read.yml`](.github/workflows/prevent-block-secret-read.yml) — two-phase chain: extract a fake value from a sibling process, then attempt an outbound call.

## Running

Set two repository secrets:

- `CIMON_CLIENT_ID` — create at [app.cycode.com/cimon](https://app.cycode.com/cimon)
- `CIMON_SECRET` — paired secret

Then dispatch the workflow from the **Actions** tab. Every flow uses `on: workflow_dispatch:` only.

## Related

- [Windows & GHES guide](https://docs.cimon.build/provenance/integrations/windows-ghes)
- [Permissions reference](https://docs.cimon.build/overview/permissions)
- [Signing approaches](https://docs.cimon.build/provenance/signing-approaches)
- [`cycodelabs/cimon-action`](https://github.com/CycodeLabs/cimon-action)
- [`cycodelabs/cimon-releases`](https://github.com/cycodelabs/cimon-releases)
