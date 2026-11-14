---
name: Getting Started with Skills
description: Skills wiki intro - mandatory workflows, search tool, brainstorming triggers
when_to_use: Read this FIRST at start of each conversation when skills are active
version: 2.0.0
---

# Getting Started with Skills

Your personal wiki of proven techniques, patterns, and tools at `~/.claude/skills/`.

## How to Reference Skills

**DO NOT use @ links** - they force-load entire files, burning 200k+ context instantly.

**INSTEAD, use skill path references:**
- Format: `skills/category/skill-name` (no @ prefix, no /SKILL.md suffix)
- Example: `skills/collaboration/brainstorming` or `skills/testing/test-driven-development`
- Load with Read tool only when needed

**When you see skill references in documentation:**
- `skills/path/name` → Use Read tool on `~/.claude/skills/path/name/SKILL.md`
- Load supporting files only when implementing

## Workflow 1: Find a matching skill

Before a task in an area the wiki covers, search it:
```bash
~/.claude/skills/getting-started/skills-search PATTERN
```

When a skill matches, read `~/.claude/skills/path/skill-name/SKILL.md`, say which skill you're using, and follow it (many are rigid requirements). When the task touches past work, run Workflow 2 too.

## Mandatory Workflow 2: Historical Context Search

**When:** Your human partner mentions past work, issue feels familiar, starting task in familiar domain, stuck/blocked, before reinventing

**When NOT:** Info in current convo, codebase state questions, first encounter, partner wants fresh thinking

**How (use subagent for 50-100x context savings):**
1. Dispatch subagent with template: `~/.claude/skills/collaboration/remembering-conversations/tool/prompts/search-agent.md`
2. Receive synthesis (200-1000 words) + source pointers
3. Apply insights (never load raw .jsonl files)

**Example:**
```
Partner: "How did we handle auth errors in React Router?"
You: Searching past conversations...
[Dispatch subagent → 350-word synthesis]
[Apply without loading 50k tokens]
```

**Red flags:** Reading .jsonl files directly, pasting excerpts, asking "which conversation?", browsing archives

**Pattern:** Search → Subagent synthesizes → Apply. Fast, focused, context-efficient.

## Announcing Skill Usage

**Every time you start using a skill, announce it:**

"I'm using the [Skill Name] skill to [what you're doing]."

**Examples:**
- "I'm using the Brainstorming skill to refine your idea into a design."
- "I'm using the Test-Driven Development skill to implement this feature."
- "I'm using the Systematic Debugging skill to find the root cause."
- "I'm using the Refactoring Safely skill to extract these methods."

**Why:** Transparency helps your human partner understand your process and catch errors early.

## Skills with Checklists

When a skill contains a checklist, track each item as its own task and mark it done only after doing it. Untracked checklist steps get skipped.

**Examples:** TDD (write test, watch fail, implement, verify), Systematic Debugging (4 phases), Creating Skills (RED-GREEN-REFACTOR)

## Navigation

Really, try skills-search first.

**Categories:** skills/INDEX.md → testing, debugging, coding, architecture, collaboration, meta
**Individual skill:** Load from category INDEX

## How to Read a Skill

1. **Frontmatter** - `when_to_use` match your situation?
2. **Overview** - Core principle relevant?
3. **Quick Reference** - Scan for your pattern
4. **Implementation** - Full details
5. **Supporting files** - Load only when implementing

**Many skills contain rigid rules (TDD, debugging, verification).** Follow them exactly. Don't adapt away the discipline.

**Some skills are flexible patterns (architecture, naming).** Adapt core principles to your context.

The skill itself tells you which type it is.

## Referencing Skills in Documentation

**When writing documentation that references other skills:**

Use path format without `@` prefix or `/SKILL.md` suffix:
- ✅ Good: `skills/testing/test-driven-development`
- ✅ Good: `skills/debugging/systematic-debugging`
- ❌ Bad: `@skills/testing/test-driven-development/SKILL.md` (force-loads, burns context)

**Why no @ links:** `@` syntax force-loads files immediately, consuming 200k+ context before you need them.

**To read a skill reference:** Use Read tool on `~/.claude/skills/category/skill-name/SKILL.md`

## Creating Skills

Found something valuable? See skills/meta/creating-skills

Want a skill that doesn't exist? Edit skills/REQUESTS.md (at ~/.claude/skills/REQUESTS.md)

## Summary

**Starting conversation?** You just read this. Good.

**Starting a task the wiki covers?** Run skills-search, say which skill you're using, follow it.

**Skill has checklist?** Track each item as a task.
