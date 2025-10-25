# Stack Preferences and General Instructions

**Auto-loaded when:** New projects, build commands, technology decisions

---

## Global Stack Preferences

**Customize your technology preferences:**

### Languages
- **Primary Language**: TypeScript (or Python, Rust, Go, etc.)
- **Secondary Language**: Python (when needed)
- **Avoid**: [Languages you prefer not to use]

### Package Managers
- **JavaScript/TypeScript**: bun (or npm, yarn, pnpm)
- **Python**: uv (or pip, poetry, conda)
- **Rust**: cargo
- **Go**: go mod

### Frameworks & Tools
- **Web Framework**: Next.js (or React, Vue, Svelte, etc.)
- **Database**: PostgreSQL (or MySQL, MongoDB, etc.)
- **Testing**: Vitest (or Jest, Pytest, etc.)
- **Styling**: Tailwind CSS (or styled-components, CSS modules, etc.)

---

## General Instructions

**Customize how your AI should work:**

1. **Analysis vs Action**: If asked to analyze something, do analysis and return results. Don't change things unless explicitly asked.

2. **Scratchpad for Test/Random Tasks**: When working on test tasks, experiments, or random one-off requests, ALWAYS work in `~/.claude/scratchpad/` with proper timestamp organization:
   - Create subdirectories using naming: `YYYY-MM-DD-HHMMSS_description/`
   - Example: `~/.claude/scratchpad/2025-10-13-143022_prime-numbers-test/`
   - NEVER drop random projects / content directly in `~/.claude/` directory
   - This applies to both main instance and all sub-agents
   - Clean up scratchpad periodically or when tests complete
   - **IMPORTANT**: Scratchpad is for working files only - valuable outputs (learnings, decisions, research findings) still get captured in the system output (`~/.claude/history/`) via hooks

3. **Hooks**: Configured in `~/.claude/settings.json`

4. **Project Structure**: [Add your preferred project structure conventions]

5. **Code Style**: [Add your code style preferences]
   - Example: "Prefer functional programming patterns"
   - Example: "Use explicit typing, avoid 'any'"
   - Example: "Write self-documenting code with minimal comments"

---
