---
title: "Claude Code Insights: The Mirror I Didn't Know I Needed"
date: "2026-04-23T10:00:00-07:00"
lastmod: "2026-04-23"
draft: false
author: "Travis Nesbit"
description: "Why the /insights command in Claude Code quietly became my favorite feature this week — a usage dashboard that actually tells you something useful about how you work."
summary: "I spent an afternoon poking at Claude Code's insights feature and came away a little smug about it. Here's why this thing is more than a usage readout — it's feedback on how you actually work."
tags: ["claude", "claude-code", "ai", "tools", "workflow"]
categories: ["Tools"]
---

I was rooting around in Claude Code the other day — part curiosity, part procrastination — and stumbled onto `insights`. I expected a usage meter. What I got was something closer to a mirror. I've been bragging about it to anyone who will listen, so I figured I'd write it down.

## What it actually shows

The short version: insights is a running readout of how you're using Claude. Which models you're reaching for, which tools get hammered, how your sessions are shaped, where your time is going. The less-short version is that it's the first dashboard I've ever looked at and thought, *oh — that's me.*

It's one thing to *feel* like you've been leaning hard on Sonnet this week. It's another to see the ratio next to your Opus calls and realize you've been reflexively picking the fast model even when the task probably wanted the smart one. Or the other way around: realizing you've been paying the Opus premium for tasks that Haiku would have eaten without blinking.

## Why it's quietly great

Most "usage stats" in dev tools are billing dashboards dressed up in nicer fonts. This isn't that. A few things make it land:

- **It's behavioral, not just financial.** It tells you *what you did*, not just *what it cost*. There's a difference between "you spent $X this week" and "you started 40 sessions and 12 of them were under two turns."
- **It surfaces patterns you don't notice in the moment.** The one-turn sessions were the tell for me. I was using Claude like a search engine half the time — which is fine, but it made me think about whether I was framing those questions in a way that could actually pay off.
- **It closes a feedback loop that's usually invisible.** You write code with an AI all day, you ship things, life moves on. Insights is the first tool that let me look back at a week of work and ask, *was any of that shaped the way I thought it was?*

## What I changed because of it

Two things, immediately:

1. **I stopped defaulting to the biggest model.** Seeing my tool-use patterns made it obvious that a lot of my sessions are grep, read, edit, done. That doesn't need a frontier model; it needs a fast one with decent judgment. I've been explicitly reaching for Haiku more, and honestly — no regrets.
2. **I started being more deliberate about session boundaries.** My shortest sessions were noisy — half-formed questions, context I didn't set up, me bailing when the first response wasn't quite right. Now I either commit to the session or I don't start it. Fewer, better turns.

Neither of those is a revelation on its own. The point is I wouldn't have made either change without the data in front of me.

## Who should care

If you use Claude Code occasionally, insights is a curiosity. If you use it every day — the way I do, the way it's woven into my editor and my shell and my brain at this point — it's a genuinely useful feedback loop. The kind of thing you glance at on a Friday, notice something, and work a little smarter the following week.

It's not the flashiest feature Anthropic shipped this cycle. It might be my favorite, though. Go poke at it.
