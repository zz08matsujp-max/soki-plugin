---
name: handover
description: Build a handover document from what SOKI remembers, for a future reader who has lost the context — a colleague, a different AI, or the user in six months. Use when the user asks for a handover, a 引き継ぎ書, a status write-up, "catch someone up on this project", "summarise where we are", or is about to hand work to someone else.
---

# Write a handover from memory

A handover document is written for someone who has lost the thread. That makes
it the one document worth generating from a memory layer: everything in SOKI is
already dated, weighted, and separated into decisions, open items and pitfalls.

## Steps

1. **Read the memory first.** Call `profile_get` (scope `project` when the user
   names one, otherwise `all`), then `profile_due` so that anything with a date
   is in hand before writing.

2. **Ask who is going to read it** if the user has not said. The answer changes
   the document completely:
   - a person taking over the work
   - a different AI being brought up to speed
   - the user's future self

3. **Lay it out in this order.** A reader with no context needs the current
   state before the history.

   - **Where it stands now** — one paragraph, no history
   - **Decisions, and why** — each with its date and its stated reason. Where
     SOKI recorded a reason, keep the reason attached to the decision; it is what
     lets the next person ask whether it still holds
   - **Still open** — the `open` items, oldest first
   - **Dates coming up** — from `profile_due`
   - **Known pitfalls** — the `pitfall` items. These are the most valuable part
     of any handover, because they are the things that cost someone a day
   - **What is deliberately not being done** — if the memory records it

4. **Mark confidence.** SOKI returns some memories flagged as needing
   confirmation. Carry that flag into the document rather than presenting
   everything as equally certain. Where a flagged item matters, ask the user
   whether it still holds, and record the answer with `memory_confirm`.

5. **Cite dates.** Every claim that came from memory carries the date it was
   recorded. A handover without dates cannot be checked later.

## Rules

- **Write only what is in the memory.** If something is missing, say it is
  missing. Do not fill the gap with a plausible guess — a handover is read by
  someone who cannot tell the difference.
- **Pseudonyms stay pseudonyms.** Do not try to resolve 「Aさん」 to a real name.
- Offer the result as a file when it runs long; otherwise put it in the reply.
- Ask before recording anything new. Writing a handover is a read operation.
