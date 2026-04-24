# Skills

A collection of agent skills by [laat](https://laat.dev).

## Available Skills

| Skill                                                      | Description                                                                           |
| ---------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| [pre-commit-format-guard](skills/pre-commit-format-guard/) | Set up a git pre-commit hook that rejects commits when staged files are not formatted |
| [pre-push-format-guard](skills/pre-push-format-guard/)     | Set up a git pre-push hook that rejects pushes when code is not formatted             |
| [readme-assert](skills/readme-assert/)                     | Verify README code examples using readme-assert                                       |
| [readme-assertify](skills/readme-assertify/)               | Convert README code examples into testable readme-assert blocks                       |

## Installation

```sh
npx skills add laat/skills
```

To list the skills without installing them:

```sh
npx skills add laat/skills --list
```

## Usage

Once installed, invoke a skill by name in your agent:

```
/pre-push-format-guard
```
