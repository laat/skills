---
name: pre-push-format-guard
description: Set up a git pre-push hook that rejects pushes when code isn't formatted. Detects the repo's formatter and writes a check-only hook.
user-invocable: true
allowed-tools: Bash Glob Grep Read Write
---

# Format Guard

Set up a git pre-push hook that runs the project's code formatter in **check-only** mode, rejecting the push if any file is not properly formatted.

## Steps

1. **Detect the formatter.** Inspect the repo for formatter config files, dependency manifests, and tool configs (e.g. `.prettierrc`, `biome.json`, `pyproject.toml`, `Cargo.toml`, `go.mod`, `deno.json`, etc.). Use your knowledge of the ecosystem to determine which formatter the project uses and what the correct check-only command is.

2. **If no formatter is detected**, tell the user you couldn't find one and stop. Don't guess.

3. **Check for an existing pre-push hook.** If `.git/hooks/pre-push` already exists, show the user its contents and ask how to proceed — don't overwrite silently.

4. **Write the hook.** Create `.git/hooks/pre-push` as a shell script that:
   - Captures the formatter's check command output (stdout and stderr)
   - On success: prints nothing — the hook should be completely silent when everything is fine
   - On failure: prints the captured output followed by a clear message explaining what happened and how to fix it
   - Keeps it minimal — just the check, no extra logic

5. **Make it executable.** `chmod +x .git/hooks/pre-push`

6. **Report.** Tell the user what formatter was detected, what check command the hook runs, and how to bypass it (`git push --no-verify`) if needed.
