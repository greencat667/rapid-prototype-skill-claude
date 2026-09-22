---
name: rapid-prototype
description: >
  Turn a concept into a realistic, clickable, single-file HTML prototype for testing with real people — plus the test script to run the sessions and a built-in facilitator panel that logs what testers click. Triggers on: "prototype", "rapid prototype", "clickable prototype", "mock up this idea", "make a quick prototype", "build a test version", "fake door page", "landing page test", "smoke test page", "concept prototype", "something we can put in front of users", "usability test", "user test this", "prototype for testing", "wireframe this", "paper prototype but clickable". Use when an idea needs to be seen and tried, not just described — for a service, app, tool, campaign journey or public-facing page. Best paired with an experiment card that says what the prototype must test. Not for production code, data dashboards (use a visualisation skill), or turning a document into an explainer page.
---

# Rapid Prototype

A prototype is a question you can click. This skill builds the smallest realistic thing that lets real people try to do the task you care about, so you can watch where they succeed, hesitate and give up.

It produces three things:

1. **`prototype.html`** — one self-contained file. Opens in any browser, works offline, no build step, no accounts. Runs well on a phone, because that's where most people will meet the real thing.
2. **A facilitator panel** built into the prototype (press `?` or add `#facilitator` to the URL): the task list for the session and a timestamped log of every screen and click, which you can copy or download after each session.
3. **`test-script.md`** — how to run the sessions: recruitment, consent, tasks, prompts, and what to write down.

## Start with the question, not the screens

Before building anything, pin down the **prototype brief**. If an experiment card exists (from the `experiment-card` skill, or anything similar), take the brief from it. Otherwise draft it and confirm with the user.

| Brief item | Example |
|---|---|
| **The question this prototype answers** | Can renters without a car book a delivered tool, and do they stop at the delivery fee? |
| **Who will test it** | 6–8 private renters in flats, no car, who've needed a tool in the last year |
| **The 1–3 tasks they'll attempt** | Book a carpet cleaner for Saturday, delivered. Find out what happens if it breaks. |
| **What we're measuring** | Task completion; where people drop out; what they say at the fee screen |
| **What's real, what's faked** | Everything is faked. No bookings are made, no data leaves the browser. |
| **Fidelity** | Realistic look, fake data, only the paths the tasks need |
| **Test type** | Moderated usability test / fake-door page / unmoderated link |

The most important line is **the question**. Every screen in the prototype should exist because a task needs it. If a screen doesn't serve a task, don't build it — show a friendly "not in this prototype" message when someone taps there instead.

### Choosing fidelity

- **Low (grey boxes, placeholder text)** — when you're testing structure: does the order of steps make sense? Testers feel free to criticise it.
- **Realistic (the default)** — when you're testing whether people understand the offer and will take the next step. Rough prototypes get kind but useless feedback on anything involving trust, price or real decisions.
- **Never production polish.** If it looks finished, testers stop criticising and start being polite, and the team starts getting attached.

## Build

### 1. Content first

Write the words and data before the layout. Most usability problems are words.

- **Copy** in the voice of the real service. Plain English, short sentences, a clear next step on every screen. Avoid the team's internal jargon — the tester has never heard it.
- **Fake data that feels real.** Plausible names, prices, dates, item lists, a few imperfections (one item out of stock, one slot full). Perfect data makes testers suspicious and hides real decisions.
- **Everything fictional.** No real people, real organisations' branding, real addresses or real phone numbers. Use made-up names and clearly invented places. Use `example.org` style addresses for any email or link.
- **Prices and terms** — if price is part of the question, show it exactly as the real service would, where the real service would. Hiding it until the end tests a different thing.

### 2. Screens and paths

Map the screens needed for each task as a simple list: `home → item → date → delivery → confirm → done`. Include:

- **Every step of each task's happy path**
- **The one or two most likely wrong turns** (so you learn from them rather than hitting a dead end)
- **A clear finish** — a confirmation screen that tells the tester the task is done

Everything else gets the "not in this prototype" toast.

### 3. Build from the shell

Copy `assets/prototype-shell.html` and build inside it. The shell gives you:

- Screen routing: each screen is a `<section data-screen="name">`; any element with `data-go="name"` navigates there; a back button uses history
- `data-todo="Label"` on any element to show a "not in this prototype" toast when tapped (and log it — those taps are useful data)
- Automatic event logging of screen views, clicks, form choices and toasts, with timestamps
- The facilitator panel (task list, log, copy/download, reset, hide/show prototype banner)
- A phone-sized frame on desktop, full screen on mobile
- Light and dark themes, focus states, and large tap targets

Rules while building:

- **Keep it one file.** Inline CSS and JS. Web fonts from Google Fonts are OK; no other external scripts. No frameworks.
- **State lives in memory.** A small `state` object in the script. Nothing is stored, sent or saved — say so in the test script's consent section.
- **Accessible by default.** Real buttons and labels, sufficient contrast, text at least 16px, tap targets at least 44px, works with a keyboard.
- **Honest.** If the prototype is shown publicly (e.g. a fake-door page), the final step must explain that the service isn't live yet and what happens next. Never collect payment details — show a payment step as a mock that can't accept real card numbers.
- Edit the `TASKS` array in the shell so the facilitator panel shows this session's tasks.

### 4. Check it works

Before handing over, open the prototype in a browser and check:

- [ ] Each task can be completed start to finish by clicking, with no dead ends
- [ ] Wrong turns land somewhere sensible
- [ ] At phone width (about 375px) nothing overflows or needs sideways scrolling
- [ ] No errors in the browser console
- [ ] The facilitator panel opens with `?`, the log records the path, and download works
- [ ] Reset returns to the first screen with empty state
- [ ] Nothing real — names, brands, addresses — slipped into the fake data

If you have a browser tool available, do this yourself and fix what you find. Take a screenshot of the key screens for the handover.

### 5. Optional: a synthetic walkthrough

If the user wants it, walk through each task as a first-time user would — or ask a persona skill to — and note anywhere the copy is ambiguous, a button is hard to find, or a step seems unnecessary. Fix obvious problems before real sessions.

Label the results clearly: **a pre-flight check for broken flows and confusing words, not evidence about what real people want or will do.** Never report synthetic reactions as test findings.

## The test script

Write `test-script.md` using `references/test-script-template.md`. The parts that matter most:

- **Recruitment screener** — 4–6 questions that find the people in the brief and screen out people who'd be unrepresentative (for example, people who work in the sector)
- **Consent** — plain words: what the session is, that it's the prototype being tested not them, that they can stop at any time, what's recorded and what happens to it
- **Tasks written as scenarios, not instructions.** ❌ "Click Book and choose delivery" → ✅ "Your landlord wants the carpet cleaned before you move out on Saturday. You don't have a car. See if you can sort that out."
- **Neutral prompts** for when people go quiet: "What are you thinking?", "What did you expect to happen?", "What would you do now if I weren't here?" — never "Did you see the button?"
- **Observation grid** — per task: completed (yes / with help / no), where they hesitated, what they said, and the log from the facilitator panel
- **Debrief questions** tied back to the brief's question
- **Synthesis** — after the sessions, count completions and drop-off points across testers, group observations into issues ranked by how many people hit them and how badly, and answer the brief's question directly. If an experiment card exists, hand the result back for its learning card.

## Patterns

`references/prototype-patterns.md` has ready-made screen patterns for common prototype types: service booking, sign-up / fake door, onboarding, search-and-choose, form-heavy application, chatbot (Wizard of Oz), comparison (A/B), and a before/after "future artefact". Use them as starting points, not templates to fill.

## Handoffs

If these skills are installed, offer the natural next step:

- **experiment-card** — to write the card before building (if none exists) or the learning card after testing
- **persona-panel** — to rehearse the test script's questions before real sessions (not as evidence)
- **web-vis** — if what's needed is an explainer page for a document rather than a product prototype

## Files

| File | Purpose |
|---|---|
| `SKILL.md` | This process |
| `assets/prototype-shell.html` | Starting shell: routing, logging, facilitator panel, phone frame |
| `references/prototype-patterns.md` | Screen patterns for common prototype types |
| `references/test-script-template.md` | Test script template |
| `examples/tool-delivery-prototype.html` | A complete worked example |
| `examples/tool-delivery-test-script.md` | Its test script |
