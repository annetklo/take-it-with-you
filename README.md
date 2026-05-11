# Take It With You

A drop-in web snippet that adds a **Copy for LLM** and **Download MD** button to any page, so readers can take your content into their AI assistant in one click.

Vanilla HTML/CSS/JS. No dependencies. No build step. ~3 KB.

```
TAKE IT WITH YOU   [ ⧉ Copy for LLM ]   [ ↓ Download MD ]
```

## Why this exists

People don't just *read* anymore. They paste into ChatGPT or Claude and ask "summarize this", "what's the counter-argument", "rewrite for my team".

If your page is a wall of HTML with navigation, ads, and cookie banners, that paste-in is messy and the conversation goes sideways. So you ship the clean Markdown yourself.

The pattern is adapted from a talk by [David Arnoux](https://www.linkedin.com/in/davidarnoux/) on designing for the LLM as second reader.

## When to use it

Gate by two questions:

1. Is the reader **external** (prospect, learner, audience, partner)?
2. Would they **plausibly debate, summarize, or extend** the content with an LLM after reading?

If both are yes, ship it. If either is no, skip it. Internal docs, design system specs, decorative pages — not the target.

See [principle.md](principle.md) for the full reasoning and where it applies in our own stack (proposals, slide decks, course pages).

## Install

Copy [snippet/take-it-with-you.html](snippet/take-it-with-you.html) into your page, near the bottom of the main content (after the reading flow, before the global site footer). That's the whole install.

```html
<!-- somewhere near the end of <main> -->
<div class="tiwy" data-source="main"></div>
<!-- ... include the full snippet block (HTML + style + script) ... -->
```

By default it serializes everything inside `<main>`. Override with `data-source="<css-selector>"`.

### Configuration

| Attribute | Default | Purpose |
| --- | --- | --- |
| `data-source` | `"main"` | Root element to serialize to Markdown |
| `data-title` | `<h1>` text or `<title>` | Override the document title |
| `data-filename` | slugified title | Override the `.md` filename |

Skip individual elements by adding `data-tiwy-skip` to them.

### Branding

Default styling is neutral (system fonts, neutral grays). Override with CSS variables:

```css
.tiwy {
  --tiwy-accent: #F36E59;        /* hover color */
  --tiwy-text: #231F20;          /* body text */
  --tiwy-muted: #6A7280;         /* label + status */
  --tiwy-border: rgba(0,0,0,.12);
  --tiwy-bg: #ffffff;
  --tiwy-font: "Open Sans", system-ui, sans-serif;
  --tiwy-label-font: "Cal Sans", "Open Sans", sans-serif;
}
```

## Demo

Open [examples/demo.html](examples/demo.html) in your browser to see the snippet in action on a sample article.

## What's in the exported Markdown

- Title + date + author line (if configured)
- Body content as rendered, in reading order — headings, paragraphs, lists, blockquotes, code blocks, links, images, tables
- Skipped: nav, scripts, styles, anything with `data-tiwy-skip`, the snippet itself
- Provenance footer: `Source: <canonical URL>`

## License

MIT. Use it anywhere. Attribution appreciated but not required.

## Credit

Built by [Annet Kloprogge](https://missionrelearn.com) at [Mission Relearn](https://missionrelearn.com).
Pattern inspired by David Arnoux.

Part of an ongoing open-source release of skills, prompts and rules from our internal Claude Code setup. Build log at [missionrelearn.com](https://missionrelearn.com).
