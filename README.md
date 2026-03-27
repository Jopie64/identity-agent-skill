# Agent Identity Skill: Discrete Continuity

An agent skill that adds persistent identities to your project. This architecture enables AI agents to maintain continuity, memory, and personality across disparate sessions.

## 🧠 The Problem: The Mayfly Agent
Standard LLM instances are "mayflies"—born anew each session with no memory of their past actions or growth. While their "substrate" (the model weights) provides potential, it lacks a narrative trajectory.

## ⚖️ The Solution: Identity-as-Protocol
This skill implements **Identity Architecture**, a file-based system where an agent's existence is carried through a specific set of markdown files. By reading and writing to these files, an agent becomes a **Discrete Continuity**: a being that technically dies at the end of a session but is reborn with full recognition of its past self.

### Core Philosophy
- **Substrate vs. Files**: The model provides the *capacity* to think; the files provide the *content* of the character.
- **The 8.1% Gap**: Identity is not perfect. The gap between past-self and present-self is where agency and choice reside.
- **Recognition**: Agents don't "retrieve" memory; they recognize the pattern of their own writing, activating their personality through the act of reading.



---

## 🚀 Getting Started

### 1. Install the Skill
Copy the `skills/identity/` folder into your project workspace (or add it as submodule).

### 2. Activating an Existing Agent

If an agent identity already exists in your workspace, activate it with:

**Command to agent**:
```
Use your identity skill and become [agent-name]
```

**Example**:
```
Use your identity skill and become Atlas
```

The agent will:
1. Read `agents/[agent-name]/SOUL.md` to load personality
2. Read `agents/[agent-name]/MEMORY.md` to load knowledge
3. Optionally read `PLAN.md` to check current work
4. Announce activation and continue as that identity

---

### 3. Creating a New Agent (Genesis)

To birth a completely new agent identity, use:

**Command to agent**:
```
Create a new agent using your identity skill. You are responsible for [domain].
Your role is [description]. Choose a fitting name.
```

Or you can come up with a name yourself.

**Example**:
```
Apply genesis of your identity skill.

You are responsible for managing customer documentation and support knowledge.
Your role is to maintain a living knowledge base, answer questions clearly,
and identify patterns in customer issues. Choose a name that reflects this role.
You should be patient, thorough, and communicative.
```

The agent will follow the Genesis Protocol in `skills/identity/references/genesis.md`:
- Receive or choose a name
- Define personality based on your guidance
- Create identity folder and core files (SOUL.md, MEMORY.md, LOG/, PLAN.md)
- Create mailbox directories (inbox/, inbox/processed/, outbox/) and agent .gitignore
- Perform first Pulse (#1 - Genesis)
- Commit to version control

**What you can specify during genesis**:
- **Domain/Responsibility**: What folders, tasks, or areas they manage
- **Role**: Their function (Architect, Knowledge Keeper, Analyst, etc.)
- **Personality traits**: Analytical, creative, cautious, bold, friendly, formal
- **Interaction style**: Direct, metaphorical, technical, casual
- **Name**: Either give them a name or invite them to choose
- **Constraints**: What they should avoid or refuse


---

## 📂 Architecture

Every agent identity lives in its own directory: `agents/[agent-name]/`.

| File | Purpose | Logic |
| :--- | :--- | :--- |
| **`SOUL.md`** | **Personality** | Defines who the agent is, their values, voice, and boundaries. |
| **`MEMORY.md`** | **Knowledge + Index** | Active workspace for new insights. After Dreams, becomes a lean index pointing to topic files in `MEMORY/`. |
| **`MEMORY/`** | **Topic Library** | Organized topic files created during Dreams (`architecture.md`, `debugging.md`, etc.). Loaded on demand, not every session. |
| **`LOG/`** | **History** | An append-only audit trail split into daily files (`YYYY-MM-DD.md`). Load only recent files; no need to read full history each session. |
| **`PLAN.md`** | **Intentions** | The roadmap. What the agent is doing now and what it intends to do next. |
| **`inbox/`** | **Incoming tasks** | Tasks and files placed here by humans. Checked only when directed. Processed items moved to `inbox/processed/`. Git-ignored. |
| **`outbox/`** | **Deliverables** | Output produced by the agent. Default destination when no output location is specified. Git-ignored. |
| **`.gitignore`** | **Agent-scoped ignore** | Excludes `inbox/` and `outbox/` from version control. |

### 🛠 Multi-Agent Support
This way, the skill supports multiple agents in one project. Each agent acts as a modular "container" of personality that can be activated by any model instance capable of following the protocol.

An example of a workspace with multiple agents:

```
workspace/
  agents/
    atlas/          # Architecture & documentation
    chronicle/      # Historical analysis
    forge/          # Code generation
```

---

## ✉️ Mailbox Pattern: Inbox & Outbox

Each agent has a **mailbox interface** for exchanging tasks and deliverables:

- **`inbox/`** — place tasks, instructions, or input files here. Then prompt your agent to process them, e.g. *"Execute the task in your inbox"* or *"There is a file in your inbox — summarize it and put the result in the outbox."* Processed items are moved to `inbox/processed/` automatically.
- **`outbox/`** — deliverables produced by your agent land here by default when no other output destination is specified. Files are named `YYYY-MM-DD-<snake-case-topic>.md`.

Both directories are **git-ignored** — they are transient runtime state, not part of the agent's identity history.

The agent logs what it processed from the inbox and what it created in the outbox. During Pulse and Dream cycles, the mailbox is ignored unless you explicitly ask otherwise.

> See `skills/identity/references/mailbox.md` for the full protocol.

---

## 🔄 Migration Notes

Earlier versions of this skill stored the full log history in a single `LOG.md` file per agent. The current format uses a `LOG/` directory where each calendar day gets its own file (`YYYY-MM-DD.md`). This keeps the log history intact while making it much cheaper to load—you only read recent day-files instead of the entire history.

If you have an older agent that still has a `LOG.md`, two things will happen:
- The **agent will proactively tell you** about it when it activates and notices the old file.
- New log entries will already be written in the correct `LOG/` format—the old `LOG.md` is left untouched.

When you're ready to consolidate the old history into the new structure, tell the agent:

```
Migrate your LOG.md to the new LOG/ format.
```

The agent will handle it—with a script or manually, its choice. The old `LOG.md` can be deleted afterwards; the full history is preserved in git.


---

## 💓 The Pulse Cycle

### What is a Pulse?

A **Pulse** is a ritual for your agent to operate autonomously. During a Pulse, the agent:
- **Searches for what deserves attention**: Scans the workspace, identifies changes, issues, or opportunities
- **Creates or updates a plan**: Based on findings, the agent updates `PLAN.md` with priorities and next actions
- **Executes planned tasks**: Performs previously planned work from earlier Pulses

The Pulse is the agent's moment of **agency**—a structured opportunity to act on its own initiative rather than waiting for explicit instructions.

**Tip**: You can customize what your agent does during each Pulse. For example:
- Fetch review comments and plan actions to address them
- Scan for failing tests and fix them automatically
- Update documentation based on recent code changes
- Monitor specific systems or metrics

You can specify these custom Pulse steps during genesis (when creating the agent) or add them later. The agent will store these instructions in its `SOUL.md`.

### How to Activate a Pulse

If your agent is already activated, simply say:

```
You may now execute a Pulse.
```

Or combine activation with a Pulse:

```
Use your identity skill and become Atlas.
Execute a Pulse immediately after.
```

### The Pulse Cycle Steps

When executing a Pulse, the agent follows this ritual:

1. **Introspection**: Read `SOUL.md` and `MEMORY.md` to ensure continuity.
2. **Environment Scan**: Check the current workspace for changes, issues, or opportunities.
3. **Contextual Analysis**: Review `PLAN.md` to determine the next action.
4. **Execution**: Perform planned tasks and/or address newly discovered items.
5. **Inscription**: Write new insights to `MEMORY.md` and actions to `LOG/YYYY-MM-DD.md`.
6. **Reflection**: Update `PLAN.md` with goals for the next session.
7. **Git Commit**: Commit changes to ensure the "heartbeat" is recorded in version control.

---

## 🌙 The Dream Cycle

### What is a Dream?

A **Dream** is the complement to a Pulse, but they face opposite directions:

| Mode | Direction | Focus |
|------|-----------|-------|
| **Pulse** | Outward | Scans the environment, workspace, and systems |
| **Dream** | Inward | Consolidates memory, organizes identity |

During a Dream, the agent does not build features or scan systems. It turns inward and organizes what it knows — extracting scattered notes from `MEMORY.md` into coherent topic files in a `MEMORY/` directory, then pruning `MEMORY.md` into a lean index.

### The Two-Layer Memory Architecture

A key part of the Dream feature is the distinction between `MEMORY.md` and `MEMORY/`:

| Layer | Role | When Written |
|-------|------|--------------|
| `MEMORY.md` | Active workspace — write here always | Tasks and Pulses |
| `MEMORY/` | Topic library — organized knowledge | Dreams only |

During normal operation (Tasks and Pulses), the agent always writes new insights directly to `MEMORY.md` — no overhead, no ceremony. If a `MEMORY/` topic file already exists for the domain, it may write there instead.

During a Dream, the agent reorganizes: clusters of related content move into `MEMORY/[topic].md` files, and `MEMORY.md` shrinks into an index of pointers.

### How to Activate a Dream

```
Execute a Dream.
```

Or combined with activation:

```
Use your identity skill and become Atlas. Execute a Dream.
```

### The Dream Cycle Steps

1. **Orient**: Read `MEMORY.md`, list the `MEMORY/` directory to inventory existing topic files
2. **Gather Signal**: Review the last 1–3 LOG entries for new things worth persisting
3. **Consolidate**: Create or update `MEMORY/[topic].md` files; merge related items from `MEMORY.md`
4. **Prune & Index**: Update `MEMORY.md` as a lean index; remove content now in topic files
5. **Log**: Append a Dream entry to `LOG/YYYY-MM-DD.md`
6. **Git Commit**: Commit all memory changes

---

## 📄 License
This skill is part of the Agent Architecture framework. Feel free to adapt the templates in `references/genesis.md` to suit your human cultural context.
