---
name: localdev-mcp
description: Use the LocalDev MCP server to inspect installed developer runtimes, browse and edit authorized project files, and run builds/tests on the user's Windows laptop.
---

# LocalDev MCP Workflow

1. **Discover environments and authorized projects first:**
   - Call `system_info` and `list_projects` before accessing any project path.
   - Only registered project IDs are accessible; never attempt paths outside registered roots.
   - Call `list_dev_environments` to see which SDKs (Node.js, Python, PHP/Laravel, Flutter, Android, Godot, Git, Go, GCC) are installed and operational.

2. **Inspect and edit files safely:**
   - Use `directory_tree`, `list_directory`, `search_files`, and `read_file` to understand code before editing.
   - Use `write_file` to create new files or update files (backups are created automatically) and `apply_patch` for targeted edits.
   - Sensitive files (`.env`, private keys, `.git/config`) are blocked by server policy.

3. **Run commands and long-running builds:**
   - Prefer language-specific tools (`node_execute`, `npm_task`, `python_execute`, `python_tests`, `php_execute`, `laravel_artisan`, `composer_task`, `flutter_doctor`, `flutter_build`, `android_devices`, `android_build`, `godot_command`, `git_status`, `git_diff`, `git_commit`).
   - For long builds/tests, use `start_background_job` (or `background: true`) and poll with `job_status` / `job_logs`.
   - If a tool returns `status: "approval_required"` with an `approvalRequest.id` (`apr_...`), ask the user to approve it in their local LocalDev MCP Dashboard (`http://127.0.0.1:8766`) or via `.\scripts\approve.ps1 -Id <id> -Approve`, then retry the exact same call with `approvalId`.
