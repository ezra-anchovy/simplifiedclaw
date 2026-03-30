# SimplifiedClaw — Redesign Notes

## What's Wrong (and Why It Matters)

- **The site is documentation, not a sales page.** NVIDIA RPM limits, Cerebras daily caps, model routing chains, tier fallback rules — this is an internal runbook, not a product. A CTO lands here and sees a wall of jargon that either terrifies them or convinces them they should just build this themselves. Neither outcome leads to a sale.

- **The brand name in the header is wrong.** "OpenClaw v4.1" with a lobster emoji is the open-source project identity, not SimplifiedClaw. Clients aren't buying the open-source project — they're buying the white-glove service built on top of it. Exposing the underlying technology undermines the premium positioning and gives sophisticated buyers a reason to DIY.

- **There is no value proposition.** Nowhere on the page does it say what this actually *does for a business*. "Intelligent Model Routing for Mission-Critical AI" is a features statement, not a benefits statement. The buyer doesn't want a model router — they want to stop doing things manually and have an AI assistant that actually works.

- **The pricing is invisible.** There's no pricing section at all. The existing stats ("24 Models Orchestrated, 7 Providers Unified") are engineering flex, not customer value. Buyers need to know what they're paying and what they're getting. Hiding price at this tier just creates friction.

- **The copy is engineer-to-engineer, not founder-to-founder.** "Capability-Aware Dispatch," "Tri-Model Routing Cascade," "TMRC" — none of this means anything to the people writing the check. The buyer is a founder or CTO who wants to know if their AI assistant can draft the board memo and pull the Salesforce pipeline. That's the conversation this page should be having.

- **The site shows the sausage being made.** Displaying specific model names, "DEGRADED" status badges, provider failover rules, and hard-stop error cases is the opposite of confidence. Premium services hide complexity. The client should see outcomes, not internals.

- **There is no call to action.** No pricing. No "book a call." No path forward. The page has a nav item called "Contact" that leads to... the footer, which shows the last-verified timestamp of an internal document. A prospect reading this has no idea how to become a client.

## What to Change

- Lead with the outcome: an AI assistant, running in your Slack, configured for your workflows, installed in a day
- Show three pricing tiers with clear deliverables per tier
- Remove all model names, provider names, rate limits, and routing logic from the public page
- Replace the "OpenClaw" brand with "SimplifiedClaw" throughout
- Add a clear primary CTA (Book a call → Calendly)
- Write copy that sounds like a smart person explaining this over coffee, not a deployment doc
