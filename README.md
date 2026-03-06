# /generate-ticket

A [Claude Code](https://claude.com/claude-code) skill that generates structured project tickets (YouTrack/JIRA) from user stories, metric sheets, PRDs, or feature descriptions.

## Installation

### Option 1: Clone into your Claude Code skills directory

```bash
git clone https://github.com/101WaysToBug/generate-ticket.git ~/.claude/skills/generate-ticket
```

Then restart Claude Code. The `/generate-ticket` slash command will be available immediately.

### Option 2: Add as a project-level skill

```bash
cd your-project
git clone https://github.com/101WaysToBug/generate-ticket.git .claude/skills/generate-ticket
```

The skill will be available when working in that project.

## Usage

```bash
# Direct — provide content inline
/generate-ticket "As a data analyst, I need a real-time dashboard showing call sentiment scores so I can identify trending issues"

# Interactive — no arguments
/generate-ticket
# Claude will ask you to paste your user stories or content
```

### How it works

1. **With arguments** — Claude uses the provided content and asks which team the ticket is for (`[Data]`, `[Eng]`, `[FE]`, `[Design]`, `[DevOps]`, `[QA]`).
2. **Without arguments** — Claude asks you to paste your user stories, metric sheet, PRD, or feature description, then generates the ticket.

## Ticket Structure

Every generated ticket includes:

| Section | Purpose |
| --- | --- |
| **Summary** | Prefixed title with team tag (e.g., `[Data] Build Dashboard for...`) |
| **Overview** | What needs to be built and why |
| **Why This Matters** | Business justification |
| **High-Level Approach** | Recommended implementation strategy |
| **Acceptance Criteria** | Specific, testable checklist defining "done" |

Optional sections (Dependencies, Out of Scope, Source Document Link) are included when relevant.

## Supported Team Prefixes

| Prefix | Team |
| --- | --- |
| `[Data]` | Data/Analytics (dashboards, pipelines, queries) |
| `[Eng]` | Backend Engineering (APIs, services, infrastructure) |
| `[FE]` | Frontend (UI components, UX changes) |
| `[Design]` | Design (mockups, prototypes, design systems) |
| `[DevOps]` | Infrastructure and deployment |
| `[QA]` | Testing and quality assurance |

## Directory Structure

```
generate-ticket/
├── SKILL.md          # Skill definition and prompt
├── README.md         # This file
└── examples/
    └── sample-ticket.md  # Reference example
```

## Customization

Edit `SKILL.md` to adjust:

- **Ticket sections** — Add or remove sections to fit your team's workflow
- **Team prefixes** — Add custom tags for your organization
- **Writing style** — Adjust tone, formatting, or terminology
- **Acceptance criteria rules** — Customize what "testable" means for your team

## Requirements

- [Claude Code](https://claude.com/claude-code) CLI installed and authenticated

## License

MIT
