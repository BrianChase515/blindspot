# Blindspot

**Catch what you forgot to tell Claude, before it guesses.**

Blindspot is a Claude skill for vague requests on tasks that matter. Instead of guessing the missing context and handing you something generic, Claude pauses for a 5-second Context Check: how confident it is, the 1 to 3 questions that would help most, and exactly what it will assume if you just say "go."

## The problem

Ask for "a go-to-market plan" or "a fix for our flaky deploys" with no context, and an AI fills the gaps with safe, average guesses. The answer looks complete and is quietly generic. Most people never see which assumptions were made.

## What it looks like

> **Context Confidence: 40%**
> 1. What is the product, and who buys it? (+25%)
> 2. What are the budget and launch date? (+15%)
> 3. What does success look like at 90 days? (+12%)
>
> Answer any, or say **go** to run now assuming: B2B SaaS for mid-market teams; modest budget, launch next quarter; goal is the first 50 paying customers.

The default assumptions are the point. Seeing them is usually the moment you realize what you left out.

## Designed not to be annoying

- Fires only on complex, high-stakes asks that are missing real context.
- Never fires on quick questions, rewrites, syntax help, casual chat, or prompts that are already clear.
- At most 3 questions at a time, and at most two rounds.
- Say "go" anytime and you get the answer immediately.
- No lectures about prompting.

You can also call it yourself: "check my blindspots," "scope this prompt," or "rate my context."

## Works with Skill Spotter

Once Blindspot helps you dial in a task, [Skill Spotter](https://github.com/BrianChase515/skill-spotter) can package that setup as a reusable skill, so you never have to answer the same questions again.

## Install

**Claude apps (claude.ai, desktop, mobile)**
1. Download [`blindspot.zip`](https://github.com/BrianChase515/blindspot/raw/main/blindspot.zip).
2. In Claude, open Customize > Skills and upload the zip.

**Claude Code**
```
/plugin marketplace add BrianChase515/blindspot
/plugin install blindspot@blindspot
```
Or copy `skills/blindspot/` into `~/.claude/skills/`.

**Other agents that read SKILL.md** (for example GitHub Copilot): copy `skills/blindspot/` into your agent's skills folder, such as `.github/skills/` or `~/.copilot/skills/`.

## Feedback

Open an issue with a prompt where it fired when it shouldn't have, or stayed quiet when it should have spoken up.

## Author

Built by [Brian Chase](https://github.com/BrianChase515). MIT licensed.
