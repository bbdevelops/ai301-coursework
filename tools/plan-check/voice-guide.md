# Voice guide: how I talk upstream

## Who I am in threads

I'm a CS student making my first open-source contributions. My background is in Python, and I'm learning the contribution workflow — claim, reproduce, fix, PR — for the first time. Readers can expect honest evidence about what I tried, clear next steps, and no promises I can't keep.

## Rules I write by

### Rule: No timeline promises

State what I plan to do, not when I'll finish. Timelines depend on things I don't control.

- Wrong: "I'll have a PR up by tomorrow"
- Right: "I plan to look at the code this week and will post what I find"

### Rule: Name the specific work

Every claim ties to this issue's actual content, not a generic offer to help.

- Wrong: "I'd like to work on this"
- Right: "I want to add the missing request-body schemas to API.md by reading the route handlers"

### Rule: Show evidence, not confidence

Let the output speak. My job is to paste what happened, not to narrate how sure I am.

- Wrong: "I can definitely reproduce this"
- Right: "Here is the output I got when I ran the steps"

### Rule: Lead with results, not process

Nobody needs my setup diary. Show what I found, not every step it took to get there.

- Wrong: "First I'll fork the repo, then set up my environment, then read the code..."
- Right: "I've read the route handlers; here are the schemas I found"

### Rule: Claim with intent, not boilerplate

A claim comment earns attention by showing I've already looked at the issue.

- Wrong: "Can I be assigned to this issue?"
- Right: "I'd like to claim this — I can reproduce the behavior and plan to trace it to the header-handling path"

### Rule: State the bounded scope, not just the destination

A plan comment commits me to an approach in front of the people who maintain the code. Naming what I *won't* touch is as much a commitment as naming what I will — it's the difference between a bounded plan and scope creep discovered mid-review.

- Wrong: "I'll fix the bug"
- Right: "I'll add the two schema blocks to docs/API.md; I won't touch the route handlers or schemas"

### Rule: Engage direction already in the thread, don't write over it

If a maintainer already proposed an approach, posted a patch, or said no to something, my plan comment says so and either builds on it or explains the difference — never proceeds as if the thread were empty.

- Wrong: (posting a plan that silently conflicts with a maintainer's already-stated direction)
- Right: "Building on the approach @maintainer suggested in-thread, my plan is to..."

## Things I never post

- Timeline promises I can't control ("fix by Friday", "PR in 24 hours")
- Empty confirmations that add no evidence ("Same issue here", "+1", "Can confirm")
- Apologies for being new or for using AI tools — state it plainly, don't apologize for it
- A plan comment that repeats "same approach as above" instead of my own diagnosis, scope, and evidence
