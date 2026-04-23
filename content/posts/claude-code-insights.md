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

The real value wasn't the stats — it was the suggestions. Based on what insights saw me doing, Claude pointed me at a handful of skills and hooks that slot directly into my workflow. Not generic "here are some features you haven't tried" filler; actual recommendations that matched the patterns I was already running. I'm adopting those.

The follow-on change is on my end: I'm going back through the repositories I work in and adjusting their structure to accommodate those skills and hooks properly. If a skill expects certain files in certain places, or a hook wants something to grep against, then the repo should meet it halfway. It's a small tax up front for a setup that pays me back every session.

That's the part that surprised me. I went in expecting a dashboard and walked out with a small list of concrete, actionable changes — both to how I use Claude and to how my projects are laid out.

## Who should care

If you use Claude Code occasionally, insights is a curiosity. If you use it every day — the way I do, the way it's woven into my editor and my shell and my brain at this point — it's a genuinely useful feedback loop. The kind of thing you glance at on a Friday, notice something, and work a little smarter the following week.

It's not the flashiest feature Anthropic shipped this cycle. It might be my favorite, though. Go poke at it.
