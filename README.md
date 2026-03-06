# /generate-ticket

A [Claude Code](https://claude.com/claude-code) skill that generates structured project tickets (YouTrack/JIRA) from user stories, metric sheets, PRDs, or feature descriptions.

## Quick Start

```bash
# 1. Install the skill
git clone https://github.com/101WaysToBug/generate-ticket.git ~/.claude/skills/generate-ticket

# 2. Restart Claude Code, then use the slash command
/generate-ticket "As a data analyst, I need a real-time dashboard showing call sentiment scores"
```

That's it — Claude will ask which team the ticket is for and generate a structured, ready-to-file ticket.

## Installation

### Option 1: Global skill (available in all projects)

```bash
git clone https://github.com/101WaysToBug/generate-ticket.git ~/.claude/skills/generate-ticket
```

### Option 2: Project-level skill (available only in one project)

```bash
cd your-project
git clone https://github.com/101WaysToBug/generate-ticket.git .claude/skills/generate-ticket
```

Restart Claude Code after installing. The `/generate-ticket` slash command will be available immediately.

## Usage

### With inline content

Provide your user story, feature description, or requirements directly:

```bash
/generate-ticket "Build an API endpoint that returns paginated search results with filtering by date range and category"
```

### Interactive mode

Run without arguments and Claude will prompt you to paste your content:

```bash
/generate-ticket
```

Claude will ask you to paste your user stories, metric sheet, PRD, or feature description, then generate the ticket.

### Workflow

1. You provide content (inline or when prompted)
2. Claude asks which team the ticket is for: `[Data]`, `[Eng]`, `[FE]`, `[Design]`, `[DevOps]`, or `[QA]`
3. Claude generates a structured draft ticket
4. You review, edit, and file the ticket in your project tracker

## What You Get

Every generated ticket includes these sections:

| Section | Purpose |
| --- | --- |
| **Summary** | Prefixed title with team tag (e.g., `[Data] Build Dashboard for...`) |
| **Overview** | What needs to be built and why, with link to source doc |
| **Why This Matters** | Business justification connecting work to outcomes |
| **High-Level Approach** | Recommended implementation strategy without being overly prescriptive |
| **Acceptance Criteria** | Specific, testable checklist defining "done" |

Optional sections (Dependencies, Out of Scope, Source Document Link) are included when relevant.

### Example Output

Here's a snippet of what a generated ticket looks like:

```markdown
# [Data] Build Call Analytics Dashboard

## Overview
Build a **real-time analytics dashboard** for the Call Analytics feature
that surfaces key metrics — sentiment scores, call duration trends, and
agent performance — to Operations Managers and Team Leads.

## Why This Matters
Call quality monitoring is currently a manual, reactive process — ops teams
only discover issues after customer complaints. A real-time dashboard enables
proactive intervention, reducing escalation rates and improving CSAT.

## Acceptance Criteria
- [ ] **Sentiment trend widget** displays average sentiment score over
      configurable time ranges (1h, 24h, 7d, 30d)
- [ ] **Data refresh cadence** is 5 minutes or less for all widgets
- [ ] **Dashboard load time** is under 3 seconds for datasets up to 100K calls
```

See [examples/sample-ticket.md](examples/sample-ticket.md) for a full example.

## Supported Team Prefixes

| Prefix | Team |
| --- | --- |
| `[Data]` | Data/Analytics (dashboards, pipelines, queries) |
| `[Eng]` | Backend Engineering (APIs, services, infrastructure) |
| `[FE]` | Frontend (UI components, UX changes) |
| `[Design]` | Design (mockups, prototypes, design systems) |
| `[DevOps]` | Infrastructure and deployment |
| `[QA]` | Testing and quality assurance |

## Tips for Best Results

- **Be specific in your input.** The more detail you provide (metrics, user roles, constraints), the better the acceptance criteria will be.
- **Paste from existing docs.** Copy-paste directly from your Notion PRD, Google Doc, or metric sheet — the skill is designed to extract and structure requirements from raw content.
- **One ticket at a time.** For best results, generate one focused ticket per invocation rather than bundling multiple features.
- **Review before filing.** Tickets are generated as drafts. Always review and adjust before adding to your backlog.
- **Include context.** Mention the target users, existing systems, or constraints so the ticket includes relevant non-functional requirements (performance, access control, etc.).

## Customization

Edit `SKILL.md` to adjust:

- **Ticket sections** — Add or remove sections to fit your team's workflow
- **Team prefixes** — Add custom tags for your organization (e.g., `[ML]`, `[Platform]`)
- **Writing style** — Adjust tone, formatting, or terminology
- **Acceptance criteria rules** — Customize what "testable" means for your team

## Directory Structure

```
generate-ticket/
├── SKILL.md              # Skill definition and prompt
├── README.md             # This file
└── examples/
    └── sample-ticket.md  # Reference example
```

## Automate Ticket Filing

By default, `/generate-ticket` outputs a draft ticket for you to copy into your project tracker. To skip the copy-paste step and create tickets directly, install a JIRA or YouTrack MCP server:

- **JIRA** — Install an [Atlassian MCP server](https://github.com/sooperset/mcp-atlassian) so Claude can create issues in your JIRA project automatically.
- **YouTrack** — Install a [YouTrack MCP server](https://github.com/nicholasgriffintn/youtrack-mcp-server) to file tickets straight into YouTrack.

Once configured, Claude can create the ticket in your tracker immediately after generating it — no manual filing required.

## Requirements

- [Claude Code](https://claude.com/claude-code) CLI installed and authenticated

## License

MIT
