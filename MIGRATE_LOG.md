# MIGRATE_LOG: Log Migration Guide

**Only read this file if your human has explicitly asked you to migrate a `LOG.md` file.**

---

## The Situation

Your agent folder contains a `LOG.md` file. This is the old log format—a single append-only Markdown file containing all log entries for the agent's entire history.

The current format is a `LOG/` directory where each day has its own file: `LOG/YYYY-MM-DD.md`.

---

## Old Structure

```
agents/[agent-name]/
  LOG.md          ← one flat file, all history
```

Entries in `LOG.md` come in various formats depending on when they were written. Common patterns include:

- `- **Date**: Mon Feb  2 2026 (Pulse #N)` — structured pulse entries with date header
- `## Pulse #N — Weekday Month Day Year` — pulse entries with Markdown heading
- `- [DD-MM-YYYY]: ...` — early-format entries with Dutch-notation date in brackets

There is no guaranteed consistency—the format evolved organically. **You must scan the file yourself** to understand what is there before you migrate.

---

## New Structure

```
agents/[agent-name]/
  LOG/
    YYYY-MM-DD.md   ← one file per calendar day
    YYYY-MM-DD.md
    ...
```

Each day-file:
- Has the header: `# LOG — YYYY-MM-DD`
- Contains all entries from that calendar day, in original order
- Is append-only once created

---

## Migration Approach

You may migrate with a script or manually—your choice. The goal is the same either way:

1. **Scan `LOG.md`**: Read the full file and identify all log entries. Determine the date of each entry (parse date strings from headers).
2. **Group by calendar day**: Entries on the same date belong in the same day-file.
3. **Write to `LOG/`**: Create the directory. For each unique date, create `LOG/YYYY-MM-DD.md` with the appropriate header and entries.
4. **Handle ambiguity**: Some entries may have unclear or missing dates. Use your judgment—surrounding context usually reveals the approximate date. If truly ambiguous, assign to the nearest known date and add an inline note.
5. **Verify**: Spot-check a few day-files against the original to confirm nothing was lost or reordered.
6. **Remove `LOG.md`**: The original is preserved in git history. Delete the file to keep the folder clean.

### If using a script

Write the script in whatever language is available in the workspace. The script should be single-use: run it, verify output, then delete it.

### If doing it manually

Read `LOG.md` section by section. Create day-files in chronological order. Copy entries verbatim—do not summarize or rephrase. Append-only applies to the destination files even during migration.

---

## After Migration

- Confirm the `LOG/` directory contains day-files covering the full date range of the old log.
- Delete `LOG.md` (or rename to `LOG.md.bak` if you want a local backup—but it is not necessary).
- Commit the result: `git commit -m "Migrate LOG.md to LOG/ directory structure"`
- Report completion to your human.
