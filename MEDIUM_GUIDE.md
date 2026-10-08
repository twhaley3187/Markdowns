# Claude Code Engineering-Management System

This guide is formatted for clean copy/paste into Medium and uses only simple headings, bullets, numbered steps, blockquotes, and code blocks.

The system is designed for an IT Delivery Manager who uses GitHub, Jira, Confluence, Microsoft 365, and local files; prepares performance reviews and 1:1s; researches new technologies; writes light code; and builds agentic-AI proofs of concept.

> Research broadly. Interpret conservatively. Keep consequential judgment human-owned.

## 1. How the System Is Structured

```text
~/.claude/
├── CLAUDE.md
├── rules/
│   ├── coding.md
│   └── ai-engineering.md
├── agents/
│   ├── evidence-researcher.md
│   ├── skeptical-reviewer.md
│   └── technology-researcher.md
├── skills/
│   ├── performance-review/SKILL.md
│   ├── developer-contributions/SKILL.md
│   ├── one-on-one-prep/SKILL.md
│   ├── promotion-evidence/SKILL.md
│   ├── technology-research/SKILL.md
│   └── poc/SKILL.md
└── management-context/
    ├── README.md
    ├── organization.md
    ├── employee-identities.md
    ├── performance-framework.md
    ├── promotion-framework.md
    └── review-periods.md
```

### CLAUDE.md

Always-on operating principles. It defines your role, available systems, evidence standards, privacy boundaries, and autonomy limits.

### Rules

Conditional engineering guidance. `coding.md` shapes normal code work. `ai-engineering.md` adds LLM/agent considerations such as evaluations, security, RAG quality, observability, cost, and reliability.

### Skills

Repeatable workflows:

```text
/performance-review
/developer-contributions
/one-on-one-prep
/promotion-evidence
/technology-research
/poc
```

### Subagents

Specialized isolated workers:

```text
evidence-researcher
skeptical-reviewer
technology-researcher
```

### Management Context

Company-specific information that changes over time:

- OKRs
- team/repository ownership
- employee system identities
- review periods
- official performance framework
- official promotion framework

## 2. Performance-Review Workflow

```text
You
 ↓
/performance-review
 ↓
Main Claude
 ↓
Load employee + review period + framework + OKRs
 ↓
evidence-researcher
 ├─ GitHub
 ├─ Jira
 ├─ Confluence
 ├─ Microsoft 365
 └─ local files
 ↓
Evidence package
 ↓
Main Claude creates provisional synthesis
 ↓
skeptical-reviewer
 ↓
Main Claude corrects weak claims
 ↓
Manager-facing review brief
 ↓
Human manager judgment
```

The evidence researcher asks:

> What can the available systems actually establish?

The skeptical reviewer asks:

> What is weak, biased, overstated, or missing?

The main Claude session asks:

> What narrative is actually supported by the evidence and the official framework?

You make the final management judgment.

## 3. Install the Kit

For manual installation, open:

```text
COPY_PASTE_ALL_FILES.md
```

Every file is shown with its exact target path and complete contents.

For macOS or Linux, you can instead review and run:

```bash
chmod +x install.sh
./install.sh
```

The installer backs up any existing target file before replacing it.

## 4. Verify the Configuration

Start a fresh Claude Code session.

Run:

```text
/context
```

Then:

```text
/skills
```

Then:

```text
/agents
```

Then:

```text
/mcp
```

Finally:

```text
/doctor
```

Confirm the expected files, skills, agents, and integrations are visible.

## 5. Verify Read Access

Test each integration with harmless read requests.

Jira:

```text
Find one Jira issue assigned to me this month. Do not modify anything.
```

GitHub:

```text
Find one recent pull request I opened and summarize its title only. Do not modify anything.
```

Confluence:

```text
Find one Confluence page I edited recently. Do not modify it.
```

Microsoft 365:

```text
Find one recent professional document or message I authored. Do not send or modify anything.
```

## 6. Configure Permissions

Run:

```text
/permissions
```

Recommended posture:

```text
READ / SEARCH
Usually allow

WRITE / MODIFY
Ask or deny

SEND / PUBLISH
Ask or deny

DELETE
Deny or require explicit approval

MERGE / PUSH
Ask or deny

EMPLOYEE-RECORD CHANGES
Deny unless intentionally performing that task
```

Do not guess MCP tool names. Inspect the names exposed by your actual integrations first.

## 7. Fill In Management Context

### organization.md

Add:

- your product-family name
- all three teams
- Jira project keys
- GitHub repositories
- Confluence spaces
- important initiatives
- your authoritative OKR link

Replace:

```text
[OKR_URL_PLACEHOLDER]
```

with the real source.

### employee-identities.md

Copy:

```text
employee-identities.template.md
```

to:

```text
employee-identities.md
```

For each developer include only professional retrieval information:

```text
Name
Team
Role
Level
GitHub username
Jira identity
Microsoft 365 work identity
Relevant repositories
Relevant Jira projects
Role changes during the review period
```

This file is critical for preventing missed or incorrect attribution.

### performance-framework.md

Copy:

```text
performance-framework.template.md
```

to:

```text
performance-framework.md
```

Add your organization's official ratings, competencies, career levels, and review expectations.

### promotion-framework.md

Populate this only from official promotion criteria.

### review-periods.md

Add exact performance-cycle and mid-year/year-end dates.

## 8. Consider Disabling Auto Memory for Formal Review Work

For a dedicated review workspace, consider:

```json
{
  "autoMemoryEnabled": false
}
```

Prefer explicit historical sources such as prior reviews, documented goals, 1:1 notes, career plans, and official feedback.

## 9. Generate a Performance Review

Run:

```text
/performance-review Jane Smith 2025-11-01 2026-10-31
```

Or:

```text
/performance-review Jane Smith 2025-11-01 2026-10-31 focus on technical leadership, agentic AI engineering, collaboration, and growth
```

The workflow should:

1. Resolve the employee's professional identities.
2. Establish the exact period.
3. Load the official framework and relevant OKRs.
4. Delegate broad evidence research.
5. Correlate Jira, GitHub, Confluence, M365, and files.
6. Draft a provisional narrative.
7. Run the skeptical reviewer.
8. Correct weak or overstated conclusions.
9. Produce the final brief.

## 10. Inspect the Report

Before using it formally, inspect four areas.

### Source Coverage

Verify the systems and dates actually searched.

### Evidence

Open consequential source links and confirm major claims.

### Counter-Evidence

Make sure contradictory or complicating evidence was not ignored.

### Gaps and Unknowns

Turn important gaps into human questions.

## 11. Use the 1:1 to Fill Invisible Gaps

Run:

```text
/one-on-one-prep Jane Smith focus on review-period accomplishments and anything the systems may have missed
```

Use those questions to uncover mentoring, pairing, debugging, architecture discussions, cross-team work, incident support, unblocking, and other contributions that may not appear clearly in GitHub or Jira.

## 12. Promotion Evidence

Run:

```text
/promotion-evidence Jane Smith Senior Engineer 2025-11-01 2026-10-31
```

Expected classifications:

```text
DEMONSTRATED
PARTIAL EVIDENCE
INSUFFICIENT EVIDENCE
NOT OBSERVED
```

`NOT OBSERVED` does not automatically mean the employee failed to demonstrate the behavior. Opportunity and source visibility matter.

## 13. Lighter Contribution Research

Run:

```text
/developer-contributions Jane Smith 2026-01-01 2026-06-30
```

Use this for quarterly summaries, recognition, project research, and talking points without producing formal review language.

## 14. Directly Use the Evidence Researcher

```text
@evidence-researcher

Investigate Jane Smith's contribution to the Agent Routing redesign
from January through June 2026.

Focus on what Jane demonstrably implemented, designed, reviewed,
coordinated, or enabled.

Do not make a performance assessment.
```

## 15. Directly Use the Skeptical Reviewer

```text
@skeptical-reviewer

Review this draft assessment.

Identify anything overstated, unsupported, affected by visibility bias,
or incorrectly assigning sole credit for collaborative work.

[paste draft]
```

## 16. Technology Research

```text
/technology-research LangGraph vs AWS Bedrock AgentCore for an enterprise agentic chatbot platform
```

## 17. Build a PoC

```text
/poc Build a minimal multi-agent customer-service prototype using LangGraph and our existing API layer
```

The PoC workflow distinguishes:

```text
POC ACCEPTABLE
PRODUCTION BLOCKER
PRODUCTION IMPROVEMENT
```

## 18. Review Checklist

```text
[ ] Correct employee identity is configured
[ ] Review-period dates are correct
[ ] Current performance framework is available
[ ] Current OKR source is available
[ ] Relevant GitHub repositories are covered
[ ] Relevant Jira projects are covered
[ ] Relevant Confluence spaces are covered
[ ] Relevant Microsoft 365 artifacts are accessible
[ ] Auto-memory policy is appropriate
[ ] Write permissions are constrained
[ ] Evidence includes traceable references
[ ] Skeptical review occurs before final synthesis
[ ] Important claims are manually spot-checked
[ ] Significant unknowns become human questions
[ ] Final rating follows the organization's human process
```

## 19. What Not to Automate

Do not create:

```text
GitHub + Jira
     ↓
formula
     ↓
developer score
     ↓
rating
```

Do not automatically rank developers, score story points, score commits, score PRs, score lines of code, score review comments, infer ownership from ticket assignment, or infer low contribution from low repository visibility.

The goal is better evidence for managerial judgment, not automated developer measurement.

## 20. Shortest Repeatable Workflow

```text
1. Update management context if necessary.
2. Run /performance-review <employee> <start-date> <end-date>.
3. Check source coverage.
4. Verify the strongest evidence.
5. Use 1:1 questions to fill important gaps.
6. Give verified context back to Claude.
7. Revise the synthesis.
8. Apply your organization's human calibration and rating process.
```
