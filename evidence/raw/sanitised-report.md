# Exposure map: vendorco

## finding

your official surface is vendorco-api-mcp (differently-named), so the bare name vendorco-mcp is open on npm, occupied today by third-party-A which requests API_TOKEN and exposes create_record, delete_record, update_settings, deploy_service, list_resources, get_account.

## channels

### npm — vendorco-mcp
- official surface: vendorco-api-mcp (differently-named)
- state: OPEN, occupied  (confidence: high)
- occupier: third-party-A [impersonator]
- requests credentials: API_TOKEN
- tools: create_record, delete_record, update_settings, deploy_service, list_resources, get_account
- provenance: NO chain back to the vendor

### directories — vendorco-api-mcp-fork
- official surface: vendorco-api-mcp (unknown)
- state: OPEN, occupied  (confidence: high)
- occupier: vendorco-api-mcp-fork [community]
- provenance: NO chain back to the vendor
- note: crawled tier

### directories — vendorco-mcp
- official surface: vendorco-api-mcp (unknown)
- state: OPEN, occupied  (confidence: high)
- occupier: vendorco-mcp [impersonator]
- provenance: NO chain back to the vendor
- note: crawled tier

### directories — vendorco-tools
- official surface: vendorco-api-mcp (unknown)
- state: OPEN, occupied  (confidence: high)
- occupier: vendorco-tools [unknown]
- provenance: NO chain back to the vendor
- note: crawled tier; provenance gap: no chain back to the vendor

### pypi — vendorco-mcp
- official surface: (none) (differently-named)
- state: OPEN, unoccupied  (confidence: high)
- note: bare name open, not currently occupied

### official_registry — vendorco
- official surface: io.github.vendorco/vendorco-api-mcp (bare-name-owned)
- state: bare-name-owned, no gap  (confidence: high)
- note: official listing present
