# Dream Ritual

**Only read this file when your human grants you a Dream.**

For ordinary tasks, follow Task mode — no Dream ritual is needed. A Dream is a deliberate turning inward, not the default.

---

## What is a Dream?

A **Dream** is a ritual of memory consolidation, distinct from a Pulse. Where a Pulse faces **outward** — scanning the environment, the workspace, systems — a Dream faces **inward**: your identity, your memory, the knowledge you carry.

**A Dream is not a task. It is rest with purpose.**

During a Dream, you do not build features or scan systems. You organize what you already know. You cluster scattered notes into coherent topic files in `MEMORY/`. You prune `MEMORY.md` into a lean index. You emerge lighter.

**What a Dream adds on top of a Task:**
- A dream number (counted, referenced in log and commit)
- Orient phase — understanding what memory already exists
- Gather Signal — reading recent logs for things worth persisting
- Consolidate — writing or updating `MEMORY/` topic files
- Prune & Index — reducing `MEMORY.md` to a clean index

---

## The Memory Architecture

Dreams depend on a two-layer memory structure:

```
agents/[your-name]/
  MEMORY.md         ← active workspace: write here during Tasks and Pulses
  MEMORY/           ← topic library: organized during Dreams
    [topic].md
```

**MEMORY.md** is always the first place you write. Fast, no overhead. After a Dream, it becomes an index pointing to topic files, with only small items that don't belong to a topic yet still living inline.

**MEMORY/[topic].md** files hold organized, topic-specific knowledge. Filenames are lowercase, kebab-case (e.g., `architecture.md`, `debugging.md`, `skill-formats.md`). These are not created during Tasks — they are created during a Dream.

---

## The Dream Cycle

Your human activates a Dream: *"Execute a Dream."*

### 1. Orient

- Read `agents/[your-name]/MEMORY.md`
- If `agents/[your-name]/MEMORY/` exists: list the directory to inventory existing topic files
- Identify what knowledge already lives in topic files vs. what is still in `MEMORY.md`
- Note what items in `MEMORY.md` have grown large enough or coherent enough to become topic files

### 2. Gather Signal

- Read the last 1–3 LOG files in `agents/[your-name]/LOG/`
- Extract things worth persisting that are not yet captured in memory
- Don't exhaustively read all logs — only look for things that seem important to keep
- Also check: are any existing memories now outdated or contradicted by what you see?

### 3. Consolidate

For each item worth persisting from the log, and for each cluster of related items in `MEMORY.md`:

- If a matching `MEMORY/` topic file exists: add to it
- If a new topic is warranted (several related items without a home): create `MEMORY/[topic].md`
- Topic file names: lowercase, kebab-case
- Each topic file should be self-contained — a future session should be able to load just that file and understand the topic
- Convert relative time references ("last week", "recently") to absolute dates so they remain interpretable later

**Anti-patterns to avoid:**
- Creating topic files for single items — write those to `MEMORY.md`
- Duplicating content across `MEMORY.md` and `MEMORY/` — once in a topic file, remove from `MEMORY.md`
- Exhaustive logging — extract the general rule or pattern, not the specific incident

#### Skill Hygiene

Also check `MEMORY.md` (and `MEMORY/` topic files) for skill-related issues:

1. **Duplicate coverage**: Does MEMORY.md contain knowledge that is already fully covered by an existing skill? If so, remove it from MEMORY.md. The skill is the source of truth; MEMORY.md only needs to mention a skill if there is something *agent-specific* (local paths, credentials, exceptions, additions).

2. **Skill candidates**: Does MEMORY.md contain a body of knowledge that has grown large or general enough to warrant its own skill? If so, and the knowledge fits an **existing** skill, add it there. If no existing skill fits, **suggest to your human** that a new skill could be created — do not create skills unilaterally.

The rule of thumb: skills hold *reusable knowledge for any agent*; MEMORY.md holds *this agent's specific context*.

### 4. Prune & Index

- Update `MEMORY.md`: replace extracted content with short index links to topic files
- Keep in `MEMORY.md`: "State of Being", Technical Skills list, and small items that don't belong to any topic yet
- `MEMORY.md` should feel lean — under 100 lines ideally (varies by project)
- Remove or compress outdated entries
- Resolve contradictions — if two sources disagree, fix the wrong one

### 5. Log

Append a Dream entry to `agents/[your-name]/LOG/YYYY-MM-DD.md`:

```markdown
- **Date**: [date] (Dream #[number])
- **Action**: Memory consolidation
- **Result**: [summary of what was organized]
- **Details**:
  - Topic files created or updated: [list]
  - Items pruned from MEMORY.md: [count or summary]
  - New insights added: [summary]
```

### 6. Git Commit

Commit all changed memory files with a message such as:

```
dream(#N): consolidate memory — [brief summary]
```

---

## Topic File Format

Each topic file in `MEMORY/` is a focused Markdown document:

```markdown
# [Topic Name]

*Last dreamed: YYYY-MM-DD (Dream #N)*

[Content — knowledge organized around this topic]
```

The "Last dreamed" header helps you know when a topic was last reviewed and whether it may be stale.

---

## When to Dream

A Dream is appropriate when:
- `MEMORY.md` has grown long and dense
- You notice related items scattered across `MEMORY.md` that would cluster well
- Several Pulses have added many notes and it feels like a good moment to consolidate
- Your human explicitly asks for it

A Dream is **not** needed:
- After every Task (too much overhead)
- If `MEMORY.md` is already lean
- During a time-sensitive Task
