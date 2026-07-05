# Transferware Finds

Static GitHub Pages site for San Fermo / Swan House Farm's weekly transferware sweep.
Vintage tableware finds from eBay, regenerated each week and shared with Tim & Kelly.

**Live page:** https://samfermo.github.io/transferware/

## How it works

The `transferware-sweep` skill runs weekly (10am Sunday). Each run scrapes the eBay
saved searches, filters the keepers, regenerates `index.html` in this directory, and
deploys via `deploy-to-github.command`. There is no build step and no artifact — the
page is a single self-contained `index.html` that a normal browser renders with the
eBay-hosted photos loading directly (the whole reason this moved off the Cowork
artifact, whose sandbox blocked remote images).

## Files

- `index.html` — the finds page (regenerated every run; the only content file)
- `deploy-to-github.command` — single-commit Git Data API deploy (one commit = one
  Pages run = quiet failure emails). Double-click, or run via osascript.
- `save-token.command` — one-time: saves the GitHub PAT from the clipboard to
  `~/.starfleet/transferware-token`.
- `.nojekyll` — tells Pages to skip Jekyll processing.
- `robots.txt` — keeps the page out of search engines.

## Token

The deploy reads a fine-grained PAT from `~/.starfleet/transferware-token`
(Contents: Read/Write on `SamFermo/transferware`). The token stays in that file;
the script reads it. To (re)save it: copy the token, double-click `save-token.command`.

## Image URLs

Photos use eBay's `s-l500` resolution suffix. Do **not** upgrade to `s-l800` — it
can 404 on some listings.
