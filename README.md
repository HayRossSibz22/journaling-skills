# Journaling Skills

A pair of [Claude Code](https://claude.com/claude-code) skills for keeping a structured,
plain-Markdown journal — set up a workspace once, then file day-to-day notes into it just by
talking.

These are deliberately **un-opinionated about categories**. Everyone tracks different things,
so the setup skill asks you what you want rather than forcing a layout.

## The skills

| Skill | What it does |
|-------|--------------|
| **`/create-journal`** | Scaffolds a new journaling workspace. Prompts you for which categories of notes you want to keep (weekly tasks, bigger projects, meetings, people, or your own), then creates a file per category with sensible templates and a `README.md` index. |
| **`/journal`** | Day-to-day filing. You dump a free-form thought, task, meeting note, or person; it reads your index, figures out where it belongs, matches the existing format, splits run-on input into separate entries, converts relative dates to absolute, and asks only when filing is genuinely ambiguous. |

## Install

Copy the skills into your Claude Code skills directory:

```bash
# User-level (available in every project)
cp -r skills/* ~/.claude/skills/

# …or project-level (just this repo)
mkdir -p .claude/skills && cp -r skills/* .claude/skills/
```

Restart Claude Code (or start a new session) so the skills are picked up. Then:

```text
/create-journal      # set up your workspace once
/journal <anything>  # file notes from then on
```

## How it works

- `create-journal` writes a `README.md` index at your workspace root. That index is the source
  of truth for structure.
- `journal` reads that index every time so it always knows where things go, and keeps it in
  sync when new categories are added.
- Everything is plain Markdown in your own repo — no database, no lock-in.

## License

MIT — see [LICENSE](LICENSE).
