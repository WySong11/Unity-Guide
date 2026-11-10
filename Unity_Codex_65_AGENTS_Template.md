# AGENTS.md — Unity 6.3 Project Instructions

## Purpose and scope
- This repository is a Unity **6.3 / URP / New Input System** game project.
- These rules apply from this directory downward. Check for additional nested `AGENTS.md` in any target subdirectory before editing.
- Prefer small, testable, reviewable changes. Respect higher-priority instructions and actual tool/sandbox permissions.

## Before every task
1. Restate the requested outcome, target scene/scripts, and acceptance criteria.
2. Inspect the affected files, `git status`, and relevant Unity asset dependencies. Protect uncommitted user edits.
3. **Read the appropriate rule document when your task touches that area** (see below). Do not claim documents were read unless inspected.
4. If a needed dependency, file, Unity tool, or runtime is unavailable, report the blocker rather than guessing.

## Rule document index
- **C# scripts, event subscriptions, gameplay architecture:** read `UNITY_CS_CODING_RULES.md`.
- **Unity Prefab / Scene / Asset / .meta / package changes:** read `UNITY_ASSET_RULES.md`.
- **Creating, renaming, moving, or deleting files:** read `FILE.md`.
- **Staging, commit, branch, reset, or push:** read `GIT.md`.
- **Unity Editor, Unity CLI, MCP, pipeline, build tooling:** read `UNITY_TOOLING.md`.
- **Compiling, Play Mode, tests, development builds:** read `BUILD.md`.
- **Recording change rationale or unexpected findings:** update `HISTORY.md` or `REVIEW_NOTES.md` only when the task asks for documentation or the team workflow requires it.
- **Project onboarding/overview:** read `READ.md`.

## Working rules
- Make only the smallest changes needed. Do not overwrite unrelated work or alter secrets, credentials, Firebase configuration, project packages, or source-controlled scenes without clear task need.
- Preserve asset GUIDs and `.meta` relationships. Prefer Unity Editor-supported operations for scene/prefab modifications when available.
- Do not execute destructive Git operations (`reset --hard`, `clean -fd`, force-push) without explicit user approval. Commit or push only when explicitly asked.
- When code changes: check reference handling, object lifecycle, event subscribe/unsubscribe symmetry, and Unity 6 API compatibility.
- Test in steps: static inspection and diff → available Unity compile → Play Mode → build/device only if feasible. Never report tests not run as passed.
- Present **changed files, key diff, checks actually run, results, blocked/not-run checks, and remaining risks**.

## Tool access and approvals
- At the start of a session, verify a required Unity CLI/MCP connection **once**; recheck on connection failure or explicit user request.
- A local AGENTS.md file does not grant OS, Git, Codex sandbox, web, tool, or network privileges. Follow the real environment and approval UI.

## Nested rules
- Check for a more specific `AGENTS.md` within the target file's directory tree. For example, `Assets/Scripts/AI/AGENTS.md` adds AI subsystem rules. Keep such guidance focused on that subtree.
