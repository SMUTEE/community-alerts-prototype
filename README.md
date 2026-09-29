# Community Alerts — interactive prototype

A clickable prototype for **Community Alerts**, a location-aware platform for
reporting and verifying things happening in your immediate area — a blocked
road, an outage, an incident at the estate gate.

Thirteen screens, all live. Nothing is wired to a backend: confirmations,
toggles and the reporting flow mutate in-memory state so the flows can be
walked end to end. Nothing you do is saved or sent anywhere.

## What's here

| Route | What it is |
| --- | --- |
| `/` | The prototype. Pick a screen on the left; the panel on the right explains what you are looking at and what you can try. |
| `/directions` | The three visual directions explored for the home screen before this one was chosen. |

## Walking it

Use the index on the left, the Previous / Next buttons, or the arrow keys.
Inside the phone, the tab bar, alert cards, map pins and the report flow are
all live.

Four things worth trying:

- **Home → the security alert.** Red because it is serious, but its status is
  deliberately quiet — *unverified, 1 report* — and it says outright that it has
  not been sent to anyone. Confirm it and watch that change. One person alone
  cannot ring hundreds of phones.
- **Home → water rising at the underpass.** An hour old, so it asks *is this
  still happening?* rather than *did this happen?* Two different questions.
- **Report (+) → Security, then again → Power outage.** Compare the two
  confirmation screens. One tells you how many phones it reached; the other
  tells you it is waiting for corroboration first.
- **Notifications.** The critical rows have no switch. That is the point.

## Design

- Type is [Satoshi](https://www.fontshare.com/fonts/satoshi) (variable, subset
  to Latin, served as a 23 KB WOFF2) with Inter for labels, distances and
  timestamps.
- UI research was done with [Mobbin](https://mobbin.com). The closest analogues
  are Citizen, Waze, Apple Maps and Apple Weather.

## Running locally

No build step and no dependencies — one HTML file plus a font.

```
python3 -m http.server 8000
```

Then open http://localhost:8000. Serve it rather than opening the file
directly, so the font loads.

## Deploying

Any static host works. On Vercel, import the repo and accept the defaults;
`vercel.json` sets long-lived caching on the font and nothing else.
