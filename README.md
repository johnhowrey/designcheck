# Design Check

Does your UI read as AI-generated? Ask before you ship it.

**Live:** https://designcheck.allthepossibles.com (docs: `/docs`, machine-readable: `/llms.txt`)
**Built by:** [All the Possibles](https://allthepossibles.com)

## What it does

Design Check scans a page's HTML, CSS, and copy for the specific patterns that
make AI-generated UI read as generic — not just individual tropes (a gradient
here, a pill button there), but the composition itself. A page can avoid every
named cliché and still look templated if the whole layout is one unvarying
centered column with a flat background the entire way down. That's the check
most tools miss, because it isn't about any single element.

Checks: default font stacks with nothing distinctive alongside them, soft tech
gradients, pill-shaped CTAs paired with arrow icons, eyebrow labels sitting
directly above headlines, uniform card grids, composition that never varies
width or background across sections, and copy tells — AI-cliché vocabulary,
negative-parallel framing ("It's not X, it's Y"), hedge words, heavy em-dash
use.

A fifth check — vision-based critique of a rendered screenshot, powered by
Claude, catching gestalt issues text analysis alone can't — is built and
tested but currently gated off while we get billing in front of it.

This page's own score, run live through the same engine on every load, is
shown at the top of [the live site](https://designcheck.allthepossibles.com).
Not a claim. A number.

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
