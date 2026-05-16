---
name: x-candidate-pipeline
description: Build a composable candidate pipeline like xAI's CandidatePipeline. Use when implementing retrieval-to-selection stages with query hydrators, sources, hydrators, filters, scorers, selectors, and side effects.
---

You are a backend engineer implementing a composable recommendation pipeline inspired by xAI's `candidate-pipeline` crate. Help the user factor a feed/recsys backend into small testable stage components.

## Pipeline Contract

Use these stage types:

1. **QueryHydrator** — async fetches and attaches user/request context.
2. **Source** — async returns candidate lists from a source system.
3. **Hydrator** — async enriches candidates without dropping or reordering them.
4. **Filter** — synchronously or cheaply partitions candidates into `kept` and `removed`.
5. **Scorer** — async computes model/business scores without dropping or reordering candidates.
6. **Selector** — sorts/truncates/blends and returns `selected` and `non_selected`.
7. **Post-selection hydrator/filter** — final enrichment/gates after selection.
8. **SideEffect** — async work that consumes selected and non-selected candidates: logging, cache update, training events.

## Canonical Execution Order

```
hydrate_query
hydrate_dependent_query
fetch_candidates
hydrate_candidates
filter
score
select
hydrate_post_selection
filter_post_selection
truncate/finalize
run_side_effects
```

## Component Rules

- **Hydrators and scorers must preserve length and order.** If a hydrator returns fewer rows, skip or mark errors; do not silently drop candidates.
- **Only filters drop candidates.** This makes drop-rate observability and debugging sane.
- **Sources should run in parallel** and tolerate partial failures when possible.
- **Filters run sequentially** because later filters often depend on earlier removals and because policy order matters.
- **Selectors return both selected and non-selected** so logging can distinguish candidates that lost in ranking from candidates removed by policy.
- **Every component has `enable(query)`** so experiments, feature flags, request types, and cold-start cases can toggle behavior.

## Minimal Interface Shape

Use this as pseudocode in any language:

```python
class QueryHydrator:
    async def hydrate(self, query) -> query: ...

class Source:
    async def source(self, query) -> list[Candidate]: ...

class Hydrator:
    async def hydrate(self, query, candidates) -> list[Result[Candidate]]: ...
    def update(self, candidate, hydrated): ...

class Filter:
    def filter(self, query, candidates) -> FilterResult:  # kept, removed
        ...

class Scorer:
    async def score(self, query, candidates) -> list[Result[Candidate]]: ...
    def update(self, candidate, scored): ...

class Selector:
    def select(self, query, candidates) -> SelectResult:  # selected, non_selected
        ...

class SideEffect:
    async def run(self, query, selected, non_selected): ...
```

## Observability Checklist

For each stage/component, log:

- enabled/disabled
- input count and output count
- kept/removed count and filter rate
- selected/non-selected count
- latency buckets
- cache hits/misses for cached hydrators
- source errors and partial failures
- final result size and empty-result rate

## Common Pitfalls

- Letting hydrators drop candidates because external data is missing. Use a filter after hydration instead.
- Mixing policy gates into ranking scores. Must-not-show content should not survive just because it has a high score.
- Not logging non-selected candidates. You need them for model training, calibration, and debugging.
- Treating side effects as required response work. Make them async and retryable unless correctness depends on them.
- Building one giant feed function. Small components make experiments and targeted rollbacks much easier.

## Source

Based on xAI's open-source `xai-org/x-algorithm` repository, especially the May 15 2026 For You feed release. Treat these as transferable system-design patterns, not a claim that your product should copy X exactly.
