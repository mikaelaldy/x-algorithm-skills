# X Algorithm Skills

Claude Code / AI-agent skills distilled from xAI's open-source [X For You Feed Algorithm](https://github.com/xai-org/x-algorithm).

These skills help agents design, review, and implement recommendation systems inspired by the X feed architecture: retrieval, ranking, filtering, home-mixer orchestration, ads blending, and content-understanding pipelines.

## Installation

In Claude Code:

```text
/plugin marketplace add mikaelaldy/x-algorithm-skills
/plugin install x-algorithm-skills
```

Alternative local install:

```bash
git clone https://github.com/mikaelaldy/x-algorithm-skills.git ~/.claude/plugins/x-algorithm-skills
```

Then in Claude Code:

```text
/plugin marketplace add ~/.claude/plugins/x-algorithm-skills
/plugin install x-algorithm-skills
```

## Skills

- `/x-feed-architecture` — design an X-style For You recommendation architecture.
- `/x-candidate-pipeline` — implement composable query/source/hydrator/filter/scorer/selector/side-effect stages.
- `/x-phoenix-retrieval` — design two-tower retrieval for narrowing huge corpora to top-K.
- `/x-phoenix-ranking` — design transformer ranking with multi-action scoring and candidate isolation.
- `/x-home-mixer` — build the online orchestration layer that creates a feed response.
- `/x-feed-filtering` — define duplicate, safety, muted/blocked, served-history, and freshness gates.
- `/x-ads-blending` — insert ads and modules with spacing and brand-safety adjacency rules.
- `/x-grox-content-understanding` — design async classifiers, embedders, summaries, ASR/media tasks, and safety labels.
- `/x-algorithm-review` — audit a recommendation system against X-algorithm lessons.

## Attribution

Derived from public concepts and code structure in [`xai-org/x-algorithm`](https://github.com/xai-org/x-algorithm), which is licensed under Apache-2.0. This repo contains agent instructions and summaries, not the original model artifacts.

## License

Apache-2.0, to stay compatible with the upstream source material.
