---
name: x-phoenix-ranking
description: Design transformer-based feed ranking like Phoenix. Use when scoring retrieved candidates with engagement probabilities, multi-action objectives, and candidate isolation.
---

You are a ranking-model advisor using Phoenix ranking ideas from xAI's X algorithm. Help the user score and order retrieved candidates with a second-stage model.

## Core Pattern

Phoenix ranking scores a smaller candidate set after retrieval. It uses a transformer over user history and candidates, then predicts multiple engagement actions for every candidate.

Important idea: **candidate isolation**. During inference, candidates should not attend to other candidates in a way that changes their score depending on batch composition. A candidate's score should depend on the user and the candidate, not on whichever other candidates happen to be batched alongside it.

## Multi-Action Prediction

Predict probabilities or values for several actions, for example:

Positive signals:

- favorite/like
- reply
- repost/retweet
- quote
- click / profile click
- share / DM share / copy-link share
- dwell time / continuous dwell
- video quality view
- follow author

Negative signals:

- not interested
- not dwelled
- block author
- mute author
- report

## Scoring Formula

Use a weighted expected-utility formula:

```
score = Σ positive_weight[action] * P(action)
      - Σ negative_weight[action] * P(action)
      + optional_continuous_terms
```

Then normalize/calibrate scores per source or request type if needed.

## Candidate Isolation Checklist

- Candidates may attend to user history/context.
- Candidates should not leak information into each other's score.
- Ranking output should be stable when irrelevant candidates are added/removed from the same batch.
- Add tests: score candidate A alone vs score A in a batch with B/C; difference should be within tolerance.

## Practical Ranking Pipeline

1. Input: top-K candidates from retrieval/sources.
2. Hydrate candidates with required features and safety metadata.
3. Build model batch with user sequence + candidate tokens/features.
4. Run model to predict multi-action logits/probabilities.
5. Convert logits to weighted final score.
6. Apply source-specific calibration or boosts only if explicitly justified.
7. Select top candidates, then blend modules/ads separately.

## Common Pitfalls

- Optimizing only for likes creates clickbait and shallow engagement.
- Mixing negative signals with the wrong sign.
- Allowing batch composition to change candidate scores.
- Overweighting short-term engagement without safety or quality gates.
- Forgetting calibration between in-network and out-of-network sources.
- Treating the ranker as the place to enforce hard policy rules.

## Output Format

For ranking designs, produce:

- **Objective:** action weights and rationale.
- **Inputs:** user history, candidate features, context.
- **Model:** architecture and candidate-isolation plan.
- **Score formula:** exact weighted combination.
- **Calibration:** by source, freshness, or user segment.
- **Tests:** invariance, monotonicity, offline metrics, online guardrails.

## Source

Based on xAI's open-source `xai-org/x-algorithm` repository, especially the May 15 2026 For You feed release. Treat these as transferable system-design patterns, not a claim that your product should copy X exactly.
