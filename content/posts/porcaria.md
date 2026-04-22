---
title: "Porcaria: A Voice Pipeline for My Linux Desktop"
date: "2026-04-21T14:00:00-07:00"
lastmod: "2026-04-21"
draft: false
author: "Travis Nesbit"
description: "Why I built porcaria — a portable voice-AI pipeline glued into my Hyprland keybinds, with local models at the desk and cloud fallbacks on the road."
summary: "A small voice-AI pipeline I built to wire microphone → transcription → optional LLM cleanup → clipboard, note file, or task CLI behind a few Hyprland keybinds. Local models on the GPU box, cloud on the travel laptop, same CLI on both."
tags: ["linux", "hyprland", "voice", "ai", "python", "tools"]
categories: ["Tools"]
---

I spend most of my day on an Arch/Hyprland workstation with a GPU, and a second chunk of it on a travel laptop. I wanted a dictation setup that felt native to both — press a key, talk, get text — and nothing I tried quite fit my workflow. I wanted to marry(largely) local models with the highly composable Hyprland environment so that time-saving, quality-improving behaviors are a simple keybind a way. So I built [porcaria](https://github.com/geekmdtravis/porcaria).

## What it is

A small voice-AI pipeline behind a CLI and a long-lived daemon. The flow is deliberately boring:

1. **Capture** audio from PulseAudio/PipeWire.
2. **Transcribe** via pluggable ASR — local Parakeet on the workstation, OpenAI Whisper on the road.
3. *(Optional)* **Clean** the transcript with an LLM — local llama.cpp (fallback to OpenRouter).
4. **Route** it — clipboard, a quick-note file, TTS playback, or my task CLI [fazerei](https://github.com/geekmdtravis/fazerei).

Provider choice is a line in `config.toml`. Home profile for local models, travel profile for cloud, same CLI on both machines.

## Why Hyprland makes it click

The name is Portuguese something that roughly translates into "junk" or "mess" — honest, because porcaria's job is mostly turning my rambling into something structured. To accomplish that, I wanted a highly composable system that pairs naturally with my custom keybinding system defined in my `hyprland.conf`:

```conf
# Engage voice recording
bind = SUPER_ALT,       D, exec, porcaria dictate # Process through Parakeet only for transcript production

# Route recording
bind = SUPER_ALT_SHIFT, D, exec, porcaria dictate --clean # Forward Parakeet transcript to a local LLM for cleanup, translation, etc.
bind = SUPER_ALT,       V, exec, porcaria dictate --route task # Update, add, mark done, etc TODO's in my system
bind = SUPER_ALT,       N, exec, porcaria dictate --sinks note,clipboard,speaker # Send the output to three different locations
```

**The start press only begins recording. The stop press decides what happens to the transcript.** I can start dictating with a bare `Super+Alt+D`, talk for three minutes, realize it's getting messy, and stop with `Super+Alt+Shift+D` — porcaria runs the full transcript through the LLM cleanup before dropping it on the clipboard. Or stop with `Super+Alt+V` and the transcript gets handed to a custom, highly composable TODO service that I built called `fazerei` to parse as a command and execute.

A keybinding-centric workflow with that one design choice — route at stop time, not start time — is what made voice feel usable to me. I don't have to predict what I'm going to say before I say it.

## What it's not

Polished. Productized. Or doing anything technically novel — it's glue around other people's excellent models. It is, however, the thing I reach for several times a day, and it works the same on both machines. I'd also estimate it saves me 30 to 60 minutes per day!

Code, config reference, and the full keybind cheat-sheet live at [github.com/geekmdtravis/porcaria](https://github.com/geekmdtravis/porcaria).
