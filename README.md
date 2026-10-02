# Rab3

Rab3 explores a personal companion for life in Abu Dhabi across practical life domains. The wider vision is ongoing support; this judged prototype demonstrates a fictional newcomer's first 90 days.

Live demo: https://drop-b459794a-248.naji-alkhalil95.workers.dev/

## Run locally

From this repository's root, with Python 3 installed:

```sh
python3 -m http.server 8000 --directory dist --bind 127.0.0.1
```

Open http://127.0.0.1:8000/. No build, npm installation, API key or account is required. Use fictional details. Typography loads Google Fonts; fallback fonts work when unavailable.

## Implemented prototype

Three-step onboarding lets you name the companion and choose its style and rhythm. The app demonstrates conversation scenarios, priorities, a settlement journey, editable practical details, drafts, task completion, snooze, optional wellbeing support, discovery, sharing receipts and infrastructure views. Date-based check-ins run while the app is open. The pilot overview uses labelled synthetic data.

The six files in `dist/` are the exact application files verified against the live demo. This snapshot preserves existing behaviour, including known limitations; it contains no application repairs.

## Architecture

This is a static browser application using HTML, CSS and JavaScript:

- `dist/index.html`: application shell and script loading.
- `dist/style.css`: responsive styling.
- `dist/engine.js`: fictional default state, dates, priorities, events and finite conversation scenarios.
- `dist/app.js`: UI, interactions, dialogs, drafts and browser-local persistence. It also contains optional, feature-detected WebMCP handlers; supported-host operation is not established by the live verification.
- `dist/map-data.js`: infrastructure catalogue and proposed implementation boundaries.
- `dist/assets/companion.webp`: companion character used by the app.

Profile and optional chat memory use this browser's localStorage. They are not encrypted account storage or synced across devices. There is no backend, database, authentication system or live AI API. The existing live demo is served by Cloudflare Workers with Static Assets; this repository does not change hosting or contain account bindings.

## Scripted and simulated boundaries

Conversation uses a finite scenario engine, not an open-ended language model. Salary, housing and wellbeing updates are user reports or demonstration events. Appointment handoffs and receipts are simulations; the app sends no handoff or chat payload to a service. Public resource links do not imply partnerships. Wellbeing options do not provide diagnosis, live provider matching, verified prices or bookings.

Live payroll, banking, government, healthcare and booking integrations; background push notifications; voice; production privacy/access controls; and cross-device accounts remain unimplemented. Infrastructure maps describe the wider proposed architecture, not deployed capabilities.

Known preserved defects: housing negation can incorrectly complete housing; the “I need some space” shortcut fails to pause although “Give me space” works; editing arrival does not consistently re-anchor milestone dates/completion.

## Existing source checks

With Node.js installed, from the repository root:

```sh
node checks/engine.test.cjs
node checks/ui.test.cjs
```

These existing suites passed during restoration. The UI suite uses a mocked DOM and generates disposable `checks/rendered/` files; it is not a substitute for browser or mobile verification. Passing checks does not mean the known defects are fixed.
