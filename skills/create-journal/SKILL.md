---
name: create-journal
description: Scaffold a new journaling workspace — prompts the user for which categories of notes they want to keep, then creates an index plus one file per category with sensible templates. Use when someone wants to start journaling/note-taking from scratch, set up a notes workspace, or initialize a journal. Pairs with the `journal` skill for day-to-day entries.
---

# create-journal

Set up a fresh journaling workspace for the user. The structure is **not fixed** — different
people track different things, so the first job is to ask what *they* want, then scaffold it.

## Steps

1. **Pick the location.** Default to the current working directory. If it already contains a
   journal (a `README.md` index plus note files), don't clobber it — tell the user it looks
   set up already and offer to add categories instead. Otherwise confirm the directory.

2. **Ask what categories they want to track.** Use the AskUserQuestion tool (multi-select) so
   the choice is theirs. Offer common starting categories as options, and make clear they can
   add their own:
   - **Weekly tasks** — recurring and current-week to-dos
   - **Bigger projects** — longer-running initiatives
   - **Meetings** — meeting notes and action items
   - **People** — colleagues, contacts, relationships
   Always allow free-form additions (e.g. "reading log", "decisions", "ideas"). Do not assume
   a category they didn't pick.

3. **Ask about layout** only if it matters: a flat set of files in one folder is the default
   and is best for most people. Offer subfolders (e.g. an `ongoing-tasks/` group) only if they
   have many categories or ask for grouping. Keep it simple unless told otherwise.

4. **Scaffold the files.** For each chosen category, create a Markdown file with a heading, a
   one-line purpose, and a minimal template the user can fill in. Suggested templates:
   - *Weekly tasks:* a `## Week of <YYYY-MM-DD>` section with empty checkboxes, plus a `## Backlog`.
   - *Bigger projects:* "one section per project" with **Status / Goal / Next step** and a Notes subsection.
   - *Meetings:* "newest at the top", each entry `## <YYYY-MM-DD> — <title>` with Attendees, Summary, and Action items.
   - *People:* "one section per person" with **Role / team**, **Context**, **Notes**.
   For custom categories, infer a reasonable template from the name, or keep it to a heading +
   purpose line.

5. **Create the index.** Write a `README.md` at the workspace root: a short intro and a table
   mapping each file to its purpose. This index is what the `journal` skill reads to learn the
   structure, so keep file paths accurate. Date-stamp it (`_Created <YYYY-MM-DD>._`).

6. **Confirm.** Summarize what was created and remind the user they can capture entries later
   with the `journal` skill. Mention they can rerun this skill to add categories.

## Principles

- Ask, don't assume — the categories are the user's call.
- Use absolute dates (`YYYY-MM-DD`), never "today"/"this week", in the files themselves.
- Keep templates minimal; the user fills them in over time via `journal`.
- The `README.md` index is the source of truth for structure — every note file must appear in it.
