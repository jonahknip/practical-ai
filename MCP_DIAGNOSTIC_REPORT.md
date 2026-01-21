# MCP DIAGNOSTIC REPORT (Claude Desktop)
Generated: 2026-01-19

## 1) Summary / Status
**Overall:** ⚠️ Partially configured

- ✅ Claude Desktop config file exists and contains an MCP server entry.
- ✅ Python runtime referenced in config exists.
- ✅ `work-context` server script exists and is executable.
- ⚠️ I cannot prove end-to-end tool invocation *inside Claude Desktop* from here (requires you to run one in-app test), but local prerequisites look OK.
- ⚠️ Multiple Claude Extensions are installed; one is disabled.

## 2) Claude Desktop MCP Config

### Primary config
**Path:** `/Users/jonahknip/Library/Application Support/Claude/claude_desktop_config.json`

**Key contents:**
- `preferences.localAgentModeTrustedFolders`: includes `/Users/jonahknip`
- `mcpServers`:
  - `work-context`
    - command: `/Library/Frameworks/Python.framework/Versions/3.14/bin/python3`
    - args: `/Users/jonahknip/mcp-servers/work-context/server.py`

✅ This is structurally correct.

### Other config file
**Path:** `/Users/jonahknip/Library/Application Support/Claude/config.json`

Contains general Claude settings / token caches (not MCP server definitions).

## 3) Installed Claude Extensions (Local)
Found in:
`/Users/jonahknip/Library/Application Support/Claude/Claude Extensions`

Installed extensions:
- `ant.dir.ant.anthropic.filesystem`
- `ant.dir.gh.k6l3.osascript`
- `ant.dir.gh.silverstein.pdf-filler-simple`
- `ant.dir.gh.wonderwhy-er.desktopcommandermcp`

Extension enablement settings (Claude Extensions Settings):
- filesystem: **isEnabled = false**
- osascript: **isEnabled = true**
- pdf-filler-simple: **isEnabled = true**
- desktopcommandermcp: **isEnabled = true**

✅ You have multiple tools available via extensions.
⚠️ Filesystem is currently disabled.

## 4) Runtime Dependencies (Mac)
Verified installed:
- Node: `/opt/homebrew/bin/node` (v25.2.1)
- npm: `/opt/homebrew/bin/npm` (v11.6.2)
- Python: `/Library/Frameworks/Python.framework/Versions/3.14/bin/python3` (Python 3.14.2)

✅ These runtimes exist.
⚠️ Node v25 is very new; most MCP servers target Node 18/20. If a Node-based MCP server fails, install Node 20 LTS and use it for MCP.

## 5) MCP Server: work-context
**Server path:** `/Users/jonahknip/mcp-servers/work-context/server.py`

Checks performed:
- File exists and is executable ✅
- Script compiles (no syntax errors) ✅
- Running the command exited without obvious import errors ✅

⚠️ Note: Many MCP servers are designed to run over stdio and will appear to “hang” waiting for messages. A quick launch doesn’t guarantee tool wiring is correct in Claude.

## 6) REQUIRED MANUAL VERIFICATION (Claude Desktop UI)
Because I cannot drive Claude Desktop from here, do this 60-second test:

1. Open **Claude Desktop**
2. Go to **Settings → Developer → Edit Config**
3. Confirm `work-context` is present under `mcpServers`
4. Restart Claude Desktop
5. Start a new chat and try:
   - “List available tools”
   - Or if `work-context` exposes specific tools, call one explicitly

**Pass criteria:** Claude shows MCP tools available and can invoke one without error.

## 7) iPhone Compatibility Reality Check
Claude on iPhone **cannot run local MCP servers** (no local daemon, no local file system access).

To use MCP-like capabilities on iPhone, you typically need:
- A **remote MCP host** (server running on a machine reachable over the internet/VPN), OR
- A **bridge** service running on your Mac (and exposing an API), OR
- Use Claude iOS normally (no MCP), relying on cloud-accessible docs.

If your goal is “seamless Mac + iPhone,” the practical approach is:
- Keep MCP on Mac for file/system actions
- Sync important docs to cloud (Google Drive/Dropbox/iCloud)
- On iPhone, work from cloud links and copy/paste into Claude

## 8) Fixes / Improvements Recommended

### A) Enable filesystem extension (optional but useful)
File shows disabled:
`/Users/jonahknip/Library/Application Support/Claude/Claude Extensions Settings/ant.dir.ant.anthropic.filesystem.json`

Set `"isEnabled": true` (then restart Claude Desktop).

### B) Prefer Node 20 LTS for MCP servers
If any Node-based MCP server fails under Node 25:
- Install Node 20 LTS (Homebrew or nvm)
- Point MCP server commands to Node 20

### C) Keep MCP server config consolidated
Right now:
- `claude_desktop_config.json` contains your `mcpServers`
- Extensions are managed separately

That’s OK; just be aware you have two systems:
- Extensions (.mcpb / extensions)
- MCP servers (claude_desktop_config.json)

---

## 9) What I Need From You (to declare “perfectly set up”)
Answer these:
1) In Claude Desktop, do you see `work-context` in the tools list?
2) When you run a tool, do you get any errors?
3) Do you want filesystem enabled (yes/no)?
4) What exact MCP servers did you intend to install besides `work-context`?

