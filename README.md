# Skills

A collection of [Claude Code](https://docs.anthropic.com/en/docs/claude-code) skills by [laat](https://laat.dev).

## Available Plugins

| Plugin | Description |
|--------|-------------|
| [format-guard](skills/format-guard/SKILL.md) | Set up a git pre-push hook that rejects pushes when code isn't formatted |
| [readme-assert](skills/readme-assert/) | Verify and convert README code examples into testable blocks using readme-assert |
| [mor](https://github.com/laat/mor) | AI-accessible notes you actually own — plain markdown on your disk |

## Installation

```sh
claude plugin marketplace add laat/skills
```

## Usage

Once installed, invoke a skill with `/` in Claude Code:

```
/format-guard
```
