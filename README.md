<p align="center"><img src="logo.png" width="96" alt="JobsGlitch"></p>

# JobsGlitch MCP server

Search over a million live jobs taken straight from employers' own hiring systems.

JobsGlitch indexes jobs from Greenhouse, Lever, Workday, Ashby, SmartRecruiters, iCIMS, Amazon, Google and others, across 85+ countries and every sector, from interns to C-suite. Jobs are not copied from other job boards, and every listing links to the employer's own posting.

Connect it to your assistant and ask in plain language: search by role, skills, location, pay, seniority, employment type and remote; open a job for the full listing and the employer's apply link; find similar roles; see what a role pays and where it is hiring.

**Endpoint:** `https://jobsglitch.com/mcp` (Streamable HTTP). Older clients: `https://jobsglitch.com/mcp/sse` (SSE).

**No key needed.** Without one, each address gets 30 tool calls a minute, 500 a day and up to 20 jobs a call. A free key from [jobsglitch.com/developer](https://jobsglitch.com/developer?utm_source=github&utm_medium=repo&utm_campaign=mcp-listing), sent as `Authorization: Bearer <key>`, removes the daily cap and returns up to 50 jobs a call. All tools only read.

## Connect

**Claude (claude.ai and Claude Desktop):** Settings → Connectors → Add custom connector → URL `https://jobsglitch.com/mcp`.

**Claude Code:**

```bash
claude mcp add --transport http jobsglitch https://jobsglitch.com/mcp
```

**Cursor** (`~/.cursor/mcp.json`):

```json
{
  "mcpServers": {
    "jobsglitch": { "url": "https://jobsglitch.com/mcp" }
  }
}
```

**VS Code** (`.vscode/mcp.json`):

```json
{
  "servers": {
    "jobsglitch": { "type": "http", "url": "https://jobsglitch.com/mcp" }
  }
}
```

With a key, add the header, for example in Cursor:

```json
{
  "mcpServers": {
    "jobsglitch": {
      "url": "https://jobsglitch.com/mcp",
      "headers": { "Authorization": "Bearer YOUR_KEY" }
    }
  }
}
```

## Tools

| Tool | What it does |
|---|---|
| `search_jobs` | Search live jobs by keywords, skills, location, salary range, seniority, employment type, remote and posting age |
| `get_job_details` | The full listing for one job: description, responsibilities, qualifications, skills, pay and the employer's apply link |
| `find_similar_jobs` | Jobs most like a given job, optionally in chosen locations |
| `get_market_stats` | Salary bands, top hiring locations and top categories, for the whole index or one role or skill |
| `get_platform_stats` | Size of the index, remote and with-pay job counts, and the hiring systems covered |

## Try asking

1. Find senior product manager jobs in Berlin posted in the last 14 days that state the pay.
2. What do data engineer roles in London pay right now? Show me the salary bands.
3. Show remote Rust jobs, newest first, with apply links.
4. I like this job (paste a JobsGlitch link). Find ten similar roles in Toronto.
5. Is Stripe hiring for sales roles in Dublin? Give me the employer's apply links.

## REST API

The same data is available as a REST API: [OpenAPI spec](https://jobsglitch.com/api/public/v1/openapi.json) · [docs](https://jobsglitch.com/api/public/v1/docs).

## Links

[Website](https://jobsglitch.com/?utm_source=github&utm_medium=repo&utm_campaign=mcp-listing) · [Developer page](https://jobsglitch.com/developer?utm_source=github&utm_medium=repo&utm_campaign=mcp-listing) · [Privacy](https://jobsglitch.com/privacy) · [Terms](https://jobsglitch.com/terms) · Support: admin@jobsglitch.com

This repository holds the listing files (`server.json` for the [official MCP Registry](https://registry.modelcontextprotocol.io)); the server itself is hosted at jobsglitch.com.
