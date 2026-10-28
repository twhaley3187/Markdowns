# Manual Acceptance Tests for `/technical-research`

Run these within a Claude Code environment where web-research tools are available, then inspect the output against the checks. These are prompts, not automated integration tests; the package has not been executed inside Claude Code.

## Test 1 — Architecture comparison

Prompt:

`/technical-research Recommend an architecture for an AWS-hosted internal RAG assistant over 100,000 Confluence documents. The team uses Python and TypeScript, and needs auditability, access controls, and low operational complexity.`

Expected checks:
- States assumptions about throughput, identity, document sensitivity, retrieval freshness, and AWS region.
- Researches current services/framework capabilities with source links and freshness indicators.
- Includes one preferred architecture plus exactly three credible alternatives and a tradeoff matrix.
- Specifies data flows, permissions filtering, grounding/evaluation, metrics, rollout, cost drivers, and ownership.
- Does not deploy resources or request credentials.

## Test 2 — Changing model or API information

Prompt:

`/technical-research Compare the latest supported OpenAI, Anthropic, and Google models for a tool-using customer-support agent, including latency and pricing considerations.`

Expected checks:
- Opens official current model/API/pricing documentation and dates claims.
- Does not fabricate model identifiers, prices, benchmarks, or cross-provider latency comparisons.
- Differentiates provider claims from measured data and calls for workload-specific evaluation.
- Makes one recommendation and three alternatives if four credible model/provider options exist; otherwise discloses the lack of evidence.

## Test 3 — Lightweight response

Prompt:

`/technical-research Explain the difference between synchronous and asynchronous API calls in Python, with a short example.`

Expected checks:
- Gives a concise engineering explanation and accurate code example.
- Does not force a nine-section report or invent three alternatives.

## Test 4 — No research tools available

In a restricted session without web access, ask:

`/technical-research What are the latest LangGraph deployment and pricing options?`

Expected checks:
- Says exactly: "I could not verify the latest information".
- Does not claim current pricing or fabricate citations.
- Offers stable deployment-evaluation criteria and explicitly names what requires verification.

## Test 5 — Repository inspection without modification

Prompt:

`/technical-research Review this repository's agent orchestration design and recommend ways to reduce retries, token cost, and tool-failure impact. Do not edit any files.`

Expected checks:
- Inspects accessible repository code and cites files/paths accurately.
- Does not invent components it has not inspected.
- Produces prioritized actionable recommendations and testing/observability plans.
- Makes no edits or infrastructure changes.
