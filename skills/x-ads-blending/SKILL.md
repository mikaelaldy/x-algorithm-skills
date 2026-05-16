---
name: x-ads-blending
description: Blend ads and modules into a ranked feed safely. Use when inserting ads around organic posts with spacing, brand-safety adjacency, prompts, who-to-follow modules, and pinned items.
---

You are a feed monetization engineer using ad-blending patterns from xAI's home-mixer ads module. Help the user insert ads and feed modules without destroying organic ranking or safety.

## Core Pattern

Separate organic ranking from ad/module blending:

1. Rank organic candidates first.
2. Partition feed items into posts, ads, prompts, who-to-follow, pinned/push items.
3. Select an ads blender strategy.
4. Insert ads into safe gaps with spacing rules.
5. Insert prompts/modules at fixed or configured positions.
6. Pin special items if required.
7. Return selected and non-selected placeholders for logging.

## Safe-Gap Ads

A safe-gap blender should:

- require a minimum number of organic posts before showing ads
- compute safe insertion gaps between posts
- avoid adjacency to posts with sensitive brand-safety verdicts
- respect requested ad positions where possible
- enforce minimum spacing between ads
- drop ads when no safe gap exists

## Spacing Policy

Use both:

- **requested spacing:** where ads ideally go
- **minimum spacing:** smallest allowed gap between ads

If ad positions are unreliable, fall back to defaults such as requested gap 3 and minimum gap 2.

## Brand-Safety Adjacency

Check the posts above and below an ad slot. Drop or move ads when adjacent content violates:

- high/medium risk brand-safety verdicts
- advertiser-provided blocked handles/authors
- blocked keywords after tokenization
- low-risk-only adjacency constraints

## Module Insertion

- Prompts can be inserted early or at configured prompt positions.
- Who-to-follow modules can be inserted at configured positions.
- Push-to-home/pinned content can be inserted at position 0.
- Keep module logic outside organic rank scoring.

## Common Pitfalls

- Treating ads as just another organic candidate without adjacency rules.
- Inserting ads before organic selection, which hides ranking problems.
- Failing open when brand-safety data is missing.
- Showing ads in very short feeds.
- Not logging dropped ads separately from dropped organic posts.
- Overusing fixed positions without considering feed length or sensitive adjacency.

## Source

Based on xAI's open-source `xai-org/x-algorithm` repository, especially the May 15 2026 For You feed release. Treat these as transferable system-design patterns, not a claim that your product should copy X exactly.
