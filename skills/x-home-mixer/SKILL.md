---
name: x-home-mixer
description: Implement a home-mixer orchestration layer for feeds. Use when combining organic posts, out-of-network retrieval, modules, ads, hydration, ranking, and response side effects.
---

You are designing a Home Mixer layer inspired by xAI's `home-mixer`. Home Mixer is the online orchestration service that turns a feed request into a final feed response.

## Responsibility Boundary

Home Mixer should orchestrate, not own everything:

- Call source systems for candidates.
- Call user/context services for query hydration.
- Call post/entity/safety/engagement services for candidate hydration.
- Call ranking/retrieval clients where needed.
- Blend feed item types into final response.
- Emit side effects for analytics, history, and training data.

It should not become a monolithic model, a data warehouse, or an unbounded business-rule dumping ground.

## Main Feed Item Types

Plan for typed feed items:

- ranked organic post
- in-network post
- out-of-network post
- ad
- prompt/module
- who-to-follow module
- push-to-home/pinned item

## Query Hydration Examples

Hydrate request context with:

- served history and past request timestamps
- user action sequence for retrieval and scoring
- followed users and followed topics
- inferred interests/topics
- blocked and muted users/keywords
- impressions and bloom filters
- subscriptions
- demographics/inferred gender if product-appropriate
- IP/region/language

## Candidate Hydration Examples

Hydrate candidates with:

- core post data
- author/user metadata
- engagement counts
- language code
- media/video duration
- quote expansion
- mutual follow score
- brand safety and visibility-filtering labels
- subscription eligibility
- filtered topics

## Side Effects

Emit asynchronously:

- served candidates log
- selected and non-selected candidates
- client events
- seen IDs
- served history update/truncation
- request cache info
- ranking/scoring stats
- experiment stats

## Design Pattern

```
HomeMixer.handle(request):
  query = hydrate_query(request)
  candidates = run_candidate_pipeline(query)
  feed_items = blend_modules_and_ads(query, candidates)
  response = truncate_and_format(feed_items)
  fire_side_effects(query, selected, non_selected)
  return response
```

## Common Pitfalls

- Making Home Mixer own business logic that belongs in separate filters/scorers/selectors.
- Failing closed on a noncritical source. For feeds, partial results are often better than empty results.
- Not distinguishing request types: first page, bottom pagination, foreground truncation, cached retry.
- Not storing served history, causing repetitive feeds.
- Adding modules/ads before ranking organic candidates, making debugging harder.

## Source

Based on xAI's open-source `xai-org/x-algorithm` repository, especially the May 15 2026 For You feed release. Treat these as transferable system-design patterns, not a claim that your product should copy X exactly.
