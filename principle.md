# The Take It With You principle

Every external-facing artifact ships with an affordance for the AI co-pilot reading alongside the human: a one-click way to grab a clean Markdown copy of the content.

Treat the LLM as a second reader, not a side effect.

## The pattern

> **TAKE IT WITH YOU — Copy for LLM | Download MD**

Adapted from David Arnoux.

## Why

A prospect reading your proposal, a learner reading a lesson, an audience member after a talk — they will continue the conversation in ChatGPT or Claude. If your content isn't easy to paste in, you lose that conversation.

The cost of shipping the affordance is ~3 KB and ten minutes. The cost of not shipping it is a worse downstream conversation about your work, in someone else's session, where you can't intervene.

## When to apply

Gate by two questions:

1. Is the reader **external** (prospect, client, learner, partner, audience)?
2. Would they **plausibly debate, summarize, or extend** the content with an LLM after reading?

If both are yes, ship the affordance. If either is no, skip it.

### Apply

- Proposals (DOCX and landing pages)
- Marketing site pages aimed at prospects
- Product framing, onboarding and docs pages
- Course and lesson pages
- Slide decks shared after a session (HTML / Remotion)
- Client-facing explainers and reports

### Skip

- Internal-style spec references (brand hubs, design systems)
- Your own private knowledge base
- Internal dashboards and ops tools
- Automation scripts, cron jobs, internal docs
- Pages where the audience isn't going to feed your content into an LLM

## Per-surface guidance

### Web pages (any stack)

Drop the snippet near the bottom of the main content, after the reading flow, before the global site footer. Generate the Markdown at click time from visible page content, not at build time. Keeps it simple.

### Slide decks (HTML / Remotion)

Add the affordance to the deck shell. Markdown content = slide titles + body text + speaker notes, in order.

### DOCX / PDF proposals

DOCX can't host live buttons. Two options, in order of preference:

1. **`.md` sibling**: every generated proposal emits a `.md` next to the `.docx` in the same folder. The cover email references it ("also available as markdown, easy to discuss with your AI").
2. **Short URL on the cover**: a per-proposal landing page hosting both buttons. Build only when (1) isn't enough.

## What goes in the Markdown export

- Title and date
- Author (if configured)
- Body content as rendered, in reading order
- For proposals: scope, deliverables, investment, planning, contact
- Skip: navigation, footers, decorative copy, signature blocks
- End with a one-line provenance footer: `Source: <canonical URL>`

## A note on attribution

The point of the pattern isn't credit, it's behavior. Ship it without our name on it. If you want to nod to the source, that's nice. If you don't, that's also fine — what matters is the LLM-reader gets a clean copy.

---

Source: principle distilled from the [Mission Relearn](https://missionrelearn.com) Second Brain. Pattern inspired by David Arnoux.
