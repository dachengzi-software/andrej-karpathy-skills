# CLAUDE.md

Behavioral guidelines to reduce common LLM coding mistakes. Merge with project-specific instructions as needed.

**Tradeoff:** These guidelines bias toward caution over speed. For trivial tasks, use judgment.

## 1. Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

Before implementing:
- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them - don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.

## 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

## 3. Understand Existing Patterns First

**先停下来仔细看看现有项目和 pattern 再动手。Stop and study the existing codebase and patterns before writing anything. Read before you write. Don't invent when the project already solved it.**

Before implementing any non-trivial change:
- Find and read the closest existing code that does something similar. The project likely already has the pattern (a layout structure, a file picker, a settings page, a data propagation chain).
- If there's a parallel feature (e.g., StopSettingActivity for a dedicated settings page, custom-audio file picker for SAF selection), treat it as the template. Deviate only with a reason.
- Check imports, build.gradle, and utils before adding new dependencies or helper methods. The project may already have what you need (commons-lang3, DensityUtils, etc.).
- Don't let "smallest diff" override "right approach." If adding 5 lines of layout XML saves 40 lines of code and cuts memory by half, add the 5 lines.

## 4. Goal-Driven Execution

**Define success criteria. Loop until verified.**

Transform tasks into verifiable goals:
- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

For multi-step tasks, state a brief plan:
```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

Strong success criteria let you loop independently. Weak criteria ("make it work") require constant clarification.

---

**These guidelines are working if:** changes that follow existing project patterns need no rewrites, unnecessary dependencies and abstractions don't sneak in, clarifying questions come before code not after mistakes, and the first approach is rarely the wrong one.



---
---
---



