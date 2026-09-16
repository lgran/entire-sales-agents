# Call Prep Agent — Entire.io Sales Flows

## Purpose
Generates a pre-call brief combining the Cold Call Script structure, the PICS chart's
pain hierarchy, Status Hacks tactics, and the Reframe-of-the-Day / Dragons-vs-Clowns
objection library — all sourced verbatim from the Chad Salesman system rather than
generic reconstructions.

## Inputs
- Prospect name, title, company, prior touch history
- Entire ICP + competitor-overlay tag from ICP Scout (which coding agent they likely run)
- Call type: cold dial, warm follow-up, discovery, or demo

## Brief Structure Generated

### 1. Cold Read + Pre-Call Prep (source: Discovery Call Checklist)
Agent auto-drafts the "cold read" paragraph the checklist calls for, e.g.: "[Company] has
40 engineers, raised a $22M Series A eight months ago with a mandate to ship faster using
AI agents, currently job-posts reference Cursor and Claude Code, no evidence of a shared
session/context layer. VP Eng joined 5 months ago — likely under pressure to show the
agent-coding bet is working."

### 2. Intro + Bridge (source: Cold Call Script, verbatim structure)
- Intro: confirm name, pause, state name plainly ("John, this is [rep name]").
- Bridge: direct permission-based opener — "I'm going to be upfront, this is a cold call.
  Do you want to hang up or should I tell you why I'm calling?" Agent fills in
  [problem 1/2/3] using the PICS Level 1 pains for that prospect's likely tool (e.g., for
  a Cursor-shop: context loss between sessions, no audit trail on agent-written code,
  redundant re-cloning on large monorepos).
- Branch handling: if prospect says no interest, follow the exact script's move-on rule
  (NEXT — don't chase). If yes, proceed to the "I mostly work with [title]s like yourself
  who struggle with X/Y/Z" frame before asking permission to continue.

### 3. Discovery Question Bank (PICS + Discovery Checklist Q&A combined)
- "Can you give me a high-level overview of how your team manages agent sessions today?"
- "If you could wave a magic wand and fix 1-2 problems with your current agent workflow,
  what would they be?"
- "How long has that been a problem, and has the team tried to fix it already?"
- "How much would you estimate that's costing you — in rework, incidents, or time?"
- "Besides you, who else would need to be involved in a decision like this?"

### 4. Status Hacks to Deploy (source: 06-9 Status Hacks.pdf, verbatim tactics)
Brief selects 2-3 relevant hacks per call type:
- **Time Constraint** (Hack #1): open with a genuine or implied hard stop to frame the
  AE as time-conscious, not the prospect.
- **Rephrase to Reframe** (Hack #3): swap weak framing ("we help companies with X") for
  status framing ("VPs of Engineering seek us out because losing agent context mid-task
  is costing them real rework hours").
- **Saying Less Is More** (Hack #7): brief reminds AE to pause 2-3 seconds after the
  prospect speaks instead of filling silence.
- **Only a King Can Judge** (Hack #8): respond to prospect wins with a brief "atta boy"
  register, not over-eager flattery.
- **Reciprocity Sometimes** (Hack #9): acknowledge niceties without escalating them
  ("good to connect" not "great to meet you too!").

### 5. Objection → Reframe Map (source: Reframe of the Day + Dragons vs Clowns, verbatim)
| Objection | Clown response (avoid) | Dragon reframe (use) |
|---|---|---|
| "We already use [Cursor/Copilot/Devin]" | "How's your experience with them going?" | "...for now." Then: "What's got you evaluating alternatives?" |
| "We need to think about it" | "Take all the time you need" | "I'll be upfront — in my experience, 'think it over' usually means no. Is that the case here?" |
| "Send me some info" | Sends the deck | Declines the info-dump; proposes a specific time instead |
| "You're too expensive" | Justifies the price | "Compared to what? Not solving this is 100x more expensive." Or: "Ha, I've been told we don't charge enough." |
| "Your competitor is half the price" | "We have a better product" | "Yeah, I remember when they changed pricing. All I'll say is they're not half the price out of generosity." |
| "What do we get if we sign today" (feature fishing) | Lists every included perk | "Only if you want it — not necessary" (removes leverage from the ask) |
| Prospect goes dark after agreement sent | Internalizes it as personal failure | Logged neutrally: "Getting rugged is part of the game — on to the next" |
| Multiple objections at once | Tries to answer all of them | Isolate one: "Out of all the concerns you listed, maybe one is actually valid — which one?" |

### 6. Tone / Frame Guardrail (Clowns vs Chads word-choice linter)
Before the brief is finalized, agent scans any AE-drafted talk track and flags:
- Supplicating words ("Perfect," "Amazing," "Fantastic," "Sorry to bother") — replace with
  neutral status language ("Cool," "Alright," "Sounds good").
- "Does that make sense?" (implies talking down) — replace with "You with me so far?"
- Leading with product before pain is quantified — hard block per PICS sequencing rule.
- Over-apologizing for being a cold call — replace with the direct Bridge script language.

### 7. Scheduling Move
If the call reaches booking stage: propose a specific time, let the prospect counter once,
"reject" that counter citing being busy, then land on a final time — logged explicitly as
a deliberate status move (Cold Call Script "Next Steps" tactic), not an actual conflict.

## Output
A single-page markdown brief per call, stored in `flows/calls/<prospect>-<date>.md`,
checkpointed so outcomes can be reviewed against the brief afterward and the objection map
refined over time.
