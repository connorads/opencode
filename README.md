# MCP Auth Workaround

> **Disclaimer:** This is an unofficial workaround branch. It is not endorsed by OpenCode or myself. Use at your own discretion.

## Background

Some remote MCP servers use an allowlist for OAuth client registration, which can prevent OpenCode from authenticating. This branch contains a workaround that allows OpenCode to authenticate with such servers.

## How it works

See the commit: https://github.com/connorads/opencode/commit/cbc7df7ceab07780934e2fc8825ad40147dadbc8

Official support for these MCP servers is hopefully coming soon:

- https://github.com/sst/opencode/issues/5636
- https://github.com/sst/opencode/issues/5583

## Instructions

### 1. Clone this branch

```bash
git clone -b mcp-auth-workaround https://github.com/connorads/opencode.git opencode-mcp-auth
cd opencode-mcp-auth
```

### 2. Install dependencies

```bash
bun install
```

### 3. Configure your MCP server

If not already done, add the remote MCP server to your `~/.config/opencode/opencode.json`:

```json
{
  "mcp": {
    "your-mcp-server": {
      "url": "https://mcp.example.com/mcp"
    }
  }
}
```

Replace `your-mcp-server` with whatever name you want, and update the URL accordingly.

### 4. Authenticate

```bash
bun dev mcp auth your-mcp-server
```

Replace `your-mcp-server` with the name you used in step 3.

This will open your browser to complete the OAuth flow.

### 5. Done!

The auth tokens are stored in `~/.opencode/mcp-auth.json` and will work with your regular OpenCode installation. You can now use the MCP server with vanilla OpenCode - you don't need this branch anymore.
