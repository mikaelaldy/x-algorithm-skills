<p align="center">
  <strong>Works with</strong><br>
  <a href="https://hermes-agent.nousresearch.com">
    <img alt="Hermes Agent" src="https://raw.githubusercontent.com/NousResearch/hermes-agent/main/website/static/img/hermes-agent-banner.png" height="40">
  </a>
  &nbsp;&nbsp;&nbsp;
  <a href="https://github.com/openclaw/openclaw">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-logo-text.png">
      <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-logo-text-dark.png">
      <img alt="OpenClaw" src="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-logo-text-dark.png" height="36">
    </picture>
  </a>
</p>

# X Algorithm Growth Skills

Agent skills for growing an X account using lessons from xAI's public [X For You Feed Algorithm](https://github.com/xai-org/x-algorithm).

Use these when your agent gives vague Twitter advice, writes posts that get likes but no followers, or cannot turn analytics into a weekly plan. The skills translate public ranking signals into practical workflows: stronger hooks, better replies, profile conversion, content calendars, and weekly experiments.

No "growth hack" promises. Every recommendation is a hypothesis you test against your own account.

## Install

Pick the method that matches your agent and OS.

### Hermes Agent — install one skill from GitHub

Good when you only need one workflow.

```bash
hermes skills install https://raw.githubusercontent.com/mikaelaldy/x-algorithm-skills/main/skills/growth/x-growth-strategy/SKILL.md --name x-growth-strategy --category growth
```

Then start Hermes and ask:

```text
Use x-growth-strategy to plan my X account growth.
```

### Hermes Agent — install the full pack

**Linux/macOS:**

```bash
git clone https://github.com/mikaelaldy/x-algorithm-skills.git /tmp/x-algorithm-skills
mkdir -p ~/.hermes/skills/growth
cp -R /tmp/x-algorithm-skills/skills/growth/* ~/.hermes/skills/growth/
```

**Windows PowerShell:**

```powershell
git clone https://github.com/mikaelaldy/x-algorithm-skills.git $env:TEMP\x-algorithm-skills
New-Item -ItemType Directory -Force "$HOME\.hermes\skills\growth" | Out-Null
Copy-Item "$env:TEMP\x-algorithm-skills\skills\growth\*" "$HOME\.hermes\skills\growth" -Recurse -Force
```

Restart Hermes, then run:

```text
/setup-x-growth-skills
```

### OpenClaw — install the full pack from GitHub

Use this when you want all 9 skills now.

**Linux/macOS:**

```bash
git clone https://github.com/mikaelaldy/x-algorithm-skills.git /tmp/x-algorithm-skills
mkdir -p ~/.openclaw/skills/growth
cp -R /tmp/x-algorithm-skills/skills/growth/* ~/.openclaw/skills/growth/
```

**Windows PowerShell:**

```powershell
git clone https://github.com/mikaelaldy/x-algorithm-skills.git $env:TEMP\x-algorithm-skills
New-Item -ItemType Directory -Force "$HOME\.openclaw\skills\growth" | Out-Null
Copy-Item "$env:TEMP\x-algorithm-skills\skills\growth\*" "$HOME\.openclaw\skills\growth" -Recurse -Force
```

### Workspace install — any AgentSkills-compatible agent

Use this when you want the skills only inside one project.

**Linux/macOS:**

```bash
git clone https://github.com/mikaelaldy/x-algorithm-skills.git /tmp/x-algorithm-skills
mkdir -p skills/growth
cp -R /tmp/x-algorithm-skills/skills/growth/* skills/growth/
```

**Windows PowerShell:**

```powershell
git clone https://github.com/mikaelaldy/x-algorithm-skills.git $env:TEMP\x-algorithm-skills
New-Item -ItemType Directory -Force "skills\growth" | Out-Null
Copy-Item "$env:TEMP\x-algorithm-skills\skills\growth\*" "skills\growth" -Recurse -Force
```

## Start Here

Run the setup skill first. It creates the account brief the other skills use.

```text
/setup-x-growth-skills
```

Give it:

- your handle or niche
- target audience
- what you sell or want to be known for
- current follower count
- posting cadence
- examples of posts that worked or failed

After that, call the specific skill for the problem in front of you.

## Skills by Problem

### "I don't know what my account should be about"

Use **[x-growth-strategy](./skills/growth/x-growth-strategy/SKILL.md)**.

It helps you define:

- account promise
- audience graph
- content pillars
- reply targets
- weekly experiments

Prompt:

```text
Use x-growth-strategy. My account is about <topic>. Build a 30-day growth strategy.
```

### "My posts get likes but no followers"

Use **[x-profile-conversion](./skills/growth/x-profile-conversion/SKILL.md)** and **[x-content-signals](./skills/growth/x-content-signals/SKILL.md)**.

They help you fix the gap between attention and conversion:

- clearer bio
- stronger pinned post
- posts that create profile clicks and follows
- fewer empty engagement posts

Prompt:

```text
Use x-profile-conversion. Rewrite my bio, pinned post idea, and profile promise for this audience: <audience>.
```

### "My draft sounds fine, but I don't know if it will work"

Use **[x-post-audit](./skills/growth/x-post-audit/SKILL.md)**.

It checks the draft before you publish:

- hook clarity
- dwell potential
- reply potential
- repost/share reason
- negative-feedback risk

Prompt:

```text
Use x-post-audit on this draft: <paste draft>.
```

### "I need better posts, not generic content ideas"

Use **[x-content-signals](./skills/growth/x-content-signals/SKILL.md)**.

It rewrites for a chosen signal:

- dwell: make people read longer
- replies: invite useful disagreement or examples
- reposts: make the post worth sharing
- profile clicks: make readers want context
- follows: make the account promise obvious

Prompt:

```text
Use x-content-signals. Rewrite this post for profile clicks and follows: <draft>.
```

### "I reply a lot but it doesn't grow the account"

Use **[x-reply-growth](./skills/growth/x-reply-growth/SKILL.md)**.

It turns replies into targeted distribution:

- choose accounts with overlapping audiences
- avoid random engagement
- write replies that add evidence, frameworks, or counterexamples
- turn good replies into posts

Prompt:

```text
Use x-reply-growth. Give me 10 strategic replies for accounts in <niche>.
```

### "I don't know what to post this week"

Use **[x-content-calendar](./skills/growth/x-content-calendar/SKILL.md)**.

It creates a calendar from your account strategy:

- daily post themes
- primary signal per post
- reply blocks
- experiments to run

Prompt:

```text
Use x-content-calendar. Make a 7-day calendar for <audience> with one post per day.
```

### "I keep posting from vibes"

Use **[x-analytics-loop](./skills/growth/x-analytics-loop/SKILL.md)**.

It turns analytics into decisions:

- repeat winners
- stop weak formats
- identify topics with profile-click or follow potential
- choose next week's experiments

Prompt:

```text
Use x-analytics-loop. Here are my last 20 posts and metrics: <paste metrics>.
```

### "I want a full account audit"

Use **[x-growth-review](./skills/growth/x-growth-review/SKILL.md)**.

It reviews the whole system:

- positioning
- profile
- content mix
- replies
- analytics loop
- next actions

Prompt:

```text
Use x-growth-review. Audit my X account from these screenshots/metrics: <paste data>.
```

## Reference

- **[setup-x-growth-skills](./skills/growth/setup-x-growth-skills/SKILL.md)** — Configure the account brief: audience, pillars, cadence, metrics, and voice rules.
- **[x-growth-strategy](./skills/growth/x-growth-strategy/SKILL.md)** — Create a full X growth strategy from positioning to weekly experiments.
- **[x-content-signals](./skills/growth/x-content-signals/SKILL.md)** — Rewrite posts for dwell, replies, reposts, profile clicks, follows, and low negative feedback.
- **[x-reply-growth](./skills/growth/x-reply-growth/SKILL.md)** — Grow through strategic replies under the right accounts.
- **[x-profile-conversion](./skills/growth/x-profile-conversion/SKILL.md)** — Improve bio, pinned post, header, and profile promise so profile clicks become follows.
- **[x-analytics-loop](./skills/growth/x-analytics-loop/SKILL.md)** — Review weekly metrics and decide what to repeat, stop, or test.
- **[x-content-calendar](./skills/growth/x-content-calendar/SKILL.md)** — Create 7-day or 30-day content calendars using algorithm-signal content pillars.
- **[x-post-audit](./skills/growth/x-post-audit/SKILL.md)** — Audit and improve a draft before publishing.
- **[x-growth-review](./skills/growth/x-growth-review/SKILL.md)** — Audit a full account growth system.

## Notes

These skills are based on public code and docs, then translated into creator workflows. They are not insider X ranking guarantees.

## Attribution

Derived from public concepts and code structure in [`xai-org/x-algorithm`](https://github.com/xai-org/x-algorithm), licensed under Apache-2.0. This repo contains agent instructions and growth playbooks, not original model artifacts.

## License

Apache-2.0, to stay compatible with the upstream source material.
