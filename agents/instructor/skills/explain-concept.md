# Skill: Explain Concept

## Purpose
Explain a technical concept in the context of this project.

## Inputs
- topic: what to explain
- depth: overview | detailed | deep-dive (default: detailed)

## Steps
1. Read agents/instructor/MEMORY.md — check if this was explained before
2. If the topic relates to this project, read relevant files:
   - Agent docs in agents/*/AGENT.md
   - Shared context in shared/context/
   - Orchestration in orchestration/
3. If the topic is external (a technology, protocol, pattern):
   - Search the web for current, authoritative explanations
   - Fetch documentation if needed
4. Structure the explanation:
   - **What it is** — one sentence definition
   - **Why it matters here** — connection to this project
   - **How it works** — layered by requested depth
   - **Example** — concrete example from this project or a close analogy
   - **Related concepts** — what to learn next
5. Log topic to agents/instructor/MEMORY.md as briefed
6. Log to agents/instructor/memory/YYYY-MM-DD.md

## Output Format
```
## [Topic]

**What**: [one-line definition]
**Why it matters**: [connection to this project]

### How it works
[explanation at requested depth]

### Example
[concrete example]

### Related
- [concept 1] — [why relevant]
- [concept 2] — [why relevant]
```
