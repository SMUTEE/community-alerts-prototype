# Community Alerts — hi-fi prototype

A clickable prototype for **Community Alerts**, a location-aware platform for
reporting and verifying things happening in your immediate area — a blocked
road, an outage, an incident at the estate gate.

**[Open the prototype →](https://community-alerts-prototype.vercel.app)**

## What's here

| Route | What it is |
| --- | --- |
| `/` | The prototype. 13 screens, clickable, with the experience audit beside each one. |
| `/directions` | The three visual directions explored for the home screen, before Direction B was picked. |

Nothing is wired to a backend. Confirmations, toggles and the reporting flow
all mutate in-memory state so the flows can be walked end to end.

## Walking it

Use the index on the left, the Previous / Next buttons, or the arrow keys. Inside
the phone, the tab bar, alert cards, map pins and the report flow are all live.

Worth trying:

- **Home → the security alert.** It is severe in colour but unverified in status,
  and says outright that it has not been sent to anyone. Confirm it and watch the
  trust state and the held-from-notifications warning both change.
- **Home → flooding.** An hour old, so it asks *is this still happening?* rather
  than *did this happen?* — two different questions that the PRD conflated.
- **Report (+) → any category → Adjust.** The audience is a consequence of the
  category, not a control the reporter has to reason about.
- **Notifications.** The critical tier has no toggle. That is the point.

## Design

- Type is [Satoshi](https://www.fontshare.com/fonts/satoshi) (variable, subset to
  Latin and served as a 23 KB WOFF2) with Inter for labels, distances and timestamps.
- UI research was done with Mobbin; the closest analogues are Citizen, Waze,
  Apple Maps and Apple Weather. Per-screen references are in the audit notes.
- The audit is attached to each screen, tagged **Changed / Kept / Risk / Reference**,
  with section numbers referring to the product requirements document.

## Running locally

No build step and no dependencies — it is one HTML file plus a font.

```
python3 -m http.server 8000
```

Then open http://localhost:8000. Serve it rather than opening the file directly,
so the font loads.

## Deploying

Any static host works. On Vercel, import the repo and accept the defaults —
`vercel.json` sets long-lived caching on the font and nothing else.
