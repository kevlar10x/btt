# btt: build this thing

A Claude skill for when you know what you want but not what shape it should take. Start a message with `btt` and an idea, and Claude decides what kind of thing to build, tells you which and why in one line, then builds it, tests it and reports back.

## How it picks

| The idea... | btt builds a |
|---|---|
| changes how Claude works or responds | Claude skill |
| changes Claude Code's interface | Claude Code mod or plugin |
| runs when something happens in Claude | hook |
| is a command you type | skill or slash command |
| works on websites | Chrome extension |
| changes a game | game mod |
| runs on a schedule | scheduled task |
| is a desktop tool or automation | script or small app |
| is something to look at or share | web page or artifact |

When two forms fit, it takes the one with fewer moving parts. If the idea can't work as described, it says so and offers the closest thing that can.

## Example

A real first reply to `btt a button that saves the web page I'm reading as a markdown file`. It ran in plan mode, so nothing was built yet. Trimmed, with the home folder shortened to `~`:

```
I'll build page-to-md as a Chrome extension: a toolbar button that saves the
page you're reading as a .md file. An extension is the lightest thing that
works on any site.

Gaps:
1. Whole page or just the main text? → Main text only (no menus, ads or
   footers). If that finds nothing, it saves the whole page.
2. Text selected on the page? → Saves only the selection (assumed, say if wrong).
3. Pages Chrome blocks extensions from (chrome://, the Web Store, PDFs)?
   → A red "!" on the button with the reason.
4. File name and where it goes? → <page title>.md in your normal Downloads
   folder. The top of the file has the title, the page's link and the date saved.
5. Permissions? → Only the current tab and downloads. It makes no network calls.

The project goes in ~/Documents/claude projects/page-to-md/, credited to kevlar10x.
```

Out of plan mode it goes on to build and test the thing, installs it locally when that's safe and easy to undo, and reports what it made, how to use it, what it checked and how to remove it. It asks you only what it can't settle itself.

## Install

Claude Code, as a skill:

```
npx skills add kevlar10x/btt -g
```

Claude Code, as a plugin:

```
/plugin install btt --marketplace kevlar10x/btt
```

Installed this way, it runs as `/btt:btt`.

In the desktop app, where `/plugin` doesn't run: click + next to the prompt box, then Plugins → Add marketplace with `kevlar10x/btt` → Add plugin.

Or copy `skills/btt/SKILL.md` into `~/.claude/skills/btt/`.

claude.ai: download `btt.zip` from the [latest release](https://github.com/kevlar10x/btt/releases/latest) and upload it under Settings → Capabilities → Skills. On claude.ai it can still pick the form and build what fits there, like pages, scripts and skill files to download. Hooks, mods and local installs need Claude Code.

## Use

Start a message with `btt` (or `/btt` in Claude Code) and describe the idea in plain words:

- `btt thing that makes the crab character dance when I send a prompt`
- `btt a button that saves the page I'm reading as markdown`
- `btt remind me to stretch every hour while I work`

Where things go: skills in `~/.claude/skills/<name>`, Claude Code mods in `~/.claude/mods/<name>`, everything else in `~/Documents/claude projects/<name>`, unless your CLAUDE.md names another projects folder. Each project gets `git init` and a CHANGELOG.md, with you credited under the name your CLAUDE.md gives.

btt never publishes anything (GitHub, Nexus, stores) until you say so. It offers at the end.

If skill-creator, update-config or gap-check are installed, btt uses them; without them, Claude does the same work directly.

If it doesn't start when you type `btt`, call it with `/btt`, and check that `SKILL.md` sits in a folder named `btt`. Bugs and ideas go in [issues](https://github.com/kevlar10x/btt/issues).

## Privacy

btt is one instruction file. It runs no scripts and sends nothing anywhere. Claude builds with its usual tools, under the permissions you've set, and what it builds lives in your own folders.

## Uninstall

```
npx skills remove btt -g
```

If you installed the plugin: `claude plugin uninstall btt`. If you copied the file, delete `~/.claude/skills/btt/`. Things btt built stay where it put them.

## Credit

Made by kevlar10x. Sister skill to [gtp](https://github.com/kevlar10x/gtp), which grills a finished product from the user's side.

MIT license. The original is at https://github.com/kevlar10x/btt.

Tips are optional: https://ko-fi.com/kevlar10x
