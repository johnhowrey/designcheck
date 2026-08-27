# Design Check

Does your UI read as AI-generated? Ask before you ship it.

**Live:** https://designcheck.allthepossibles.com (docs: `/docs`, machine-readable: `/llms.txt`)
**Built by:** [All the Possibles](https://allthepossibles.com)

## What it does

Design Check scans a page's HTML, CSS, copy, and interaction patterns for what
makes AI-generated work read as generic. Individual visual tropes matter, a
gradient here, a pill button there, but composition matters more: a page can
avoid every named cliché and still look templated if the whole layout is one
unvarying centered column with a flat background the entire way down. That's
the check most tools miss, because it isn't about any single element.

Design here isn't only visual. A tool that names a problem and stops there —
tells you what's wrong with no path forward — has an experience-design
failure, whatever it looks like. Every finding Design Check returns includes
a concrete fix alongside the diagnosis, not just a description of what's
wrong.

Checks span four categories: typography and color (default fonts, soft tech
gradients), components and layout (pill+arrow CTAs, eyebrow labels, uniform
card grids, composition that never varies width or background), copy
(AI-cliché vocabulary, negative-parallel framing, hedge words, heavy em-dash
use), and experience (a diagnosis with no next step, dead-end links).

A fifth check, vision-based critique of a rendered screenshot powered by
Claude and catching gestalt issues text analysis alone can't, is built and
tested but currently gated off while we get billing in front of it.

This page's own score, run live through the same engine on every load, is
shown at the top of [the live site](https://designcheck.allthepossibles.com).

## Using it

**As an MCP server:**

```json
{
  "mcpServers": {
    "designcheck": { "url": "https://designcheck.allthepossibles.com/mcp" }
  }
}
```

Then call `check_design` before presenting UI to a human.

**Or the REST API directly:**

```
curl -X POST https://designcheck.allthepossibles.com/api/check \
  -H "content-type: application/json" \
  -d '{"url": "https://example.com"}'
```

Full API reference: https://designcheck.allthepossibles.com/docs

## Free during preview

20 checks/minute per caller IP, no signup, no API key.

## Reporting a false positive or false negative

Most useful thing you can do right now. Open an issue with the URL or HTML
snippet that got it wrong and what you expected instead.

## Why the source isn't here

Same reasoning as Preflight, our sibling product: publishing the exact
detection patterns makes it easier to write copy or CSS specifically designed
to slip past them. What's public is this documentation, the methodology, and
this repo for issues.

## Support

Open an issue in this repo.
