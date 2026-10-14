# Optional search-probe model economics

## Purpose

Test whether the probabilistic agent-search probe could be retained as a low-cost secondary signal after deterministic namespace resolution became the product core.

## Configuration

- Five vendors
- One trial per vendor
- Haiku 4.5
- Same probe configuration as the Sonnet baseline
- Web-search tool enabled; Haiku used the compatible `web_search_20250305` tool through automatic fallback

## Measured results

| model | total cost | cost / scan | input tokens | reached official |
|---|---:|---:|---:|---:|
| Haiku 4.5 | $0.315 | $0.063 | 195,508 | 4/5 |
| Sonnet baseline | $5.018 | $1.00 | 1,503,702 | 5/5 |

For one vendor, Haiku selected a community server where the Sonnet baseline reached the official server.

## Interpretation

The measured Haiku operating point is approximately $0.06 per scan. The raw cost ratio against this Sonnet subset should not be presented as a controlled model-to-model saving: web-search content injected into the context varied substantially, and the Sonnet subset contained heavy-input outliers.

The more defensible economic bounds are:

- **3× token-price advantage:** based on the model input and output price ratio.
- **Approximately 2.4× effective saving on light payloads:** the model-independent web-search fee does not shrink with the cheaper model and represented roughly one third of the Haiku run cost.

The quality result is also preliminary. Four successes in five single trials indicates a possible discovery-recall trade-off, not a stable error rate. More repeated trials are required before using Haiku where a miss carries material consequences.

## Product decision

- The deterministic resolution scan remains the customer-facing core and incurs no LLM or web-search cost.
- Haiku is a candidate for bounded, low-stakes behavioural probing.
- Stronger-model escalation or refusal to score should be used when the cheaper path does not meet an explicit quality threshold.
