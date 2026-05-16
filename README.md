# X Algorithm Growth Skills

<p align="center">
  <a href="https://hermes-agent.nousresearch.com"><img src="https://raw.githubusercontent.com/NousResearch/hermes-agent/main/website/static/img/logo.png" alt="Hermes Agent" height="56"></a>
  &nbsp;&nbsp;&nbsp;&nbsp;
  <a href="https://github.com/openclaw/openclaw"><img src="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-logo-text.svg" alt="OpenClaw" height="56"></a>
</p>

Agent skills for growing an X account using lessons from xAI's public [X For You Feed Algorithm](https://github.com/xai-org/x-algorithm).

This repo is now focused on **creator growth**, not backend recommendation-system implementation. The skills translate public algorithm concepts into practical actions: stronger posts, better replies, profile conversion, content calendars, and analytics loops.

Primary targets: **Hermes Agent** and **OpenClaw**. The skills use standard `SKILL.md` folders, so they are also compatible with other AgentSkills-style tools.

## What These Skills Optimize For

The public X algorithm code shows ranking signals around positive and negative user actions. For account growth, the practical translation is:

- Earn **dwell** with posts people stop to read.
- Earn **replies** with specific opinions, tradeoffs, and questions.
- Earn **reposts/quotes/shares** with useful frameworks, templates, and status-signaling insights.
- Earn **profile clicks and follows** through clear expertise and consistent positioning.
- Avoid negative feedback: **not interested**, low dwell, mutes, blocks, reports, misleading hooks, and repetitive slop.

## Install for Hermes Agent

### Global install

```bash
git clone https://github.com/mikaelaldy/x-algorithm-skills.git /tmp/x-algorithm-skills
mkdir -p ~/.hermes/skills
cp -R /tmp/x-algorithm-skills/skills/* ~/.hermes/skills/
```

Then restart Hermes or start a new session. You can ask Hermes to use a skill by name, for example:

```text
Use /x-growth-strategy to create a 7-day plan for my X account.
```

### Project-local install

From a project/workspace directory:

```bash
git clone https://github.com/mikaelaldy/x-algorithm-skills.git /tmp/x-algorithm-skills
mkdir -p skills
cp -R /tmp/x-algorithm-skills/skills/* skills/
```

## Install for OpenClaw

### Global install

```bash
git clone https://github.com/mikaelaldy/x-algorithm-skills.git /tmp/x-algorithm-skills
mkdir -p ~/.openclaw/skills
cp -R /tmp/x-algorithm-skills/skills/* ~/.openclaw/skills/
```

Restart OpenClaw or start a new session, then use the skills by name.

### Workspace install

From an OpenClaw workspace:

```bash
git clone https://github.com/mikaelaldy/x-algorithm-skills.git /tmp/x-algorithm-skills
mkdir -p skills
cp -R /tmp/x-algorithm-skills/skills/* skills/
```

## Skills

- `/x-growth-strategy` — create a full X growth strategy from positioning to weekly experiments.
- `/x-content-signals` — rewrite posts for dwell, replies, reposts, profile clicks, follows, and low negative feedback.
- `/x-reply-growth` — grow through strategic replies under the right accounts.
- `/x-profile-conversion` — improve bio, pinned post, header, and profile promise so profile clicks become follows.
- `/x-analytics-loop` — review weekly metrics and decide what to repeat, stop, or test.
- `/x-content-calendar` — create 7-day or 30-day content calendars using algorithm-signal content pillars.
- `/x-post-audit` — audit and improve a draft before publishing.
- `/x-growth-review` — audit a full account growth system.

## Suggested Workflow

1. Start with `/x-growth-strategy` to define audience, positioning, and pillars.
2. Use `/x-content-calendar` to plan the week.
3. Use `/x-content-signals` or `/x-post-audit` before publishing.
4. Use `/x-reply-growth` daily to enter the right audience graph.
5. Use `/x-analytics-loop` weekly to double down on winners.
6. Use `/x-profile-conversion` whenever profile clicks do not become follows.

## Important Caveat

These skills are based on public code and docs, then translated into creator strategy. They are not insider X growth guarantees. Treat every recommendation as a hypothesis to test with your own analytics.

## Attribution

Derived from public concepts and code structure in [`xai-org/x-algorithm`](https://github.com/xai-org/x-algorithm), licensed under Apache-2.0. This repo contains agent instructions and growth playbooks, not original model artifacts.

## License

Apache-2.0, to stay compatible with the upstream source material.
