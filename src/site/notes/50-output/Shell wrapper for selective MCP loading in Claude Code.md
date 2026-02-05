---
{"dg-publish":true,"permalink":"/50-output/shell-wrapper-for-selective-mcp-loading-in-claude-code/"}
---

# Shell wrapper for selective MCP loading in Claude Code
[[Mini case study\|Mini case study]] [[10-journal/2026-02-05\|2026-02-05]]

### Why I built this

I kept editing `.mcp.json` every time I started a Claude Code session. Some tasks need Jira and Slack. Others need Confluence. Loading all MCPs wastes context window and slows startup. Switching configs manually felt like unnecessary friction for something that should take seconds.

MCP tools are powerful, but they come with overhead. Each loaded server adds to your context window budget. When you only need Jira for a quick ticket lookup, loading Confluence, Slack, and Miro is wasteful. The current workflow forces a choice: either maintain multiple `.mcp.json` files and swap them, or accept the bloat. Neither scales well when you switch contexts multiple times per day.

### How it works

I created a shell function that wraps the `claude` command. It intercepts arguments starting with `+` as MCP selectors, uses `jq` to filter a master config file, and passes the result to Claude's `--mcp-config` flag. All other arguments pass through unchanged.

The `+` prefix syntax was the critical decision. It doesn't conflict with existing Claude flags (which use `-` and `--`), it's fast to type, and reads naturally ("add jira, add slack"). I initially tried `+?` for help but zsh interprets `?` as a glob. Switching to `++` solved it while staying intuitive.

Add to `~/.zshrc`:

```bash
claude() {
  local mcps=()
  local args=()

  for arg in "$@"; do
    if [[ "$arg" == "++" ]]; then
      echo "Available MCPs:"
      jq -r '.mcpServers | keys[]' ~/.mcp-master.json
      return 0
    elif [[ "$arg" == +* ]]; then
      mcps+=("${arg:1}")
    else
      args+=("$arg")
    fi
  done

  if [ ${#mcps[@]} -eq 0 ]; then
    command claude "${args[@]}"
  else
    local filter=$(printf '"%s",' "${mcps[@]}" | sed 's/,$//')
    local config=$(jq --argjson keys "[$filter]" \
      '{mcpServers: .mcpServers | with_entries(select(.key | IN($keys[])))}' \
      ~/.mcp-master.json)
    command claude --mcp-config "$config" --strict-mcp-config "${args[@]}"
  fi
}
```

Master config (`~/.mcp-master.json`):

```json
{
  "mcpServers": {
    "miro": {
      "type": "http",
      "url": "https://mcp.miro.com"
    },
    "confluence": {
      "command": "/path/to/mcp-launcher",
      "args": ["CONFLUENCE_API_TOKEN", "/path/to/mcp-confluence-server"],
      "env": {
        "CONFLUENCE_URL": "https://wiki.example.com",
        "ENABLED_TOOLS": "search_cql,get_confluence_page_details"
      }
    },
    "jira": {
      "command": "/path/to/mcp-launcher",
      "args": ["JIRA_API_TOKEN", "/path/to/mcp-jira-server"],
      "env": {
        "JIRA_URL": "https://jira.example.com",
        "ENABLED_TOOLS": "get_jira_issue,search_jql"
      }
    },
    "slack": {
      "command": "/path/to/mcp-launcher",
      "args": ["SLACK_TOKEN", "/path/to/mcp-slack-server"],
      "env": {
        "ENABLED_TOOLS": "search_slack_messages,post_message"
      }
    }
  }
}
```

Usage:
```bash
claude +jira +slack -p "what tickets are in progress"
claude +confluence           # just confluence
claude ++                    # list available MCPs
claude                       # normal behavior, uses .mcp.json
```

### Results and limitations

Selecting MCPs now takes one extra word per server instead of file editing. Context window stays lean. The `++` command gives instant visibility into what's available. Normal Claude usage is unaffected when no `+` args are passed.

The approach also made me consolidate MCP configs. Instead of scattered `.mcp.json` files per project, I have one master file with clean, short keys (`jira` instead of `mcp-jira`).

**Limitations:** Requires `jq` installed. The `--strict-mcp-config` flag ignores project-level `.mcp.json` entirely when using `+` selectors. No tab completion for MCP names yet. If master config has syntax errors, the error message isn't friendly.

### What's next

- **Keep:** The `+` prefix syntax scales well and doesn't conflict with existing flags
- **Add:** Tab completion for MCP names using zsh's completion system
- **Try:** A `+all` shortcut and `+work` / `+personal` presets for common combinations
