# Product decisions

## 1. Move from agent selection to producer-side namespace defence

The first hypothesis was that an agent searching for an MCP server might select an impersonating or unofficial result. A Sonnet-based search probe reached the official server in 29 of 30 trials. Meanwhile, deterministic inspection of an initial vendor sample found that three of seven vendors with scoped, remote or differently named official surfaces had their obvious bare package name occupied.

That evidence changed the product direction. The working core became a producer-side exposure map: identify the official surface, enumerate obvious namespace variants, determine whether they are open or occupied, and verify whether an occupier has provenance back to the vendor.

The probabilistic search probe was retained as a secondary behavioural signal rather than discarded. This preserves an evaluation path for future questions about agent discovery while keeping the customer-facing finding reproducible and explainable.

## 2. Prefer deterministic facts over an opaque score

Each finding reports the surface, state, occupier, provenance evidence and confidence. The tool does not ask a model to rediscover registry facts that code can establish more cheaply and consistently.

## 3. Treat inference economics and quality as architectural inputs

The first Sonnet search-probe runs showed that fetched web content, injected into context as input tokens, dominated the cost of the probabilistic path. A wider Sonnet test set used 6,211,159 input tokens and 90 web searches across 30 trials, for a metered cost of $21.24.

I then ran Haiku 4.5 on the same five-vendor configuration as a Sonnet baseline, one trial per vendor:

| model | total cost | cost / scan | input tokens | reached official |
|---|---:|---:|---:|---:|
| Haiku 4.5 | $0.315 | $0.063 | 195,508 | 4/5 |
| Sonnet baseline | $5.018 | $1.00 | 1,503,702 | 5/5 |

The absolute Haiku operating point is measured and useful: about six cents per scan. The raw approximately 16× difference is not a clean model comparison because web-search payloads varied substantially and the Sonnet subset contained heavy-input outliers. The defensible pricing interpretation is:

- model token prices favour Haiku by 3×;
- the flat web-search fee is model-independent;
- on light payloads that fee dampens the effective saving to roughly 2.4×;
- Haiku produced one discovery miss in five trials, so lower cost cannot be treated as equivalent quality without more repetitions.

The architectural response was broader than changing models:

1. Keep deterministic resolution as the product core; it uses no model and incurs no web-search cost.
2. Retain the probabilistic probe only as an optional behavioural signal.
3. Use a lower-cost model for bounded, low-stakes probing when its quality threshold is met.
4. Escalate to a stronger model, or decline to score, when ambiguity or recall requirements warrant it.
5. Measure cost and quality together rather than optimising either in isolation.

## 4. Make the exposure audit the first sellable output

The earliest product is a one-off, evidence-backed exposure audit. The recurring product extends the same resolution layer into namespace monitoring, defensive claims, provenance issuance and managed response. The recurring product was not built: the project closed at the audit stage after a no-go decision in August 2026.
