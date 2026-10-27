---
name: btt
description: Build this thing. Run when the user's message starts with "btt" (or /btt) followed by an idea, e.g. "btt thing that makes the crab character dance when I send a prompt". Pick the right kind of thing to build (Claude skill, Claude Code mod or plugin, hook, slash command, browser extension, game mod, script, app, web page), say which and why in one line, then build it, verify it and report.
license: MIT
metadata:
  author: kevlar10x
  version: "1.0.0"
  repository: https://github.com/kevlar10x/btt
---

# BTT: build this thing

The user gives an idea and leaves the "what kind of thing is this" decision to you. Make that call quickly and well, then build it.

## 1. Pick the form

Choose the lightest form that fully does the job, based on where it has to run and who will use it:

| The idea... | Build a |
|---|---|
| Changes how Claude works, knows or responds | Claude skill (`~/.claude/skills/<name>`), via skill-creator |
| Changes Claude's interface (panels, animations, transcript look) | Claude Code mod/plugin (`~/.claude/mods/<name>`), via plugin-authoring |
| Runs a script when something happens in Claude (prompt sent, tool used, session start) | Hook, via update-config; a mod if it also needs UI |
| Is a command I type | Skill or slash command |
| Works on websites in the browser | Chrome extension (Manifest V3) |
| Changes a game | Game mod (follow any modding rules in the user's CLAUDE.md) |
| Runs on a schedule | Routine (scheduled task) |
| Is a desktop tool or automation | Script or small app |
| Is something to look at or share | Web page or artifact |

If two forms fit, take the one with fewer moving parts. If the idea can't work as described (the platform doesn't allow it), say so and offer the closest thing that can.

Use the helper skills named above when they're installed; without them, do the same job directly.

## 2. Say it in one line

```
btt: <name> → <form>, because <one reason>
```

Then check for gaps (missing cases, unclear scope, risks), answer them yourself and list them compactly, one line each. Use the gap-check skill if it's installed. Ask the user only what truly needs them.

## 3. Build it

- Name: short, lowercase, hyphenated.
- Location: skills in `~/.claude/skills/<name>`, Claude mods in `~/.claude/mods/<name>`, everything else in `~/Documents/claude projects/<name>` unless the user's CLAUDE.md names another projects folder.
- `git init` and a CHANGELOG.md. Credit the user as author under the name or alias their CLAUDE.md gives, and follow its other project rules.
- Install it locally so it's live (skill folder, plugin dir, hook, extension loaded unpacked) when that's safe and reversible.
- Don't publish (GitHub, Nexus, stores) until the user says so. Offer it at the end.

## 4. Verify and report

Test it the way it will actually be used. Report in a few lines: what was built and where, how to use or trigger it, what was verified and what wasn't, and how to remove it.
