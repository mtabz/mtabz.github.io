# MCPFence evidence

> MCPFence closed in August 2026 after a no-go decision. This folder is kept as a record of the build.

Public-safe build evidence for **MCPFence**, a deterministic namespace-defence tool for MCP vendors.

This repository contains sanitised outputs from a working CLI, a redacted record/replay cassette, and a terminal transcript showing a live scan and the test suite. It intentionally does **not** contain the full resolver implementation, the private vendor corpus, or unredacted third-party identities.

> Product and CLI name: MCPFence (`mcpfence`).

## What works today

- Live queries against npm, PyPI and the official MCP Registry.
- Deterministic multi-channel name resolution and provenance-gap detection.
- Human-readable Markdown and machine-readable JSON output.
- 159 passing tests, including planted fixtures, a no-provenance decoy and frozen cassettes of registry responses.
- Typed, fixture-backed support for independent MCP directories. Live directory adapters are not yet implemented.

Package archive inspection is not automated yet. It is deferred behind a bounded safety spike.

## Three resolution outcomes

| Example | Outcome | What it demonstrates |
|---|---|---|
| `examples/1-open-occupied/` | Open and occupied | A differently named official package leaves the obvious bare namespace occupied by an unrelated publisher with no vendor provenance. |
| `examples/2-open-unclaimed/` | Open and unclaimed | A scoped official package leaves a latent namespace exposure, but no third-party accusation is implied. |
| `examples/3-clean-no-gap/` | No gap | The vendor owns the obvious bare name across the represented channels. |

The first two examples are sanitised real-world outputs. The third uses a synthetic vendor so the repository does not publicly assert that a real vendor is fully protected.

## Other evidence

- `evidence/terminal-transcript.txt` shows the CLI interface, a live scan and `159 passed`.
- `evidence/cassette-sample-redacted.json` is a frozen npm registry response used to keep offline test runs deterministic.
- `evidence/model-cost-experiment.md` records the measured Haiku/Sonnet cost-and-quality comparison for the optional search probe.
- `docs/product-decisions.md` explains why deterministic resolution replaced probabilistic agent search as the product core.
- `docs/architecture.md` describes the public-safe architecture and current boundaries.

## Responsible disclosure and sanitisation

Vendor names, publisher identities, contact details and identifying tool names are redacted. Do not replace these files with unredacted cassettes or reports: the private test corpus contains real third-party handles and email addresses.

## Not included

- Full resolver source code.
- Private 11-vendor corpus.
- Unredacted findings.
- Credentials or local configuration.
- Automated package archive inspector.

## Publishing checklist

1. Create a new personal repository named `mcpfence-evidence`.
2. Upload the contents of this folder, preserving the directory structure.
3. Review every file for identifying metadata before making the repository public.
4. Add the final GitHub URL to the portfolio's **Inspect evidence repository** link.
5. Add selected resolver tests later, after sanitising fixtures and removing private corpus references.

## Public repository

https://github.com/mtabz/mtabz.github.io
