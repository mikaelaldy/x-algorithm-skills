<p align="center">
  <strong>Works with</strong><br>
  <a href="https://hermes-agent.nousresearch.com">
    <img alt="Hermes Agent" src="https://raw.githubusercontent.com/NousResearch/hermes-agent/main/website/static/img/hermes-agent-banner.png" height="40">
  </a>
  &nbsp;&nbsp;&nbsp;
  <a href="https://github.com/openclaw/openclaw">
    <img alt="OpenClaw" src="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-logo-text.svg" height="36">
  </a>
</p>

# X Algorithm Growth Skills

Agent skills for growing an X account using lessons from xAI's public [X For You Feed Algorithm](https://github.com/xai-org/x-algorithm).

These are small, adaptable, composable skills for Hermes Agent, OpenClaw, and any AgentSkills-compatible tool. They are not magic growth hacks. They translate public ranking signals into repeatable creator workflows: better posts, better replies, better profiles, and better weekly experiments.

## Quickstart

### Hermes Agent

Install globally:

```bash
git clone https://github.com/mikaelaldy/x-algorithm-skills.git /tmp/x-algorithm-skills
mkdir -p ~/.hermes/skills/growth
cp -R /tmp/x-algorithm-skills/skills/growth/* ~/.hermes/skills/growth/
```

Start a new Hermes session, then run:

```text
/setup-x-growth-skills
```

### OpenClaw

Install globally:

```bash
git clone https://github.com/mikaelaldy/x-algorithm-skills.git /tmp/x-algorithm-skills
mkdir -p ~/.openclaw/skills/growth
cp -R /tmp/x-algorithm-skills/skills/growth/* ~/.openclaw/skills/growth/
```

Start a new OpenClaw session, then run:

```text
/setup-x-growth-skills
```

### Workspace install

For either Hermes or OpenClaw, you can install into the current workspace instead:

```bash
git clone https://github.com/mikaelaldy/x-algorithm-skills.git /tmp/x-algorithm-skills
mkdir -p skills/growth
cp -R /tmp/x-algorithm-skills/skills/growth/* skills/growth/
```

## Why These Skills Exist

I built these skills to fix common failure modes when using agents to grow on X.

### #1: The Agent Gives Generic Twitter Advice

**The Problem**: Most advice sounds like "post consistently" or "engage with your audience." True, but useless.

**The Fix**: Use the public X algorithm as a signal map. The skills focus on concrete actions that map to measurable signals: dwell, replies, reposts, shares, profile clicks, follows, and negative feedback avoidance.

Use:

- **[/x-growth-strategy](./skills/growth/x-growth-strategy/SKILL.md)** — decide the account promise, audience, retrieval neighborhood, and weekly experiments.
- **[/setup-x-growth-skills](./skills/growth/setup-x-growth-skills/SKILL.md)** — create the account brief the other skills can use.

### #2: Posts Get Likes But No Followers

**The Problem**: Likes are not the same as growth. A post can be agreeable but fail to create profile clicks, follows, shares, or a stronger audience graph.

**The Fix**: Design posts around the action you want.

Use:

- **[/x-content-signals](./skills/growth/x-content-signals/SKILL.md)** — rewrite posts for a primary signal.
- **[/x-post-audit](./skills/growth/x-post-audit/SKILL.md)** — score a draft before publishing.
- **[/x-profile-conversion](./skills/growth/x-profile-conversion/SKILL.md)** — fix the profile when clicks do not become follows.

### #3: Replies Waste Time

**The Problem**: Random replies feel productive but do not teach the algorithm who should see you.

**The Fix**: Reply inside the right audience graph. Add evidence, frameworks, counterexamples, or sharp questions under accounts whose audience should overlap with yours.

Use:

- **[/x-reply-growth](./skills/growth/x-reply-growth/SKILL.md)** — plan daily strategic replies and draft high-signal replies.

### #4: The User Never Learns What Works

**The Problem**: Without a weekly review, the user keeps posting from vibes.

**The Fix**: Track topics, hooks, formats, and outcomes. Repeat winners. Turn good replies into posts. Kill weak formats.

Use:

- **[/x-analytics-loop](./skills/growth/x-analytics-loop/SKILL.md)** — diagnose winners and losers.
- **[/x-content-calendar](./skills/growth/x-content-calendar/SKILL.md)** — turn the diagnosis into a plan.
- **[/x-growth-review](./skills/growth/x-growth-review/SKILL.md)** — audit the whole system.

## Reference

### Growth

Skills for X account growth.

- **[setup-x-growth-skills](./skills/growth/setup-x-growth-skills/SKILL.md)** — Configure the account brief: audience, pillars, cadence, metrics, and voice rules.
- **[x-growth-strategy](./skills/growth/x-growth-strategy/SKILL.md)** — Create a full X growth strategy from positioning to weekly experiments.
- **[x-content-signals](./skills/growth/x-content-signals/SKILL.md)** — Rewrite posts for dwell, replies, reposts, profile clicks, follows, and low negative feedback.
- **[x-reply-growth](./skills/growth/x-reply-growth/SKILL.md)** — Grow through strategic replies under the right accounts.
- **[x-profile-conversion](./skills/growth/x-profile-conversion/SKILL.md)** — Improve bio, pinned post, header, and profile promise so profile clicks become follows.
- **[x-analytics-loop](./skills/growth/x-analytics-loop/SKILL.md)** — Review weekly metrics and decide what to repeat, stop, or test.
- **[x-content-calendar](./skills/growth/x-content-calendar/SKILL.md)** — Create 7-day or 30-day content calendars using algorithm-signal content pillars.
- **[x-post-audit](./skills/growth/x-post-audit/SKILL.md)** — Audit and improve a draft before publishing.
- **[x-growth-review](./skills/growth/x-growth-review/SKILL.md)** — Audit a full account growth system.

## How These Skills Are Written

Before rewriting this repo, I checked current guidance for Hermes, OpenClaw, AgentSkills, and Claude-style skills. The useful rules are:

- Keep each skill focused on one repeatable workflow.
- Put the trigger in the `description`; agents see that before they load the body.
- Use imperative steps, not essays.
- Keep `SKILL.md` lean; move bulky detail into reference files when needed.
- Use concrete examples and output formats.
- Make directory names match `name:`.
- Use standard `SKILL.md` folders so Hermes and OpenClaw can both load them.

## Caveat

These skills are based on public code and docs, then translated into creator strategy. They are not insider X growth guarantees. Treat every recommendation as a hypothesis to test with your own analytics.

## Attribution

Derived from public concepts and code structure in [`xai-org/x-algorithm`](https://github.com/xai-org/x-algorithm), licensed under Apache-2.0. This repo contains agent instructions and growth playbooks, not original model artifacts.

## License

Apache-2.0, to stay compatible with the upstream source material.
