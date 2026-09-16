# entire-sales-agents

Three hyper-tuned agent specs for building sales flows on the Entire platform
(Founding AE interview project).

Entire (founded by former GitHub CEO Thomas Dohmke, $60M seed) is a git-native developer
platform for AI coding agents — code hosting, session/checkpoint capture, agentic search,
and a semantic graph unifying code with its reasoning history. This repo treats sales-flow
logic the same way Entire treats code: every agent decision is versioned, checkpointed, and
explainable (`entire explain` / `entire rewind`), not a black-box automation.

## Agents

1. **[Deal Qualification Agent](agents/deal-qualification-agent.md)** — the real PICS
   5-level pain chart, the literal Discovery Call Checklist as a stage-advance gate, and a
   Dragon-vs-Clown status/frame classifier, applied against Entire's ICP.
2. **[Call Prep Agent](agents/call-prep-agent.md)** — call briefs built from the verbatim
   Cold Call Script, PICS pain hierarchy, all 9 Status Hacks, and the Reframe-of-the-Day /
   Dragons-vs-Clowns objection library.
3. **[ICP & Signal Scout](agents/icp-signal-scout-agent.md)** — scores accounts against
   Entire's ICP, flags likely current tool (Cursor, GitHub Copilot, Claude Code, Devin /
   Devin Desktop) with live Sept-2026 pricing data, and actively mines net-new pipeline
   rather than only scoring a static list.

## Source material
Built on the Chad Salesman sales-psychology system (PICS chart, Discovery Call Checklist,
Cold Call Script, Cold Email Sequence, 9 Status Hacks, Reframe of the Day, Dragons vs
Clowns, Chad Maxims) plus live competitor market data pulled September 2026. All tactical
content is sourced verbatim from the original framework, not paraphrased reconstructions.

## Why this maps to Entire's actual product
Each agent produces a checkpointed markdown/JSON artifact under `flows/`, mirroring how
Entire stores agent sessions alongside commits. An AE (or the agent itself) can run
`entire explain` on any qualification decision, call brief, or pipeline candidate and get
a traceable answer grounded in a specific chart, checklist item, or reframe pattern —
not a mystery score.

Last verified: September 15, 2026

