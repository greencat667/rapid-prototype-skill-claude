# Prototype patterns

Starting points for common prototype types. Each lists the screens you usually need, what the pattern is good at testing, and the traps. Build only the screens your tasks need.

## Service booking

**Screens:** browse or search → item detail → choose time → choose how (collect / delivery) → your details → confirm → done
**Tests:** can people complete a booking; where they drop out; how they react to price, time slots and conditions
**Traps:** hiding the price until the end (tests a different thing); only showing available slots (real services have full ones); skipping the "what if something goes wrong" information that trust depends on
**Tip:** make one popular item or slot unavailable — how people recover from that is often the most useful moment of the session

## Sign-up or fake door

**Screens:** landing page with the offer → interest step (e.g. "Join the waiting list" / "Check if it's in your area") → short form → honest ending ("This isn't live yet — thanks, here's what happens next")
**Tests:** will people take a first step towards the offer, and which message gets more of them to do it
**Traps:** taking payment or card details (never do this); pretending the service exists after the final step; traffic from friends and colleagues instead of the real audience
**Tip:** the metric is the share of visitors who take the interest step. Decide the threshold before launching (see the experiment card).

## Onboarding

**Screens:** welcome → 2–4 steps collecting what's needed → first useful moment
**Tests:** do people understand what the thing is for, and do they reach the first useful moment
**Traps:** asking for information before showing value; too many steps; tooltips explaining a confusing screen instead of fixing it

## Search and choose

**Screens:** search or category list → results with filters → comparison or detail → choice
**Tests:** can people find the right thing; which information they use to decide
**Traps:** too few results to feel real, or so many that the session is about scrolling; results that are too perfectly relevant

## Form-heavy application

**Screens:** eligibility check → one question per screen (or small groups) → check your answers → submitted
**Tests:** where people get stuck, what they don't understand, what they don't have to hand
**Traps:** building every question — build the hard ones and stub the rest; asking for real personal data in testing (use a persona card with fake details the tester can copy)
**Tip:** "one thing per page" works well on phones and makes drop-off points obvious in the log

## Chatbot or assistant (Wizard of Oz)

**Screens:** chat window with suggested prompts
**Tests:** what people ask, in their own words; whether they trust the answers; where they want a human
**How:** for a moderated session, a facilitator types replies from another device or picks from prepared replies. For an unmoderated prototype, script a small set of replies keyed to likely questions and a clear "I can't help with that yet" fallback. Tell participants afterwards if a person was answering.
**Traps:** letting it sound more capable than the real thing would be; collecting sensitive information in free text

## Comparison (A/B)

**Screens:** two versions of the same screen or journey, switched with a parameter (e.g. `?v=a` / `?v=b`) and logged
**Tests:** which version more people complete, or understand
**Traps:** tiny samples — with 8 testers, you can see big differences in understanding, not small differences in rates; changing more than one thing between versions

## Future artefact

**Screens:** a single realistic object from a possible future — a news article, a council letter, a product label, an app notification, a receipt, a job advert — often shown next to its present-day equivalent
**Tests:** reactions to a scenario made concrete: what feels desirable, worrying or implausible
**Traps:** real mastheads, logos or organisation names (never — make up a publication or body and say it's fictional); making it so polished it reads as real news
**Tip:** pair with a scenario from the `scenario-builder` skill. Ask people what they'd do the week this artefact arrived — that's where the useful answers are.

## Common screen elements in the shell

| Need | Shell element |
|---|---|
| List of choosable items | `.card` buttons with `.thumb`, `.title`, `.muted` |
| Single choice | `.options` with `label.option` + radio `data-bind` |
| Price / order summary | `.summary` with `.row` and `.row.total` |
| Important condition or warning | `.notice` |
| Primary / secondary / text button | `.btn`, `.btn.secondary`, `.btn.link` |
| Status label | `.tag`, `.tag.warn` |
| Confirmation | `.hero-emoji` + `h2` + summary |
