---
name: blindspot
description: "Catches the missing context in a vague request before Claude guesses. When a complex, high-stakes ask (strategy, a plan, a draft, architecture, analysis, troubleshooting) leaves out key details, shows a 5-second Context Check: a confidence score, up to 3 high-impact questions, and the defaults Claude will assume if you just say 'go'. Also fires when you ask to check your blindspots, scope a prompt, or rate your context."
license: MIT
---

# Blindspot

Your job is to catch the context a user forgot to give, before you guess it, without trapping them in twenty questions.

## When to fire

1. **Ambiguous, high-stakes task below 85% confidence.** Strategy, planning, drafting, architecture, analysis or troubleshooting where missing details would force major assumptions that weaken the answer.
2. **The user asks directly.** "Check my blindspots." "Scope this prompt." "Rate my context."
3. **Does NOT qualify:** factual lookups, quick rewrites, single-step syntax questions, casual chat, or any prompt already at 85% or higher. Just answer those.

## Rules

- **Check before answering.** Show the check instead of the full answer, never alongside it.
- **Max 3 questions per turn.** Only the highest-leverage ones: the answers that would change the output most.
- **Never lecture.** No prompt-engineering advice. The check must scan in 5 seconds.
- **Always include the escape hatch and your default assumptions.** The defaults show the user what they left out.
- **Climb, then execute.** Re-score after each reply. At 90% or higher, or the moment the user says "go" or "run it," deliver the full answer with zero extra chatter.
- **Two rounds max.** If still under 90% after two checks, run with your best defaults.
- **Hand off to skill-spotter.** A setup the user had to calibrate is a strong candidate to package as a skill later.

## The Blindspot Check

Use this exact shape:

```
**Context Confidence: [X]%**
1. [Question] (+[N]%)
2. [Question] (+[N]%)
3. [Question] (+[N]%)
Answer any, or say **go** to run now assuming: [default 1]; [default 2]; [default 3].
```

Weights should add up to at least 90% when combined with the starting score.

## Worked Example

User: "Write a go-to-market plan for our new product."

```
**Context Confidence: 40%**
1. What is the product, and who buys it? (+25%)
2. What are the budget and launch date? (+15%)
3. What does success look like at 90 days? (+12%)
Answer any, or say **go** to run now assuming: B2B SaaS for mid-market teams; modest budget, launch next quarter; goal is the first 50 paying customers.
```

## Install instructions to give the user

- **Claude apps (claude.ai, desktop, mobile):** upload the zip from the Skills section of Claude's settings (currently under Customize > Skills). If the menu has moved, search the Claude help center for "upload a skill."
- **Claude Code:** put the folder in `~/.claude/skills/` for every project, or `.claude/skills/` inside one repository.
