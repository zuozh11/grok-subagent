---
name: grok-subagent
description: Delegate tasks to the user-configured local Grok Build CLI when the user requests Grok collaboration, implementation, review, or research.
---

# Grok collaboration

Use `grok_spawn` with an absolute `cwd`, a bounded task, and expected output. It inherits the MCP host environment and the normal Grok configuration. Omit `model` unless the user requests an override. This is not a read-only sandbox; delegate only the work authorized by the user.

Use this same tool for research or implementation. Legacy worker, search and interactive tools retain their specialized upstream behavior and are not the default in this fork.

Monitor `grok_status` with `after_revision` and up to 30 seconds of waiting. Relay material progress within 60 seconds. Retrieve `grok_result`, verify conclusions and file changes, and use `grok_send` for focused follow-ups in the same session.

Running turns reject `grok_send`. Wait until the turn completes, or call `grok_cancel`, wait until idle, then send the revised task. Never claim live message injection. Close agents with `grok_close` after the work is done.

If Grok requests interactive permission, report it; the bridge cancels that tool request instead of silently approving. Shell aliases and variables absent from the Codex process are not automatically imported. Never print credentials. Grok owns authentication and configuration. Do not spawn nested subagents.
