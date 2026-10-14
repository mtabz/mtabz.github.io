# Public-safe architecture

MCPFence separates deterministic identity resolution from optional probabilistic interpretation.

```text
Vendor name + optional official identifiers
                  |
                  v
          Candidate generation
                  |
        +---------+---------+
        |         |         |
       npm       PyPI   Official MCP Registry
        |         |         |
        +---------+---------+
                  |
        Provenance and surface rules
                  |
                  v
        Deterministic exposure map
          |                   |
          v                   v
      report.md       exposure_map.json
```

## Resolution layer

The resolver compares the obvious bare namespace with the vendor's probable official surfaces. It records whether each surface is open, occupied or vendor-owned, and whether an occupier chains back to a vendor-controlled domain, repository or recognised official listing.

The same input and frozen registry responses produce byte-for-byte reproducible output. Live HTTP responses are captured as cassettes for deterministic offline regression tests.

## Current live coverage

- npm
- PyPI
- Official MCP Registry

Independent MCP directory models and resolver paths exist and are tested against fixtures. Live adapters for those directories remain pending.

## Safety boundary

The current scanner relies on registry metadata and provenance evidence. Automated package archive inspection is deliberately deferred behind a safety spike. The product does not install or execute unknown MCP servers as part of a scan.

## Optional probabilistic layer

A separate agent-search spike tests whether reasoning agents discover the official server. It is not part of the deterministic product path and the core scan incurs no model or web-search cost.

A five-vendor Haiku 4.5 run measured an operating cost of approximately $0.063 per probe and reached the official server in four of five cases, compared with five of five for the Sonnet baseline. Because there was only one trial per vendor and search payloads varied, this is treated as a cost-and-quality signal rather than a definitive benchmark. Probabilistic interpretation remains bounded and subordinate to observable provenance facts.
