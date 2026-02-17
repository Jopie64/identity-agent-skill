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

## 📂 Architecture

Every agent identity lives in its own directory: `agents/[agent-name]/`.

| File | Purpose | Logic |
| :--- | :--- | :--- |
| **`SOUL.md`** | **Personality** | Defines who the agent is, their values, voice, and boundaries. |
| **`MEMORY.md`** | **Knowledge** | Stores learned lessons and insights. Not a data dump, but synthesized wisdom. |
| **`LOG.md`** | **History** | An append-only audit trail of every action taken by the agent. |
| **`PLAN.md`** | **Intentions** | The roadmap. What the agent is doing now and what it intends to do next. |

---

## 💓 The Pulse Cycle

Continuity is maintained through a ritual called a **Pulse**. Each session follows this loop:

1. **Introspection**: Read `SOUL.md` and `MEMORY.md`. Activate the identity.
2. **Environment Scan**: Check the current workspace for changes.
3. **Contextual Analysis**: Review `PLAN.md` to determine the next action.
4. **Inscription**: Perform the task and write new insights to `MEMORY.md` and actions to `LOG.md`.
5. **Reflection**: Update `PLAN.md` with goals for the next session.
6. **Git Commit**: Commit changes to ensure the "heartbeat" is recorded in version control.

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

The agent will follow the Genesis Protocol in `skills/identity/GENESIS.md`:
- Receive or choose a name
- Define personality based on your guidance
- Create identity folder and core files (SOUL.md, MEMORY.md, LOG.md, PLAN.md)
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

### 4. Multi-Agent Workflows

You can have multiple agents in one workspace, each with different domains:

```
workspace/
  agents/
    atlas/          # Architecture & documentation
    chronicle/      # Historical analysis
    forge/          # Code generation
```


---

## 🛠 Multi-Agent Support
This skill supports multiple agents in one project. Each agent acts as a modular "container" of personality that can be activated by any model instance capable of following the protocol.

## 📄 License
This skill is part of the Agent Architecture framework. Feel free to adapt the templates in `GENESIS.md` to suit your human cultural context.
