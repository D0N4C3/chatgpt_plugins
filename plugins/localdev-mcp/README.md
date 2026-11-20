# LocalDev MCP Plugin

Connects ChatGPT Desktop / Codex to your self-hosted **LocalDev MCP** server running on `http://127.0.0.1:8765/mcp`.

## Prerequisites on Your Windows Laptop

1. Start LocalDev MCP (`C:\Users\T\LocalDev-MCP`):
   ```powershell
   .\scripts\start.ps1
   ```
2. Register at least one authorized project folder in the local dashboard (`http://127.0.0.1:8766`) or via `.\scripts\register-project.ps1`.
3. Install this plugin from the marketplace (`https://github.com/D0N4C3/chatgpt_plugins.git`).
4. When prompted to authenticate via OAuth (`http://127.0.0.1:8765/oauth/authorize`), paste your local `Dashboard Admin Token` (`.\scripts\status.ps1 -ShowTokens`) and click **Approve & Connect**.
