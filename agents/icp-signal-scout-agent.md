# ICP & Signal Scout (with Competitor Overlay + Pipeline-Find Enhancement)

## Purpose
Scores inbound/outbound target accounts against Entire's real ICP, flags which competitor
tool they are most likely running today, and actively surfaces net-new pipeline candidates
using public signal sources — feeding directly into the PICS chart (Deal Qualification
Agent) and cold-read prep (Call Prep Agent).

## Entire ICP Definition
- Funded engineering organization (seed through enterprise) with an active multi-agent
  coding workflow in production or evaluation.
- Git-native, GitHub/GitLab-centric engineering culture.
- Evidence of scale pain: large monorepos, multiple concurrent agent sessions, or
  compliance/audit requirements on AI-generated code.
- Buying committee typically includes a VP/Head of Engineering or Platform lead plus a
  security/compliance stakeholder for regulated buyers.

## Competitor Overlay — Current Market Map (Sept 2026)
| Tool | Pricing signal | Where they win | Displacement angle for Entire |
|---|---|---|---|
| GitHub Copilot | Business $19/user/mo, Enterprise ~$39/user/mo; 56% adoption at 10,000+ employee orgs | Deep GitHub/enterprise contract lock-in, IDE-embedded autocomplete | Lead with session/context loss across tools — Copilot has no cross-agent checkpoint layer |
| Cursor | Pro $20/mo, Ultra $200/mo, Team $40/user/mo | Fastest multi-file refactor UX, strong with startups and individual devs | Lead with team-scale reviewability — Cursor sessions aren't git-native or shareable as commits |
| Claude Code | ~$20-200/mo tiers, API-based billing; 41-54% of enterprise coding-agent share, $2.5B ARR in under 9 months | Terminal-first agentic power users, highest revenue-per-user of any tool | Lead with multi-agent handoff — sessions don't unify across tools via a shared semantic graph |
| Devin / Devin Desktop (formerly Windsurf, rebranded Sept 2026) | Core $20/mo pay-as-you-go ACUs, Team $500/mo (250 ACUs), Enterprise custom w/ VPC + SAML SSO | Fully autonomous task execution, enterprise security posture | Lead with explainability — ACU-billed autonomous runs are opaque; Entire's explain/rewind gives auditability they don't message on |

> Note: Windsurf no longer exists as a standalone brand as of September 2026 — rebranded
> to Devin Desktop. Treat any account still referencing "Windsurf" in job posts as a
> stale-data signal; verify current tooling via recent job reqs or eng blog before
> assuming a displacement target.

## Signal Sources for Scoring
- Job postings mentioning specific agent tools in eng job descriptions — direct
  tool-in-use signal.
- Engineering blog posts or conference talks referencing agent workflows or
  context/session pain points.
- GitHub org activity: AI-attributed commits, bot accounts in commit history, or CI
  config/README references to agent tooling.
- Recent funding events (seed through Series C) — budget trigger, fresh tooling decisions.

## PICS-Informed Scoring Layer
Rather than scoring accounts on fit alone, each candidate is tagged with a hypothesized
PICS Level 1-3 chain (per Deal Qualification Agent's chart) before it ever reaches a rep:
predicted technical pain, predicted business impact, and predicted personal stake of the
likely DM (tenure signal from LinkedIn: a DM 3-9 months into role scores higher urgency,
per the Discovery Checklist's "cold read" logic).

## Pipeline-Find Enhancement
Beyond scoring a static list, this agent actively generates net-new candidates:
1. Run code/repo search across public GitHub for repos with CI configs or READMEs
   referencing Cursor/Copilot/Claude Code/Devin at scale (monorepo size as proxy for
   team size).
2. Cross-reference against recent funding databases — prioritize orgs that raised in the
   last 2 quarters (fresh budget, still forming vendor preferences).
3. De-duplicate against existing CRM accounts; only surface accounts not already in an
   open or recently-closed opportunity.
4. Auto-tag each new candidate with: ICP fit score (0-100), likely current tool,
   hypothesized PICS chain, and a one-line displacement angle from the Competitor
   Overlay table.
5. Feed top-scored candidates directly into the Call Prep Agent's queue so a lead never
   sits un-actioned between discovery and first outreach.

## Output
`flows/pipeline/candidates.csv` — ranked list with ICP score, likely current tool,
hypothesized pain chain, displacement angle, and signal source, refreshed on a scheduled
checkpoint (weekly) so the pipeline list is a living, versioned artifact.
