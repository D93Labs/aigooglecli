# Google Workspace AI Assistant for Claude Code

An AI-powered personal assistant built with Claude Code and connected to Google Workspace via MCP. It reads your Gmail, manages your calendar, tracks your tasks, and keeps you a step ahead — all from the terminal.

## How It Works

```
You (Terminal) → Claude Code → MCP Protocol → gws CLI → Google APIs (Gmail + Calendar + Tasks)
```

Open Claude Code in this project folder and the assistant loads its personality, context, and tool access from `CLAUDE.md` automatically every session. Slash commands give you one-word access to common daily workflows.

## Capabilities

### Can Do

- **Email** — Search, read, label, archive, trash, and organize your Gmail inbox
- **Calendar** — View and create events across multiple calendars (primary, social media, family)
- **Tasks** — View, create, and complete tasks via Google Tasks
- **Daily Briefings** — Summarize your day, week, or upcoming schedule with context
- **Inbox Triage** — Flag what needs attention, surface what matters most
- **Weather** — Current conditions and 7-day forecasts via Open-Meteo (no API key required)
- **WiFi Diagnostics** — Full access point scan with signal, SNR, latency, and nearby networks
- **Slash Commands** — Quick triggers for common daily workflows (see below)
- **Website Audits** — Crawl your organization's site for stale content, broken links, and accessibility issues
- **Email Drafting** — Draft replies that match your natural voice by reading your sent history first
- **Social Media** — Draft posts for Facebook, Instagram, and X simultaneously

### Cannot Do

- Send emails (explicitly blocked — scope is authorized but sending is disabled by rule)
- Send calendar invites to others (`sendUpdates: "none"` enforced on all calendar writes)
- Access Google Drive (not currently authorized — re-auth required to enable)
- Access Google Sheets (not currently authorized — re-auth required to enable)

## Slash Commands

| Command | What it does |
|---------|-------------|
| `/morning` | Morning briefing — weather, calendar, emails, tasks, and what to focus on |
| `/today` | Real-time check-in — what's happened, what's left, what to focus on next |
| `/tomorrow` | Prep for tomorrow — calendar, inbox, tasks, and what to handle tonight |
| `/calendar` | What's on your calendar today |
| `/week` | Walk through your week, what to prep for, and tasks due this week |
| `/month` | Scan the rest of the month and flag anything important |
| `/inbox` | Unread emails from today with anything flagged for response |
| `/reply` | Draft a reply to the most recent email needing a response |
| `/recap` | Full recap of the week — meetings, emails, and what got done |
| `/social-draft` | Draft a social media post for your organization |
| `/wifi` | WiFi access point scan and full diagnostic report |
| `/weather` | Current conditions and today's hourly forecast |
| `/weather-week` | 7-day forecast |
| `/refresh-creds` | Refresh Google Workspace MCP credentials when auth breaks |

## Project Structure

```
cli/
├── .claude/
│   ├── commands/            # Slash commands (/morning, /inbox, /today, etc.)
│   └── settings.local.json  # Claude Code permissions and MCP tool allowlist
├── CLAUDE.example.md        # ← Template: copy to CLAUDE.md and fill in your values
├── mcp.example.json         # ← Template: copy to .mcp.json and update paths
├── setup.html               # Visual setup guide — open in any browser
├── .gitignore               # Excludes CLAUDE.md, .mcp.json, and all credential files
└── README.md                # This file
```

> **CLAUDE.md** and **.mcp.json** are excluded from git by design — they contain your personal calendar IDs, task list IDs, and file paths. Copy the example files and fill in your own values.

## Setup

**Quick start:** Open `setup.html` in a browser for a full visual walkthrough.

### Short version

1. **Install gws CLI**
   ```bash
   npm install -g @googleworkspace/cli
   ```

2. **Authenticate with Google**
   ```bash
   gws auth login --account YOUR_EMAIL@yourdomain.com --full -s gmail,calendar,tasks
   ```

3. **Copy and configure the template files**
   ```bash
   cp CLAUDE.example.md CLAUDE.md
   cp mcp.example.json .mcp.json
   ```
   Then open both files and replace every placeholder with your real values (email, calendar IDs, task list IDs, username, location).

4. **Open the folder in Claude Code** — MCP loads automatically. Test with `/morning` or `/today`.

See `setup.html` for the full customization guide, including how to find your calendar and task list IDs.

## Prerequisites

- [Claude Code](https://claude.ai) with Claude Max subscription
- [`gws` CLI](https://github.com/googleworkspace/cli) — `npm install -g @googleworkspace/cli`
- Node.js v14+ (for credential management)
- macOS (some commands use macOS-specific tools like `system_profiler` for WiFi diagnostics)

## OAuth Scopes

Minimal permissions — only what's needed:

| Scope | Access |
|-------|--------|
| `gmail.modify` | Read, label, trash, organize emails (sending disabled by rule) |
| `gmail.settings.basic` | Email settings and filters |
| `gmail.settings.sharing` | Mail delegation settings |
| `gmail.labels` | Create and edit email labels |
| `calendar` | Full calendar read/write (invites silenced) |
| `tasks` | Read and write Google Tasks |

**Intentionally excluded:** `gmail.send`, `drive`, `spreadsheets` — can be added via re-auth when needed.

## Model Recommendations

| Model | Best For |
|-------|----------|
| **Sonnet 4.6** (default) | Daily use — fast, handles all Workspace tools well |
| **Opus 4.6** | Heavy lifting — drafting, deep research, complex multi-step tasks |

Switch anytime with `/model` in Claude Code.

## Example Prompts

```
"Summarize my day and tell me what I should focus on."
"What's on my calendar for next week? Flag anything I should prep for."
"Show me unread emails I need to handle before Monday."
"Draft a reply to the last email from [Name] — keep it short."
"Add a task to follow up with the team about the newsletter."
"What's the weather looking like this week?"
```

## Troubleshooting

**MCP tools return 401 or scope errors**
Run `/refresh-creds` inside Claude Code, then restart Claude Code to reload the MCP server.

**Need to re-authenticate from scratch**
Run in a regular terminal (not Claude Code):
```bash
gws auth login --account YOUR_EMAIL@yourdomain.com --full -s gmail,calendar,tasks
```

**Calendar event creation fails**
Known bug in gws v0.5.0 — `calendar_events_insert` via MCP fails with a type error. A Python subprocess workaround is documented in `CLAUDE.md` and used automatically.

## Related

- **gws CLI** — [github.com/googleworkspace/cli](https://github.com/googleworkspace/cli)
- **Claude Code** — [claude.ai](https://claude.ai)
- **Open-Meteo** — [open-meteo.com](https://open-meteo.com) (free weather API, no key required)

---

Built for communications teams using Claude Code + Google Workspace.
