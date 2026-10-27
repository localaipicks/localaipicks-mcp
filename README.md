# Local AI Picks MCP server and agent skill

[Local AI Picks](https://localaipicks.com) lists open-weight AI models you can run on your own hardware: the latest version of each family, its weight files, how much memory each needs, where every number comes from, and whether the site has tested it. This repository holds the connection details for its remote MCP server and an [Agent Skill](skills/localaipicks/SKILL.md) that teaches an agent to use it. The service is hosted; there is nothing to install or run.

- **MCP endpoint:** `https://localaipicks.com/mcp` (Streamable HTTP)
- **Auth:** none. Free, no key, no account. Each IP address can make 60 requests a minute.
- **Registry name:** `com.localaipicks/localaipicks` in the [official MCP Registry](https://registry.modelcontextprotocol.io/v0/servers?search=com.localaipicks/localaipicks)
- **Docs:** [localaipicks.com/docs/mcp](https://localaipicks.com/docs/mcp)

## Connect

**Claude Code**

```bash
claude mcp add --transport http localaipicks https://localaipicks.com/mcp
```

**Cursor** (`~/.cursor/mcp.json`)

```json
{
  "mcpServers": {
    "localaipicks": { "url": "https://localaipicks.com/mcp" }
  }
}
```

**Codex** (`~/.codex/config.toml`)

```toml
[mcp_servers.localaipicks]
url = "https://localaipicks.com/mcp"
```

In Claude or ChatGPT, add it as a custom connector with the same URL.

## Tools

All tools are read-only.

| Tool | What it does |
| --- | --- |
| `list_tasks` | The tasks covered (text LLM, coding, speech to text, text to speech, image, video, music, translation, OCR), with the number of current models and the page for each |
| `find_models` | Current models for one task, in site order. Pass `memory_gb` (and `device`: `apple`, `gpu` or `cpu`) to keep only models whose smallest weight option fits |
| `get_model` | One model: parameters, license, context length, every weight option with file size and memory need, third-party scores with source and date, test status, links |
| `compare_models` | The same facts for 2 to 4 models side by side |

Answers carry the same numbers, sources and dates as the website, with a link to the page. There are no ratings and no speed estimates. Memory is estimated only for text LLMs; for other tasks it comes from vendor sources, and is `unknown` when neither exists.

## Agent skill

[`skills/localaipicks/SKILL.md`](skills/localaipicks/SKILL.md) follows the [Agent Skills](https://agentskills.io) format. Install it with

```bash
npx skills add localaipicks/localaipicks-mcp
```

or copy the folder into your agent's skills directory (for Claude Code, `~/.claude/skills/localaipicks/`).

## Support

support@localaipicks.com

## License

The files in this repository are MIT licensed. The data on localaipicks.com is not covered by this license.
