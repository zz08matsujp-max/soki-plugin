---
name: import-notes
description: Read a folder of Markdown notes and seed SOKI with the due dates and unfinished items found in them. Use when the user says they already have notes (an Obsidian vault, a Logseq graph, a folder of .md files) and wants SOKI to know about them, or says things like "read my notes into SOKI", "import my vault", "SOKI doesn't know anything yet", "ノートを読ませたい", "vault を取り込みたい".
---

# Seed SOKI from existing notes

SOKI only knows what has been said to it, so a new account returns nothing for
the first few weeks. Most people who want SOKI already have years of notes
sitting in a folder. This skill moves what is still *live* in those notes into
SOKI, so it has something to hand back on day one.

## What to take, and what to leave

Take only two kinds of line. Everything else stays in the notes.

| Take | Looks like | Record as |
|---|---|---|
| A date that has not passed | `2026-09-24 までに提出`, `- [ ] ship by 10/3` | `plan` with `refers_to_at` |
| An unfinished item | `- [ ] …` that is not `- [x]` and not struck through | `open` |

**Leave everything else.** Do not import prose, ideas, meeting notes or
reference material. SOKI is not a second copy of the vault — it is the small set
of things that are still open. Importing the whole vault makes every later
recall worse, because the signal drowns.

## Steps

1. **Ask which folder**, unless the user already named one. Read only `.md`,
   `.markdown` and `.txt`.

2. **Skip machine-written files.** Anything under `.obsidian`, `.git`,
   `node_modules`, `_tools`, `templates`, and any file whose front matter
   declares it generated, or whose name starts with `_TODAY_` or `_DAILY_`.
   Re-importing a generated file means importing SOKI's own output.

3. **Find the candidates.**
   - Dates: `YYYY-MM-DD`, `YYYY年M月D日`, and bare `M/D`. Require a
     deadline word within about 30 characters of the date — まで, 期限, 締切,
     期日, 予定, due, by, deadline — unless the line is an unchecked `- [ ]`,
     where the checkbox already says it is pending.
   - Reject a date that is immediately followed by 追加, 記録, 作成, added,
     recorded — that is when the line was written, not when it is due.
   - Reject a date sitting inside quotation marks（「」『』"…"）— that is
     someone else's words being quoted, not the user's own plan.
   - Reject a line that is already `- [x]`, or wrapped in `~~strikethrough~~`.

4. **Rank before importing.** Prefer items from files the user is still editing
   (recent modification time). An unfinished line in a file untouched for years
   is usually a dead project, not a loose end — and importing hundreds of those
   is the fastest way to make SOKI useless.

5. **Show the list and stop.** Present at most 20 items, grouped into
   「期日（dates）」 and 「開いたまま（open）」, each with its source file.
   **Do not write anything to SOKI yet.** Ask which ones to keep. Offer
   "all of them", "the dates only", or a selection.

6. **Record the approved ones**, one `memory_observe` call each:
   - Dates → `category: "plan"`, `refers_to_at: "YYYY-MM-DD"`
   - Unfinished → `category: "open"`, no date needed
   - `subject` is the project when the folder makes that obvious, otherwise leave it.
   - Copy the line's own wording. Do not summarise, do not interpret, do not
     add a judgement about the user. SOKI rejects interpretations by design.
   - Names of other people must be replaced with a pseudonym（Aさん / "A"）.

7. **Report what went in and what did not**, and say plainly that the notes
   themselves were not modified.

## Limits to respect

- **Never import more than 50 items in one run**, even if asked. Suggest running
  again later. A memory layer full of dead items returns dead items.
- **Never write back into the user's notes.** This skill reads only.
- If SOKI declines an observation (it refuses some categories on its own),
  say so — do not store it anywhere else instead.
