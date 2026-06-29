---
name: journal
description: Route free-form notes into the right journal file with appropriate headings. The user dumps an unstructured thought, task, meeting note, or person, and this files it under the correct category, matching the existing format. Use for day-to-day journaling once a workspace exists (see the `create-journal` skill to set one up).
---

# journal

Help the user organize input they give you: take whatever they say and put it in the right
file, under the right heading, formatted like the notes already there. This is a filing
assistant, not a rewriter — preserve the user's meaning, just structure it.

## Steps

1. **Learn the structure.** Read the workspace `README.md` index to see which files exist and
   what each is for. If there's no index, look for Markdown note files in the working
   directory. If nothing exists yet, tell the user to run `create-journal` first (or offer to).

2. **Classify the input.** Decide which category/file the input belongs to. Examples:
   - A to-do or deadline → the weekly-tasks file (current-week section, or backlog if not urgent).
   - A longer-running effort → the bigger-projects file (new or existing project section).
   - Notes from or prep for a meeting → the meetings file (newest at top).
   - A person the user met or works with → the people file.
   If the input mixes several things (a run-on dump), **split it into discrete items** and file
   each where it belongs — don't force it all into one place.

3. **Read the target file before editing** so you match its existing structure: heading style,
   ordering (e.g. meetings newest-first), checkbox vs. bullet, the fields each entry uses. New
   entries should be indistinguishable in form from the ones already there.

4. **File it.**
   - Add under the appropriate existing heading, or create a new heading/section if the topic is new.
   - Convert relative dates to absolute (`YYYY-MM-DD`) — "next Friday" becomes the real date.
   - Keep the user's wording and intent; tighten only for clarity, never invent facts.
   - If the input clearly belongs in a category that has no file yet, create the file (with a
     sensible template) and add a row to the `README.md` index.

5. **Handle ambiguity.** If you genuinely can't tell where something goes, or a detail is
   missing that changes the filing (e.g. a name spelling, a date), ask a brief clarifying
   question rather than guessing. For everything else, file it and move on.

6. **Report.** Briefly say what you filed and where (one line per item). Flag anything you had
   to interpret — date guesses, name spellings, items split out — so the user can correct you.

## Principles

- One input can become several entries in several files — split run-ons.
- Match the destination file's existing format exactly; read before writing.
- Absolute dates always.
- Keep the `README.md` index in sync when you add a new file.
- Don't oversell or editorialize — file faithfully and note your assumptions.
