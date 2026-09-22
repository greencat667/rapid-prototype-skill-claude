# Test script — Tool delivery prototype

## Prototype brief

| | |
|---|---|
| **Question** | Can renters without a car book a delivered tool without help, and do they stop at the delivery fee? |
| **Linked experiment card** | Experiment 2, "Will they get past the fee?" Right if 5 or more of 8 choose delivery and complete the booking without help after seeing the fee; stop if 2 or fewer |
| **Who tests it** | 8 people renting a flat, with no car, who needed an occasional-use tool or piece of equipment in the last year |
| **Tasks** | 1. Arrange a carpet cleaner for Saturday. 2. Find out what happens if it breaks |
| **What's real, what's faked** | Everything is faked. No bookings are made and nothing leaves the browser. Items, prices, slots and the hub are fictional |
| **Fidelity** | Realistic look, fake data. Only the cleaning category and the booking path are built |
| **Format** | Moderated, in person, on the participant's own phone or a test phone · 8 sessions · 30 minutes each |

The prototype is `tool-delivery-prototype.html`. The delivery fee can be changed with `?fee=0`, `?fee=3` or `?fee=6` (the default). Use the default for all 8 sessions. Only use the other values if the result is inconclusive and the experiment card says to test a lower fee.

## Who we need

People renting a flat (privately or from a housing association or council), without a car, who've needed a tool or piece of equipment they don't own in the last year.

### Screener

1. "Do you rent your home, own it, or something else?" *Include if:* rent (private, housing association or council)
2. "Is your home a flat, a house, or something else?" *Include if:* flat or maisonette
3. "Does anyone in your household have a car or van you can use?" *Include if:* no
4. "In the last year, have you needed a tool or piece of equipment you didn't own, like a drill, ladder or carpet cleaner?" *Include if:* yes
5. "Do you work for, or volunteer with, a tool library, repair café or environmental charity?" *Exclude if:* yes
6. "Which of these times could you do for a 30-minute session?" [times]

**Mix we're aiming for:** at least 5 of 8 receiving a means-tested benefit or council tax reduction (self-declared, optional to answer); at least 2 aged over 50; at least 2 who describe themselves as not very confident online.
**Thank-you payment:** £25 voucher, given at the start so nobody feels they must finish.

## Before the session

- [ ] Prototype open on the test phone, with the facilitator panel checked (press `?` on a keyboard, or tap the orange banner three times) and then closed
- [ ] Reset the prototype from the facilitator panel
- [ ] Participant ID (P01–P08) entered in the facilitator panel
- [ ] Task card printed (below)
- [ ] Note-taker ready with the observation grid

### Task card (give to the participant)

> You can use these made-up details if the prototype asks for them:
>
> **Name:** Sam Taylor
> **Address:** Flat 12, Canal View
> **Postcode:** ZZ1 1ZZ
> **Mobile:** 07700 900123
> **Lift in your building:** Yes

## Introduction and consent (read aloud, about 3 minutes)

"Thanks for coming. We're testing an early idea for borrowing tools and equipment, and we'd like to see how it works for you.

We're testing the idea, not you. There are no wrong answers, and if something's confusing, that's exactly what we need to know. I didn't design it, so you won't hurt my feelings.

This is a mock-up. Nothing you type is saved or sent anywhere, and no real booking or payment happens. Please use the made-up details on this card rather than your own.

As you go, please think out loud: say what you're looking at, what you expect and what you're unsure about.

We'd like to record the screen and audio so we don't have to take notes the whole time. Only the project team will see it, and we'll delete it within three months. Is that OK?

You can stop at any time, and skip anything you'd rather not do. Any questions before we start?"

## Warm-up (about 5 minutes)

- "Tell me about the last time you needed a tool or bit of equipment you didn't have."
- "What did you do?" *(Bought it, borrowed it, hired it, went without?)*
- "How did you get it home, or back?"
- "Have you ever borrowed or hired something like that before? How did it go?"

## Tasks

For each task, read the scenario aloud and hand over the phone. Stay quiet unless they're stuck for more than a minute.

### Task 1 — Carpet cleaner for Saturday

> "Your landlord wants the carpets cleaned before you move out on Saturday. You don't have a car. See if you can sort that out using this."

**Done when:** the "You're booked in" screen appears.
**Watch for:**

- which option they choose on "How do you want to get it?", and whether they read both
- their reaction at the check-and-book screen, where the £6 fee and the total appear
- whether they notice the full slots, and how they react
- any sign they're looking for a cheaper option or a way out

**After the task:** "How did that go?" · "Was there anything you expected that wasn't there?"

### Task 2 — If it breaks

> "While you're using it, the carpet cleaner stops working. Find out what you'd do, and whether it would cost you anything."

**Done when:** they reach "If something breaks" and can say in their own words what they'd do and what it might cost.
**Watch for:** where they look first; whether the £20 maximum reassures or worries them.

### If they go quiet or get stuck

- "What are you thinking right now?"
- "What did you expect to happen when you did that?"
- "What would you do now if I weren't here?"
- After a minute stuck: "Where would you look for that?" If they're still stuck, note it and move on.

**Don't:** point at things, name buttons, explain the design, mention the fee before they reach it, or ask "would you use this?" during a task.

## Debrief (about 5 minutes)

- "In your own words, what is this service?"
- "What did you think about the cost of delivery?" *(Then:)* "Compared with what?"
- "Delivery comes in a two-hour window, and someone needs to be in. How would that work for you?"
- "What would stop you using something like this?"
- "Is there anything you'd change first?"
- At the very end, and treated as weak evidence: "If this existed near you, how likely would you be to try it?"

Download the log from the facilitator panel and save it as P0X. Then thank them.

## Observation grid (one per participant)

| Task | Completed? (yes / with help / no) | Chose delivery? | Time | Hesitated at | Said at fee screen | Log file |
|---|---|---|---|---|---|---|
| 1 | | | | | | |
| 2 | | n/a | | | n/a | |

## Synthesis

1. **Completion table.** Participants × tasks: completed unaided, with help, or not at all.
2. **The number for the experiment card:** how many of the 8 chose delivery *and* completed Task 1 without help after seeing the fee. Compare with the thresholds (5 or more = right; 2 or fewer = stop).
3. **Drop-off points.** Use the logs: the last `view` before anyone gave up, any `blocked` events, and any `back` from the check-and-book screen.
4. **Issues,** grouped and ranked by how many people hit each and how badly (blocker / slowed down / minor).
5. **Answer the question** in one paragraph, with the numbers.
6. **What this can't tell us.** Whether people would really pay, since no money changed hands, and how many people across the area would use it. That's Experiment 3.
7. **Hand back:** complete the learning card for Experiment 2.
