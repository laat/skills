---
name: readme-assertify
description: Convert existing README code examples into testable readme-assert blocks by adding test tags and assertion comments.
user-invocable: true
allowed-tools: Bash Glob Grep Read Edit
---

# /readme-assertify

Convert existing README code examples into testable
[readme-assert](https://readme-assert.laat.dev/) blocks by adding `test` tags
and assertion comments.

## Core Workflow

Process markdown files to identify JavaScript/TypeScript code blocks and
categorize them:

- **Already tagged blocks** are skipped
- **Blocks with assertion syntax** get the `test` tag added
- **Convertible blocks** receive new assertion comments using `//=>` notation
- **Non-convertible blocks** (setup code, shell commands, external dependencies)
  remain untouched

## Key Transformation Patterns

Target expressions that can be self-verifying: bare function calls,
`console.log()` statements, and variable assignments with demonstrable results.
Expected values come from surrounding documentation or code context analysis.

## Important Principles

The conversion prioritizes readability — assertion comments should appear as
natural annotations rather than test scaffolding. Avoid forcing testability on
conceptual or incomplete snippets; a partially-tested README provides more value
than an awkwardly over-instrumented one.

Blocks demonstrating side effects like file writes or HTTP requests typically
remain unconverted unless mocking is feasible.
