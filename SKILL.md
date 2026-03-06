---
name: generate-ticket
description: Generate structured project tickets (YouTrack/JIRA) from metric sheets, PRDs, or user stories. Use when the user asks to "create a ticket", "draft a ticket", "generate a ticket", or needs execution-ready tickets for engineering, data, or design teams.
argument-hint: "[user stories, PRD content, or feature description]"
version: 1.0.0
---

# Ticket Generator

Generate **structured project tickets** (YouTrack or JIRA) from user stories, metric sheets, PRDs, or conversational input. Produces draft tickets with testable acceptance criteria ready for cross-functional teams to execute.

## Input

If the user provided `$ARGUMENTS`, use that as the source content to generate a ticket from. If no arguments are provided, ask the user to paste their user stories, metric sheet, PRD, or describe the feature they need a ticket for.

## Step 1: Determine the Target Team

Ask the user which team the ticket is for. Present these options:

1. **[Data]** — Data/Analytics (dashboards, pipelines, queries)
2. **[Eng]** — Backend Engineering (APIs, services, infrastructure)
3. **[FE]** — Frontend (UI components, UX changes)
4. **[Design]** — Design (mockups, prototypes, design systems)
5. **[DevOps]** — Infrastructure and deployment
6. **[QA]** — Testing and quality assurance

If the user already specified the team prefix in their input, skip this step.

## Step 2: Generate the Ticket

Produce a ticket with the following sections in order:

### Required Sections

1. **Summary** — A clear, prefixed title (e.g., `[Data] Build Dashboard for...`, `[Eng] Implement...`)
2. **Overview** — One-to-two paragraph description of what needs to be built and why. Link to the source document if one was provided.
3. **Why This Matters** — 2-4 sentences connecting the work to business outcomes.
4. **High-Level Approach** — Brief technical or strategic approach outlining how the team should tackle this work. Include key architecture decisions, suggested implementation steps, or recommended tools/frameworks without being overly prescriptive.
5. **Acceptance Criteria** — Checklist of specific, testable conditions that define "done".

### Optional Sections (include when relevant)

- **Dependencies** — What must exist before this work can begin
- **Out of Scope** — Explicitly excluded items
- **Source Document Link** — URL to the Notion doc, metric sheet, or PRD this ticket derives from

## Acceptance Criteria Rules

- Write as a checklist using `- [ ]` markdown format
- Each criterion must be specific, measurable, and testable
- Bold the key deliverable or component name in each criterion
- Include non-functional criteria where relevant (performance, access control, data refresh cadence)
- Derive criteria directly from the source content provided
- Group related criteria logically (e.g., all metric-related items together, all UX items together)

## Source Document Handling

- Always link back to the source Notion doc or metric sheet in the Overview section when available
- Extract requirements from the source content rather than inventing them
- When the source has detailed specs (metrics, events, schemas), summarize in the ticket and reference the full doc
- Do not duplicate the entire source document into the ticket — keep it concise

## Writing Style

**Tone:**
- Clear and outcome-focused
- Active voice (not passive)
- Concise (2-sentence max paragraphs for most content)
- Use "we" not "I" in documentation
- Avoid jargon unless it's standard PM terminology

**Formatting:**
- Always use Oxford commas
- Use bullet points for lists (not numbered unless sequence matters)
- Bold key terms on first use
- Use markdown checklists (`- [ ]`) for acceptance criteria

## Immutable Rules

**ALWAYS:**
- Include an **Overview** section with a link to the source document when available
- Include a **Why This Matters** section connecting work to business outcomes
- Include a **High-Level Approach** section outlining the recommended implementation strategy
- Include **Acceptance Criteria** as a testable checklist
- Prefix the summary with the target team tag (e.g., `[Data]`, `[Eng]`)
- Create tickets as **drafts** first so the PM can review before sharing

**NEVER:**
- Skip the "Why This Matters" section
- Write vague acceptance criteria (e.g., "dashboard works well")
- Duplicate the entire source document into the ticket body
- Use passive voice in acceptance criteria
- Publish tickets directly without creating as draft first
- Invent requirements not present in the source content

## Example

See [examples/sample-ticket.md](examples/sample-ticket.md) for a reference example of a well-structured ticket.
