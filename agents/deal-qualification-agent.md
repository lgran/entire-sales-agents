# Deal Qualification Agent — Entire.io Sales Flows

## Purpose
Gate deals from "in conversation" to "working opportunity" using the real PICS chart
methodology, the Discovery Call Checklist's exact completion criteria, and a Dragon vs
Clown status classifier. Runs as a checkpoint before every pipeline stage advance.

## Inputs
- CRM opportunity record (stage, notes, next steps, contact role)
- Discovery call transcript or notes
- Entire ICP fit signals (see ICP & Signal Scout agent output)

## PICS Chart — 5-Level Pain Architecture (source: 01-PICS chart.pdf)
The agent builds and maintains a live PICS chart per target segment (not per deal — this
is reviewed daily/pre-call per the source material) with five layers:

1. **Level 1 — Technical Pain**: the literal problem Entire's checkpoint/session/rewind
   model fixes. For Entire's ICP: agent-session context loss, no audit trail on
   AI-written code, redundant repo cloning at scale, fragmented multi-tool workflows.
2. **Level 2 — Business Impact**: what Level 1 pain does to the org — slower ship velocity,
   more rework/QA cycles, compliance exposure on unreviewable AI-generated commits,
   engineering morale/attrition from redoing lost agent work.
3. **Level 3 — Personal/Emotional Impact on the DM**: the VP Eng or Platform Lead is
   usually 3-9 months into role, under pressure to prove the agent-coding bet was right,
   feeling exposed if a compliance or reliability incident traces back to unreviewable
   agent output on their watch.
4. **Potential Causes**: using single-tool agent setups with no session persistence,
   no git-native checkpointing, ad hoc Slack/doc tracking of agent decisions instead of
   commit-linked context.
5. **Potential Solutions competing for this budget**: build in-house tooling, do nothing
   and accept the risk, switch coding-agent vendors entirely, or adopt a session/context
   layer like Entire.

Agent generates and refreshes this chart per vertical/segment weekly, and every call brief
(see Call Prep Agent) pulls the relevant Level 1-3 chain before the call.

## Scoring Rubric (derived from PICS + Discovery Checklist Q&A)
Each dimension scored 0-3 based on what discovery notes actually captured:
- **Pain identified & quantified** (Level 1 tied to a cost/time figure — never advance
  past Discovery un-quantified, per source: "continue probing until you get a price tag")
- **Impact mapped** (Level 2 business impact articulated, not just the technical symptom)
- **Personal stake confirmed** (Level 3 — does the DM have skin in the game on this fix)
- **Solution fit** (does Entire actually displace their current setup, per ICP Scout's
  competitor overlay, or is this a feature-tourist eval with no real trigger)

Total <6 = stays in Discovery. 6-9 = Qualified, needs exec sponsor confirmed. 10-12 =
Committed, move to proposal.

## Discovery Call Checklist Completion Gate (source: 02-Discovery Call Checklist.pdf)
Deal cannot move out of "Discovery" until every box below is checked in CRM — this is
the literal checklist structure, not a paraphrase:

Pre-call prep:
- [ ] PICS chart reviewed for this segment before the call
- [ ] Call objective defined
- [ ] Assumed tech stack mapped (which coding agent(s) they likely run)
- [ ] Assumed social dynamics of the DM in their org
- [ ] Recent news/funding events checked
- [ ] Cold read prepared (headcount, funding stage, tenure of DM, likely pressure point)

Intro / Bridge:
- [ ] Sounded powerful, mirrored the prospect, used positive associations, prospect engaged
- [ ] Bridge delivered clearly and confidently, prospect agreed to proceed

Q&A (hard gates):
- [ ] Pain identified
- [ ] Cost of pain quantified
- [ ] Other business/personal impacts surfaced
- [ ] Confirmed prospect hasn't given up on fixing it (active urgency)
- [ ] Affordability sanity-checked
- [ ] Full buying committee identified beyond the DM

Recap:
- [ ] AE controlled the frame for the majority of the call
- [ ] Prospect left feeling emotional about their pain, not just informed
- [ ] Prospect EARNED next steps — the agent flags any deal where a demo was booked
  without the pain-quantification gate above being satisfied first (this is a violation
  of the core sequencing rule: never present the solution before the pain has a price tag)

## Status / Power-Dynamics Check (Dragon vs Clown classifier)
Applies the Dragons-vs-Clowns pattern library to flag deals where the AE (or the
Entire.io buyer relationship generally) is in a structurally weak frame:
- Flag "we need to think about it" logged without a direct challenge follow-up
  ("is it over?" / "can you tell me what that means to you specifically?") — this phrase
  is treated as a likely soft no, not a real next step, until clarified.
- Flag any call where the AE showed the product before pain was quantified — hard
  violation, auto-downgrades deal score by one tier.
- Flag single-thread deals (only one contact, no named buying committee) after 2+ touches
  — force disposition to Nurture or Closed-Lost rather than let it sit in "Qualified."
- Reward signal: prospect proactively self-diagnoses their problem or proposes their own
  next step (a "sell themselves" moment) — fast-track stage advance.
- Reward signal: AE held a genuine walk-away line (e.g., named a real dealbreaker and let
  the prospect react) rather than negotiating against themselves — treated as a
  high-integrity, high-conversion behavior pattern worth reinforcing in coaching notes.

## Entire ICP Gate (applied jointly with scoring above)
Deal must match Entire's actual ICP before PICS scoring even starts:
- Funded engineering org (seed+ or enterprise) actively running multi-agent coding
  workflows (Claude Code, Codex, Cursor, Devin, or similar) in production or eval.
- Evidence of pain around agent session loss, context fragmentation across tools, or
  reviewability/audit gaps in AI-generated code.
- Git-native workflow already in place.

## Output
Structured JSON checkpoint written back to CRM + Entire repo (`flows/deals/<deal-id>.md`):
PICS level breakdown, checklist completion %, status/frame flags, and a one-line "why"
explanation — mirroring Entire's own `entire explain` philosophy so every qualification
decision is traceable to a specific captured input, not a vibe.
