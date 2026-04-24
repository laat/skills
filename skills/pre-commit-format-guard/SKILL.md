---
name: pre-commit-format-guard
description: Set up a git pre-commit hook that rejects commits when staged files aren't formatted. Detects the repo's formatter and writes a check-only hook.
user-invocable: true
allowed-tools: Bash Glob Grep Read Write
---

# Pre-Commit Format Guard

Set up a git pre-commit hook that runs the project's code formatter in
**check-only** mode on **staged files only**, rejecting the commit if any staged
file is not properly formatted.

## Steps

1. **Detect the formatter.** Inspect the repo for formatter config files,
   dependency manifests, and tool configs (e.g. `.prettierrc`, `biome.json`,
   `pyproject.toml`, `Cargo.toml`, `go.mod`, `deno.json`, etc.). Use your
   knowledge of the ecosystem to determine which formatter the project uses,
   what the correct check-only command is, and which file extensions it handles.

2. **If no formatter is detected**, tell the user you couldn't find one and
   stop. Don't guess.

3. **Check for an existing pre-commit hook.** If `.git/hooks/pre-commit` already
   exists, show the user its contents and ask how to proceed — don't overwrite
   silently.

4. **Write the hook.** Create `.git/hooks/pre-commit` as a shell script that:
   - Lists staged files with `git diff --cached --name-only --diff-filter=d`
   - Filters to file extensions relevant to the detected formatter
   - Exits 0 (allows commit) if no matching files are staged
   - Runs the formatter's check command on only the matched staged files
   - On success: prints nothing — the hook should be completely silent when
     everything is fine
   - On failure: prints the formatter output followed by a clear message
     explaining what happened and how to fix it
   - Keeps it minimal — just the check, no extra logic

5. **Make it executable.** `chmod +x .git/hooks/pre-commit`

6. **Report.** Tell the user what formatter was detected, what check command the
   hook runs, and how to bypass it (`git commit --no-verify`) if needed.
