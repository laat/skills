# Skills

A collection of [Claude Code](https://docs.anthropic.com/en/docs/claude-code) skills by [laat](https://laat.dev).

## Available Plugins

| Plugin                                                       | Description                                                                      |
| ------------------------------------------------------------ | -------------------------------------------------------------------------------- |
| [git-hooks](plugins/git-hooks/)                              | Git hooks for code formatting — pre-push and pre-commit guards                   |
| [readme-assert](plugins/readme-assert/skills/readme-assert/) | Verify and convert README code examples into testable blocks using readme-assert |
| [mor](https://github.com/laat/mor)                           | AI-accessible notes you actually own — plain markdown on your disk               |

## Installation

```sh
claude plugin marketplace add laat/skills
```

## Usage

Once installed, invoke a skill with `/` in Claude Code:

```
/pre-push-format-guard
```
