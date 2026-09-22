# Rapid Prototype

A skill for [Claude Code](https://docs.anthropic.com/en/docs/agents-and-tools/claude-code/overview) and [Cowork](https://claude.ai) that turns a concept into a realistic, clickable, single-file HTML prototype for testing with real people. It also writes the test script for running the sessions, and builds in a facilitator panel that logs every screen and tap.

## What it does

1. **Starts from the question, not the screens.** It writes a prototype brief first: what the prototype must answer, who tests it, the 1–3 tasks they'll attempt, what's measured, and what's faked. It takes the brief from an experiment card if you have one.
2. **Writes the content first**: copy in the service's own voice and realistic, imperfect, entirely fictional data (one item out of stock, one slot full).
3. **Builds only the screens the tasks need**, from a shell that handles routing, "not in this prototype" messages for everything else, a phone-sized frame, light and dark themes and accessible defaults.
4. **Includes a hidden facilitator panel** (press `?`): the session's task list, a timestamped log of screens, taps, choices and dead ends, notes, reset, and log download.
5. **Checks it works**: every task completable, no dead ends, no sideways scrolling at phone width, no console errors, no real names or brands in the fake data.
6. **Writes the test script**: screener, plain-English consent, tasks written as scenarios rather than instructions, neutral prompts, observation grid and a synthesis method.

The output is one HTML file. It opens in any browser, works offline, needs no build step or accounts, and stores or sends nothing.

See [`examples/tool-delivery-prototype.html`](rapid-prototype/examples/tool-delivery-prototype.html) for a complete worked example, a doorstep tool-delivery booking journey, with its [`test script`](rapid-prototype/examples/tool-delivery-test-script.md). GitHub shows HTML files as code, so download it and open it in a browser; press `?` to see the facilitator panel. It's built to test the delivery-fee assumption from the [experiment-card skill's](https://github.com/greencat667/experiment-card-skill-claude) worked example.

## Installation

**Ask Claude to set it up for you.** If you're using Claude Code or Claude Cowork, you can just say something like *"install the rapid-prototype skill from github.com/greencat667/rapid-prototype-skill-claude"* and Claude will clone the repo and put it in the right place. You don't need to do this by hand.

Or do it yourself: copy the `rapid-prototype/` folder into your project's `.claude/skills/` directory:

```bash
git clone https://github.com/greencat667/rapid-prototype-skill-claude.git
cp -r rapid-prototype-skill-claude/rapid-prototype/ your-project/.claude/skills/rapid-prototype/
```

Claude will pick it up automatically the next time you start a session.

## Example prompt

Once installed, just ask Claude something like:

> "Make a clickable prototype of a service where people can check whether their home qualifies for a free insulation grant, so we can test it with six older homeowners next week. The question is whether they get through the eligibility questions without help."

## A note on synthetic testing

The skill can walk through the prototype as a first-time user, or hand it to a persona skill, to catch broken flows and confusing words before real sessions. It labels this clearly as a pre-flight check, never as evidence about what real people want or will do. Only real people trying the prototype can tell you that.

## Pairs well with

- [experiment-card](https://github.com/greencat667/experiment-card-skill-claude) — to decide what the prototype should test, and to record the results
- [persona-panel](https://github.com/greencat667/persona-panel-skill-claude) — to rehearse the test script's questions
- [scenario-builder](https://github.com/greencat667/scenario-builder-skill-claude) — pair a scenario with a "future artefact" prototype to make it tangible in a workshop

## Repository structure

```
rapid-prototype-skill-claude/
├── rapid-prototype/
│   ├── SKILL.md                       # Copy this folder to .claude/skills/
│   ├── assets/
│   │   └── prototype-shell.html       # Starting shell: routing, logging, facilitator panel
│   ├── references/
│   │   ├── prototype-patterns.md      # Booking, fake door, onboarding, forms, chatbot, A/B, future artefact
│   │   └── test-script-template.md
│   └── examples/
│       ├── tool-delivery-prototype.html
│       └── tool-delivery-test-script.md
├── README.md
├── CONTRIBUTING.md
└── LICENSE
```

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Note that this repo isn't actively maintained, so responses to issues and PRs will be slow or may never come.

## License

MIT — see [LICENSE](LICENSE).
