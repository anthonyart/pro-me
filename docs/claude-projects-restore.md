---
layout: default
title: Claude projects hidden after resubscribing (fix observed)
description: After resubscribing to Claude Pro, only 5 projects showed. Search for a hidden project, close search, and the full list returned.
---

# Claude projects hidden after resubscribing (fix observed)

- **Verified:** 2026-10-23
- **Environment:** Claude iOS app
- **Scenario:** Pro plan lapsed, then resubscribed to Pro
- **Status:** single observation (n=1), not official Anthropic guidance

## Symptom

After resubscribing, the Projects list showed only 5 projects (the free-plan cap).
The rest were hidden, not deleted.

## Steps that restored them

1. Open **Projects**.
2. Tap **Search** and type the name of a hidden project.
3. The hidden project appears in results.
4. Close search (X).
5. The full project list now loads.

## Evidence

Timeline from the screenshots (same device, same session):

| Time | Screenshot | What it shows |
|------|-----------|---------------|
| 4:58 | 1 | Plan was Free before upgrading |
| 5:05 | 2 | Search for "sol" returns a project missing from the list |
| 5:05 | 3 | After closing search, the full list is back |

Not captured: the 5-project symptom screen right after upgrading (reported by the author, no screenshot).
Some project names are redacted with solid black boxes for privacy.

![Claude iOS Settings screen at 4:58. The account card reads "Personal" with the email redacted and the plan label "Free". Below it is a card titled "Get more Claude" with an Upgrade button, then Account rows: Profile, Billing, Notifications, Time & focus, Privacy, Shared links.](img/01-settings-plan-free.jpg)

![Claude iOS Projects screen at 5:05 with the search field containing "sol" (circled in green). Two results are listed: "sol", circled in green, described as "As a website designer a…", 6 months ago, and "qaw", described as "Testing websites for bu…", 6 months ago.](img/02-search-hit.jpg)

![Claude iOS Projects screen at 5:05 after closing search; the search field is empty. A long list of projects is shown, including tja, fab, loc, sol (circled in green), cam and qaw. Several project names and descriptions are covered with black boxes. Far more than 5 projects are visible.](img/03-list-restored.jpg)

## Hypothesis (~60% confidence)

Search forces a refetch of the full project list. The initial list was likely stale
from the free-tier state. This points to a client-side display bug, not data loss.

## Not tried

- Claude web vs. app
- Force-quitting the app
- Waiting for the list to refresh on its own

## Context

- Anthropic lists the free plan cap as 5 projects; Pro is reported as unlimited.
- A Reddit user (Jul 2026) reported projects vanishing on downgrade and returning on resubscribe.
- Official docs do not describe this behavior. If the fix fails, contact Anthropic support.

## Changelog

- 2026-10-23: first observation.
- 2026-10-23: header lines converted to a bullet list so they render on separate lines.
