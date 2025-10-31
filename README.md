# PAI - Personal AI Infrastructure Plugin

> **🔗 This is the Claude Code plugin version of [PAI (Personal AI Infrastructure)](https://github.com/danielmiessler/PAI)**
>
> For full documentation, architecture details, and the complete PAI system, visit the [main PAI repository](https://github.com/danielmiessler/PAI).

Transform Claude Code into your Personal AI Infrastructure with skills, agents, and automation workflows.

## What is Claude Code?

[Claude Code](https://claude.ai/code) is Anthropic's official AI-powered coding assistant CLI. It's like having an expert developer pair with you in your terminal.

This PAI plugin extends Claude Code with specialized skills, agents, and workflows for research, development, security testing, and more.

**New to Claude Code?**
- **Get Claude Code**: https://claude.ai/code
- **Documentation**: https://docs.claude.com/en/docs/claude-code
- **Requirements**: Claude Code v2.0.12+ (plugin system support)






## 📢 Recent PAI Updates

> **🔗 This plugin tracks the main [PAI (Personal AI Infrastructure)](https://github.com/danielmiessler/PAI) project.**
>
> Below are the latest updates from the PAI repository. For complete details, see the [full PAI README](./docs/PAI-README.md).

## 🚀 **Recent Updates**

> [!IMPORTANT]
> **🔥 v0.6.0 MAJOR UPGRADE:** Repository completely restructured with `.claude/` directory!
>
> **BREAKING CHANGE - Repository Structure Changed:**
> - All PAI infrastructure now lives in `.claude/` directory
> - Repository now properly mirrors your actual `~/.claude/` working system
> - Fixes major compatibility issues reported by users
> - **Action Required:** New installations should copy `.claude/` to `~/.claude/`
>
> [See full changelog below →](#-recent-updates)

<details>
<summary><strong>📅 Click to see all updates</strong></summary>

### Recent Manual Updates

- **✨ Oct 31:** v1.2.0 - Skills-as-Containers Migration - Complete architectural upgrade
- **✨ Oct 19:** Session-start hook now loads PAI skill - improved Skills system bootstrap
- **✨ Oct 18:** Major repo cleanup - fixed missing files, hooks, settings
- **✨ v0.5.0:** Skills-based architecture with 92.5% token reduction

### Automated Documentation Updates

<details>
<summary>📅 2025-10-20 - Settings: 1 updated</summary>

*Updated by pre-commit hook: 1 modified*
</details>

<details>
<summary>📅 2025-10-19 - Voice: 2 updated</summary>

*Updated by pre-commit hook: 3 modified*
</details>

<details>
<summary>📅 2025-10-19 - Skills: 1 updated, 5 removed</summary>

*Updated by pre-commit hook: 1 modified, 5 deleted*
</details>

<details>
<summary>📅 2025-10-19 - Hooks: 2 new, 1 removed, Settings: 1 updated</summary>

*Updated by pre-commit hook: 3 added, 1 modified, 1 deleted*
</details>

---

### Version History

<details>
<summary><strong>📅 v1.2.0 - Skills-as-Containers Migration 🔥 ARCHITECTURAL UPGRADE</strong></summary>

**The Problem:**
Commands were scattered in a flat global namespace (`~/.claude/commands/`), making it hard to discover related functionality, maintain consistency, and understand domain boundaries. The architecture needed hierarchical organization that matched how capabilities are naturally grouped.

**The Solution:**
Complete migration to Skills-as-Containers pattern:
- Moved 73 commands into skill-specific `workflows/` subdirectories
- Enhanced 21 skills with proper workflow organization
- Established deprecation pattern for future architectural upgrades
- Documented the complete migration process

**What Changed:**
```
Before (v0.6.0):
~/.claude/
├── commands/
│   ├── write-blog.md
│   ├── publish-blog.md
│   ├── quick-research.md
│   ├── extensive-research.md
│   └── [75+ scattered commands]
└── skills/
    ├── blogging/SKILL.md
    └── research/SKILL.md

After (v1.2.0):
~/.claude/
├── commands/               # Empty (commands moved to skills)
└── skills/
    ├── blogging/
    │   ├── SKILL.md
    │   └── workflows/
    │       ├── write.md
    │       └── publish.md
    └── research/
        ├── SKILL.md
        └── workflows/
            ├── quick.md
            └── extensive.md
```

**Architecture Benefits:**
- ✅ Domain knowledge colocated with workflows
- ✅ Clear ownership and responsibility
- ✅ Natural language routing: Skills → Workflows
- ✅ Easier discovery of related capabilities
- ✅ Better encapsulation of domain context

**Migration Stats:**
- 73 commands migrated to skill workflows
- 21 skills enhanced with workflows/ directories
- 1 new skill created (content-enhancement)
- Commands directory reduced from 75 files to 0
- Zero errors, 100% QA pass rate
- Complete in ~25 minutes using parallel agents

**Documentation:**
- See `docs/ARCHITECTURE.md` for Skills-as-Containers pattern
- Deprecation pattern established in `history/upgrades/deprecated/`
- Complete migration audit trail preserved

</details>

<details>
<summary><strong>📅 v0.6.0 - Repository Restructure with .claude/ Directory 🔥 MAJOR UPDATE</strong></summary>

**The Problem:**
Users reported issues with PAI not working correctly because the repository structure didn't match the actual working system. The real PAI system expects all infrastructure to live in `~/.claude/`, but the repo had everything at root level. This caused confusion and compatibility problems.

**The Solution:**
Complete repository restructure to mirror the actual working system:
- Created `.claude/` directory at repository root
- Moved ALL PAI infrastructure into `.claude/` (agents, commands, documentation, hooks, skills, voice-server, etc.)
- Kept GitHub infrastructure at root (README, LICENSE, .gitignore, .github, etc.)
- Repository now serves as a true reference implementation

**What Changed:**
```
Before (v0.5.0):
/PAI/
├── agents/
├── commands/
├── documentation/
├── hooks/
├── skills/
├── voice-server/
├── settings.json
├── .mcp.json
├── setup.sh
└── README.md

After (v0.6.0):
/PAI/
├── .claude/                 # ← NEW: All PAI infrastructure here
│   ├── agents/
│   ├── commands/
│   ├── documentation/
│   ├── hooks/
│   ├── skills/
│   ├── voice-server/
│   ├── settings.json
│   ├── .mcp.json
│   └── setup.sh
├── README.md               # GitHub infrastructure stays at root
├── LICENSE
└── .gitignore
```

**Why This Matters:**
1. **Proper Emulation:** Repository now accurately represents how PAI works in production
2. **Easier Setup:** Users can see exactly how their `~/.claude/` directory should be structured
3. **Less Confusion:** Clear separation between GitHub files and PAI infrastructure
4. **Better Documentation:** Structure itself serves as documentation
5. **Reference Implementation:** Can be copied/referenced directly for setup

**Migration:**
- No action required for existing installations
- New users get the correct structure from the start
- All documentation updated to reflect new paths

**Rationale:**
The PAI system is designed to live in `~/.claude/` on your system. By organizing the repository to mirror this structure, we make it immediately clear how PAI should be set up. This is especially important for new users who are trying to understand the system architecture and for contributors who need to know where files belong.

</details>

<details>
<summary><strong>📅 v0.5.0 - Skills-Based PAI Architecture (92.5% Token Reduction)</strong></summary>

**Major Architectural Improvement:**
- **Zero hook overhead** - Eliminated all context loading from UserPromptSubmit hook
- **92.5% token reduction** - From 4000 tokens/interaction to 300 tokens
- **Pure skills architecture** - Core identity in skill description (always in system prompt)
- **On-demand context** - Full context loaded only when explicitly needed

**What Changed:**
- Added YAML frontmatter to `skills/PAI/SKILL.md` with comprehensive system description
- Core identity + critical security now in skill description (always present)
- Removed `MINIMAL.md` entirely (no longer needed)
- Hook renamed to `update-tab-titles.ts` (only handles tab titles, zero context)
- Flat file structure in `skills/PAI/` (no `/contexts` subdirectory)

**Architecture:**
- **Tier 1 (Always On):** Skill description in system prompt (~300 tokens) - identity, critical security, architecture explanation
- **Tier 2 (On Demand):** `SKILL.md` body loaded when PAI skill invoked (~4000 tokens) - contacts, preferences, voice IDs, detailed security
- **Hook:** Only updates tab titles (0 tokens context overhead)

**Benefits:**
- Cleanest possible architecture - fully embraces Claude Code skills system
- Context always relevant - skill description always present, full context on-demand
- Easy to customize - clear YAML frontmatter with `[CUSTOMIZE:]` markers
- Scales efficiently - adding content doesn't multiply token costs

**Files:**
- `skills/PAI/SKILL.md` - Full context with YAML frontmatter
- `skills/PAI/contacts.md` - Contact templates
- `skills/PAI/preferences.md` - Stack preferences templates
- `skills/PAI/response-format.md` - Response format templates
- `skills/PAI/security-detailed.md` - Security procedures
- `skills/PAI/voice-ids.md` - Voice system configuration (optional)
- `hooks/update-tab-titles.ts` - Tab title updates only

</details>

<details>
<summary><strong>📅 v0.4.0 - Repository Restructure 🔥 BREAKING CHANGE</strong></summary>

**⚠️ Breaking Changes:**
- PAI_DIR environment variable: Change from `/path/to/PAI/PAI_DIRECTORY` to `/path/to/PAI`
- Repository renamed: `PAI` → `Personal_AI_Infrastructure`

**What Changed:**
- Moved all `PAI_DIRECTORY/` contents to repository root (agents/, skills/, commands/, etc.)
- Repository renamed for clarity and better SEO
- All functional directories now immediately visible on GitHub
- GitHub automatically redirects old URLs to new

**Migration:**
1. Update PAI_DIR: `export PAI_DIR="/path/to/PAI"` (remove `/PAI_DIRECTORY`)
2. Reload shell: `source ~/.zshrc`
3. Pull latest: `git pull`
4. Update remote: `git remote set-url origin git@github.com:danielmiessler/Personal_AI_Infrastructure.git`

</details>

<details>
<summary><strong>📅 v0.3.2 - Fabric Skill with Intelligent Pattern Selection</strong></summary>

Fabric skill now intelligently selects the right pattern from 242+ options based on user intent. Complete Fabric repository bundled locally. Categories: Security (15), Summarization (20), Extraction (30+), Analysis (35+), Creation (50+), Improvement (10), Rating (8).

</details>

<details>
<summary><strong>📅 v0.3.1 - Research Skills & API Key Infrastructure</strong></summary>

Multi-source research with parallel agent execution. New skills: `alex-hormozi-pitch`, `research`. New agents: `perplexity-researcher`, `claude-researcher`, `gemini-researcher`. Added `.env.example` with API key documentation.

</details>

<details>
<summary><strong>📅 v0.3.0 - Skills System Migration</strong></summary>

Migrated to [Anthropic's Skills architecture](https://www.anthropic.com/news/skills). Modular skill packages with progressive disclosure. Context system → Skills system. See [documentation](./documentation/skills-system.md) for details.

</details>

<details>
<summary><strong>📅 v0.2.4 - README Cleanup</strong></summary>

Collapsed updates section, reduced visual clutter, optimized space.

</details>

<details>
<summary><strong>📅 v0.2.3 - Visibility & Portability</strong></summary>

`.claude` → `PAI_DIRECTORY`, vendor agnostic, dynamic paths with `${PAI_DIR}`, full portability.

</details>

<details>
<summary><strong>📅 v0.2.2 - Voice System</strong></summary>

Migrated to macOS native Premium voices (zero cost, offline, private).

</details>

<details>
<summary><strong>📅 v0.2.0 - v0.1.0 - Initial Releases</strong></summary>

Public release with voice server, PAI_HOME support, comprehensive documentation, MCP detection, hooks system.

</details>

<details>
<summary><strong>📅 Previous Updates</strong></summary>

**September 20, 2025**
- 🗣️ Added `/voice-server` with ElevenLabs integration
- 🔧 Fixed hardcoded path issues
- 🪝 Working on missing hooks

**September 12, 2025**
- 🧠 Dynamic resource loading system
- ⚡ Submit-user-hook for context loading
- 🗺️ Dynamic routing via load-dynamic-requirements

</details>

</details>

---


---

## 🚀 **Recent Updates**

> [!IMPORTANT]
> **🔥 v0.6.0 MAJOR UPGRADE:** Repository completely restructured with `.claude/` directory!
>
> **BREAKING CHANGE - Repository Structure Changed:**
> - All PAI infrastructure now lives in `.claude/` directory
> - Repository now properly mirrors your actual `~/.claude/` working system
> - Fixes major compatibility issues reported by users
> - **Action Required:** New installations should copy `.claude/` to `~/.claude/`
>
> [See full changelog below →](#-recent-updates)

<details>
<summary><strong>📅 Click to see all updates</strong></summary>

### Recent Manual Updates

- **✨ Oct 31:** v1.2.0 - Skills-as-Containers Migration - Complete architectural upgrade
- **✨ Oct 19:** Session-start hook now loads PAI skill - improved Skills system bootstrap
- **✨ Oct 18:** Major repo cleanup - fixed missing files, hooks, settings
- **✨ v0.5.0:** Skills-based architecture with 92.5% token reduction

### Automated Documentation Updates

<details>
<summary>📅 2025-10-20 - Settings: 1 updated</summary>

*Updated by pre-commit hook: 1 modified*
</details>

<details>
<summary>📅 2025-10-19 - Voice: 2 updated</summary>

*Updated by pre-commit hook: 3 modified*
</details>

<details>
<summary>📅 2025-10-19 - Skills: 1 updated, 5 removed</summary>

*Updated by pre-commit hook: 1 modified, 5 deleted*
</details>

<details>
<summary>📅 2025-10-19 - Hooks: 2 new, 1 removed, Settings: 1 updated</summary>

*Updated by pre-commit hook: 3 added, 1 modified, 1 deleted*
</details>

---

### Version History

<details>
<summary><strong>📅 v1.2.0 - Skills-as-Containers Migration 🔥 ARCHITECTURAL UPGRADE</strong></summary>

**The Problem:**
Commands were scattered in a flat global namespace (`~/.claude/commands/`), making it hard to discover related functionality, maintain consistency, and understand domain boundaries. The architecture needed hierarchical organization that matched how capabilities are naturally grouped.

**The Solution:**
Complete migration to Skills-as-Containers pattern:
- Moved 73 commands into skill-specific `workflows/` subdirectories
- Enhanced 21 skills with proper workflow organization
- Established deprecation pattern for future architectural upgrades
- Documented the complete migration process

**What Changed:**
```
Before (v0.6.0):
~/.claude/
├── commands/
│   ├── write-blog.md
│   ├── publish-blog.md
│   ├── quick-research.md
│   ├── extensive-research.md
│   └── [75+ scattered commands]
└── skills/
    ├── blogging/SKILL.md
    └── research/SKILL.md

After (v1.2.0):
~/.claude/
├── commands/               # Empty (commands moved to skills)
└── skills/
    ├── blogging/
    │   ├── SKILL.md
    │   └── workflows/
    │       ├── write.md
    │       └── publish.md
    └── research/
        ├── SKILL.md
        └── workflows/
            ├── quick.md
            └── extensive.md
```

**Architecture Benefits:**
- ✅ Domain knowledge colocated with workflows
- ✅ Clear ownership and responsibility
- ✅ Natural language routing: Skills → Workflows
- ✅ Easier discovery of related capabilities
- ✅ Better encapsulation of domain context

**Migration Stats:**
- 73 commands migrated to skill workflows
- 21 skills enhanced with workflows/ directories
- 1 new skill created (content-enhancement)
- Commands directory reduced from 75 files to 0
- Zero errors, 100% QA pass rate
- Complete in ~25 minutes using parallel agents

**Documentation:**
- See `docs/ARCHITECTURE.md` for Skills-as-Containers pattern
- Deprecation pattern established in `history/upgrades/deprecated/`
- Complete migration audit trail preserved

</details>

<details>
<summary><strong>📅 v0.6.0 - Repository Restructure with .claude/ Directory 🔥 MAJOR UPDATE</strong></summary>

**The Problem:**
Users reported issues with PAI not working correctly because the repository structure didn't match the actual working system. The real PAI system expects all infrastructure to live in `~/.claude/`, but the repo had everything at root level. This caused confusion and compatibility problems.

**The Solution:**
Complete repository restructure to mirror the actual working system:
- Created `.claude/` directory at repository root
- Moved ALL PAI infrastructure into `.claude/` (agents, commands, documentation, hooks, skills, voice-server, etc.)
- Kept GitHub infrastructure at root (README, LICENSE, .gitignore, .github, etc.)
- Repository now serves as a true reference implementation

**What Changed:**
```
Before (v0.5.0):
/PAI/
├── agents/
├── commands/
├── documentation/
├── hooks/
├── skills/
├── voice-server/
├── settings.json
├── .mcp.json
├── setup.sh
└── README.md

After (v0.6.0):
/PAI/
├── .claude/                 # ← NEW: All PAI infrastructure here
│   ├── agents/
│   ├── commands/
│   ├── documentation/
│   ├── hooks/
│   ├── skills/
│   ├── voice-server/
│   ├── settings.json
│   ├── .mcp.json
│   └── setup.sh
├── README.md               # GitHub infrastructure stays at root
├── LICENSE
└── .gitignore
```

**Why This Matters:**
1. **Proper Emulation:** Repository now accurately represents how PAI works in production
2. **Easier Setup:** Users can see exactly how their `~/.claude/` directory should be structured
3. **Less Confusion:** Clear separation between GitHub files and PAI infrastructure
4. **Better Documentation:** Structure itself serves as documentation
5. **Reference Implementation:** Can be copied/referenced directly for setup

**Migration:**
- No action required for existing installations
- New users get the correct structure from the start
- All documentation updated to reflect new paths

**Rationale:**
The PAI system is designed to live in `~/.claude/` on your system. By organizing the repository to mirror this structure, we make it immediately clear how PAI should be set up. This is especially important for new users who are trying to understand the system architecture and for contributors who need to know where files belong.

</details>

<details>
<summary><strong>📅 v0.5.0 - Skills-Based PAI Architecture (92.5% Token Reduction)</strong></summary>

**Major Architectural Improvement:**
- **Zero hook overhead** - Eliminated all context loading from UserPromptSubmit hook
- **92.5% token reduction** - From 4000 tokens/interaction to 300 tokens
- **Pure skills architecture** - Core identity in skill description (always in system prompt)
- **On-demand context** - Full context loaded only when explicitly needed

**What Changed:**
- Added YAML frontmatter to `skills/PAI/SKILL.md` with comprehensive system description
- Core identity + critical security now in skill description (always present)
- Removed `MINIMAL.md` entirely (no longer needed)
- Hook renamed to `update-tab-titles.ts` (only handles tab titles, zero context)
- Flat file structure in `skills/PAI/` (no `/contexts` subdirectory)

**Architecture:**
- **Tier 1 (Always On):** Skill description in system prompt (~300 tokens) - identity, critical security, architecture explanation
- **Tier 2 (On Demand):** `SKILL.md` body loaded when PAI skill invoked (~4000 tokens) - contacts, preferences, voice IDs, detailed security
- **Hook:** Only updates tab titles (0 tokens context overhead)

**Benefits:**
- Cleanest possible architecture - fully embraces Claude Code skills system
- Context always relevant - skill description always present, full context on-demand
- Easy to customize - clear YAML frontmatter with `[CUSTOMIZE:]` markers
- Scales efficiently - adding content doesn't multiply token costs

**Files:**
- `skills/PAI/SKILL.md` - Full context with YAML frontmatter
- `skills/PAI/contacts.md` - Contact templates
- `skills/PAI/preferences.md` - Stack preferences templates
- `skills/PAI/response-format.md` - Response format templates
- `skills/PAI/security-detailed.md` - Security procedures
- `skills/PAI/voice-ids.md` - Voice system configuration (optional)
- `hooks/update-tab-titles.ts` - Tab title updates only

</details>

<details>
<summary><strong>📅 v0.4.0 - Repository Restructure 🔥 BREAKING CHANGE</strong></summary>

**⚠️ Breaking Changes:**
- PAI_DIR environment variable: Change from `/path/to/PAI/PAI_DIRECTORY` to `/path/to/PAI`
- Repository renamed: `PAI` → `Personal_AI_Infrastructure`

**What Changed:**
- Moved all `PAI_DIRECTORY/` contents to repository root (agents/, skills/, commands/, etc.)
- Repository renamed for clarity and better SEO
- All functional directories now immediately visible on GitHub
- GitHub automatically redirects old URLs to new

**Migration:**
1. Update PAI_DIR: `export PAI_DIR="/path/to/PAI"` (remove `/PAI_DIRECTORY`)
2. Reload shell: `source ~/.zshrc`
3. Pull latest: `git pull`
4. Update remote: `git remote set-url origin git@github.com:danielmiessler/Personal_AI_Infrastructure.git`

</details>

<details>
<summary><strong>📅 v0.3.2 - Fabric Skill with Intelligent Pattern Selection</strong></summary>

Fabric skill now intelligently selects the right pattern from 242+ options based on user intent. Complete Fabric repository bundled locally. Categories: Security (15), Summarization (20), Extraction (30+), Analysis (35+), Creation (50+), Improvement (10), Rating (8).

</details>

<details>
<summary><strong>📅 v0.3.1 - Research Skills & API Key Infrastructure</strong></summary>

Multi-source research with parallel agent execution. New skills: `alex-hormozi-pitch`, `research`. New agents: `perplexity-researcher`, `claude-researcher`, `gemini-researcher`. Added `.env.example` with API key documentation.

</details>

<details>
<summary><strong>📅 v0.3.0 - Skills System Migration</strong></summary>

Migrated to [Anthropic's Skills architecture](https://www.anthropic.com/news/skills). Modular skill packages with progressive disclosure. Context system → Skills system. See [documentation](./documentation/skills-system.md) for details.

</details>

<details>
<summary><strong>📅 v0.2.4 - README Cleanup</strong></summary>

Collapsed updates section, reduced visual clutter, optimized space.

</details>

<details>
<summary><strong>📅 v0.2.3 - Visibility & Portability</strong></summary>

`.claude` → `PAI_DIRECTORY`, vendor agnostic, dynamic paths with `${PAI_DIR}`, full portability.

</details>

<details>
<summary><strong>📅 v0.2.2 - Voice System</strong></summary>

Migrated to macOS native Premium voices (zero cost, offline, private).

</details>

<details>
<summary><strong>📅 v0.2.0 - v0.1.0 - Initial Releases</strong></summary>

Public release with voice server, PAI_HOME support, comprehensive documentation, MCP detection, hooks system.

</details>

<details>
<summary><strong>📅 Previous Updates</strong></summary>

**September 20, 2025**
- 🗣️ Added `/voice-server` with ElevenLabs integration
- 🔧 Fixed hardcoded path issues
- 🪝 Working on missing hooks

**September 12, 2025**
- 🧠 Dynamic resource loading system
- ⚡ Submit-user-hook for context loading
- 🗺️ Dynamic routing via load-dynamic-requirements

</details>

</details>

---


---

## 🚀 **Recent Updates**

> [!IMPORTANT]
> **🔥 v0.6.0 MAJOR UPGRADE:** Repository completely restructured with `.claude/` directory!
>
> **BREAKING CHANGE - Repository Structure Changed:**
> - All PAI infrastructure now lives in `.claude/` directory
> - Repository now properly mirrors your actual `~/.claude/` working system
> - Fixes major compatibility issues reported by users
> - **Action Required:** New installations should copy `.claude/` to `~/.claude/`
>
> [See full changelog below →](#-recent-updates)

<details>
<summary><strong>📅 Click to see all updates</strong></summary>

### Recent Manual Updates

- **✨ Oct 31:** v1.2.0 - Skills-as-Containers Migration - Complete architectural upgrade
- **✨ Oct 19:** Session-start hook now loads PAI skill - improved Skills system bootstrap
- **✨ Oct 18:** Major repo cleanup - fixed missing files, hooks, settings
- **✨ v0.5.0:** Skills-based architecture with 92.5% token reduction

### Automated Documentation Updates

<details>
<summary>📅 2025-10-20 - Settings: 1 updated</summary>

*Updated by pre-commit hook: 1 modified*
</details>

<details>
<summary>📅 2025-10-19 - Voice: 2 updated</summary>

*Updated by pre-commit hook: 3 modified*
</details>

<details>
<summary>📅 2025-10-19 - Skills: 1 updated, 5 removed</summary>

*Updated by pre-commit hook: 1 modified, 5 deleted*
</details>

<details>
<summary>📅 2025-10-19 - Hooks: 2 new, 1 removed, Settings: 1 updated</summary>

*Updated by pre-commit hook: 3 added, 1 modified, 1 deleted*
</details>

---

### Version History

<details>
<summary><strong>📅 v1.2.0 - Skills-as-Containers Migration 🔥 ARCHITECTURAL UPGRADE</strong></summary>

**The Problem:**
Commands were scattered in a flat global namespace (`~/.claude/commands/`), making it hard to discover related functionality, maintain consistency, and understand domain boundaries. The architecture needed hierarchical organization that matched how capabilities are naturally grouped.

**The Solution:**
Complete migration to Skills-as-Containers pattern:
- Moved 73 commands into skill-specific `workflows/` subdirectories
- Enhanced 21 skills with proper workflow organization
- Established deprecation pattern for future architectural upgrades
- Documented the complete migration process

**What Changed:**
```
Before (v0.6.0):
~/.claude/
├── commands/
│   ├── write-blog.md
│   ├── publish-blog.md
│   ├── quick-research.md
│   ├── extensive-research.md
│   └── [75+ scattered commands]
└── skills/
    ├── blogging/SKILL.md
    └── research/SKILL.md

After (v1.2.0):
~/.claude/
├── commands/               # Empty (commands moved to skills)
└── skills/
    ├── blogging/
    │   ├── SKILL.md
    │   └── workflows/
    │       ├── write.md
    │       └── publish.md
    └── research/
        ├── SKILL.md
        └── workflows/
            ├── quick.md
            └── extensive.md
```

**Architecture Benefits:**
- ✅ Domain knowledge colocated with workflows
- ✅ Clear ownership and responsibility
- ✅ Natural language routing: Skills → Workflows
- ✅ Easier discovery of related capabilities
- ✅ Better encapsulation of domain context

**Migration Stats:**
- 73 commands migrated to skill workflows
- 21 skills enhanced with workflows/ directories
- 1 new skill created (content-enhancement)
- Commands directory reduced from 75 files to 0
- Zero errors, 100% QA pass rate
- Complete in ~25 minutes using parallel agents

**Documentation:**
- See `docs/ARCHITECTURE.md` for Skills-as-Containers pattern
- Deprecation pattern established in `history/upgrades/deprecated/`
- Complete migration audit trail preserved

</details>

<details>
<summary><strong>📅 v0.6.0 - Repository Restructure with .claude/ Directory 🔥 MAJOR UPDATE</strong></summary>

**The Problem:**
Users reported issues with PAI not working correctly because the repository structure didn't match the actual working system. The real PAI system expects all infrastructure to live in `~/.claude/`, but the repo had everything at root level. This caused confusion and compatibility problems.

**The Solution:**
Complete repository restructure to mirror the actual working system:
- Created `.claude/` directory at repository root
- Moved ALL PAI infrastructure into `.claude/` (agents, commands, documentation, hooks, skills, voice-server, etc.)
- Kept GitHub infrastructure at root (README, LICENSE, .gitignore, .github, etc.)
- Repository now serves as a true reference implementation

**What Changed:**
```
Before (v0.5.0):
/PAI/
├── agents/
├── commands/
├── documentation/
├── hooks/
├── skills/
├── voice-server/
├── settings.json
├── .mcp.json
├── setup.sh
└── README.md

After (v0.6.0):
/PAI/
├── .claude/                 # ← NEW: All PAI infrastructure here
│   ├── agents/
│   ├── commands/
│   ├── documentation/
│   ├── hooks/
│   ├── skills/
│   ├── voice-server/
│   ├── settings.json
│   ├── .mcp.json
│   └── setup.sh
├── README.md               # GitHub infrastructure stays at root
├── LICENSE
└── .gitignore
```

**Why This Matters:**
1. **Proper Emulation:** Repository now accurately represents how PAI works in production
2. **Easier Setup:** Users can see exactly how their `~/.claude/` directory should be structured
3. **Less Confusion:** Clear separation between GitHub files and PAI infrastructure
4. **Better Documentation:** Structure itself serves as documentation
5. **Reference Implementation:** Can be copied/referenced directly for setup

**Migration:**
- No action required for existing installations
- New users get the correct structure from the start
- All documentation updated to reflect new paths

**Rationale:**
The PAI system is designed to live in `~/.claude/` on your system. By organizing the repository to mirror this structure, we make it immediately clear how PAI should be set up. This is especially important for new users who are trying to understand the system architecture and for contributors who need to know where files belong.

</details>

<details>
<summary><strong>📅 v0.5.0 - Skills-Based PAI Architecture (92.5% Token Reduction)</strong></summary>

**Major Architectural Improvement:**
- **Zero hook overhead** - Eliminated all context loading from UserPromptSubmit hook
- **92.5% token reduction** - From 4000 tokens/interaction to 300 tokens
- **Pure skills architecture** - Core identity in skill description (always in system prompt)
- **On-demand context** - Full context loaded only when explicitly needed

**What Changed:**
- Added YAML frontmatter to `skills/PAI/SKILL.md` with comprehensive system description
- Core identity + critical security now in skill description (always present)
- Removed `MINIMAL.md` entirely (no longer needed)
- Hook renamed to `update-tab-titles.ts` (only handles tab titles, zero context)
- Flat file structure in `skills/PAI/` (no `/contexts` subdirectory)

**Architecture:**
- **Tier 1 (Always On):** Skill description in system prompt (~300 tokens) - identity, critical security, architecture explanation
- **Tier 2 (On Demand):** `SKILL.md` body loaded when PAI skill invoked (~4000 tokens) - contacts, preferences, voice IDs, detailed security
- **Hook:** Only updates tab titles (0 tokens context overhead)

**Benefits:**
- Cleanest possible architecture - fully embraces Claude Code skills system
- Context always relevant - skill description always present, full context on-demand
- Easy to customize - clear YAML frontmatter with `[CUSTOMIZE:]` markers
- Scales efficiently - adding content doesn't multiply token costs

**Files:**
- `skills/PAI/SKILL.md` - Full context with YAML frontmatter
- `skills/PAI/contacts.md` - Contact templates
- `skills/PAI/preferences.md` - Stack preferences templates
- `skills/PAI/response-format.md` - Response format templates
- `skills/PAI/security-detailed.md` - Security procedures
- `skills/PAI/voice-ids.md` - Voice system configuration (optional)
- `hooks/update-tab-titles.ts` - Tab title updates only

</details>

<details>
<summary><strong>📅 v0.4.0 - Repository Restructure 🔥 BREAKING CHANGE</strong></summary>

**⚠️ Breaking Changes:**
- PAI_DIR environment variable: Change from `/path/to/PAI/PAI_DIRECTORY` to `/path/to/PAI`
- Repository renamed: `PAI` → `Personal_AI_Infrastructure`

**What Changed:**
- Moved all `PAI_DIRECTORY/` contents to repository root (agents/, skills/, commands/, etc.)
- Repository renamed for clarity and better SEO
- All functional directories now immediately visible on GitHub
- GitHub automatically redirects old URLs to new

**Migration:**
1. Update PAI_DIR: `export PAI_DIR="/path/to/PAI"` (remove `/PAI_DIRECTORY`)
2. Reload shell: `source ~/.zshrc`
3. Pull latest: `git pull`
4. Update remote: `git remote set-url origin git@github.com:danielmiessler/Personal_AI_Infrastructure.git`

</details>

<details>
<summary><strong>📅 v0.3.2 - Fabric Skill with Intelligent Pattern Selection</strong></summary>

Fabric skill now intelligently selects the right pattern from 242+ options based on user intent. Complete Fabric repository bundled locally. Categories: Security (15), Summarization (20), Extraction (30+), Analysis (35+), Creation (50+), Improvement (10), Rating (8).

</details>

<details>
<summary><strong>📅 v0.3.1 - Research Skills & API Key Infrastructure</strong></summary>

Multi-source research with parallel agent execution. New skills: `alex-hormozi-pitch`, `research`. New agents: `perplexity-researcher`, `claude-researcher`, `gemini-researcher`. Added `.env.example` with API key documentation.

</details>

<details>
<summary><strong>📅 v0.3.0 - Skills System Migration</strong></summary>

Migrated to [Anthropic's Skills architecture](https://www.anthropic.com/news/skills). Modular skill packages with progressive disclosure. Context system → Skills system. See [documentation](./documentation/skills-system.md) for details.

</details>

<details>
<summary><strong>📅 v0.2.4 - README Cleanup</strong></summary>

Collapsed updates section, reduced visual clutter, optimized space.

</details>

<details>
<summary><strong>📅 v0.2.3 - Visibility & Portability</strong></summary>

`.claude` → `PAI_DIRECTORY`, vendor agnostic, dynamic paths with `${PAI_DIR}`, full portability.

</details>

<details>
<summary><strong>📅 v0.2.2 - Voice System</strong></summary>

Migrated to macOS native Premium voices (zero cost, offline, private).

</details>

<details>
<summary><strong>📅 v0.2.0 - v0.1.0 - Initial Releases</strong></summary>

Public release with voice server, PAI_HOME support, comprehensive documentation, MCP detection, hooks system.

</details>

<details>
<summary><strong>📅 Previous Updates</strong></summary>

**September 20, 2025**
- 🗣️ Added `/voice-server` with ElevenLabs integration
- 🔧 Fixed hardcoded path issues
- 🪝 Working on missing hooks

**September 12, 2025**
- 🧠 Dynamic resource loading system
- ⚡ Submit-user-hook for context loading
- 🗺️ Dynamic routing via load-dynamic-requirements

</details>

</details>

---


---

## 🚀 **Recent Updates**

> [!IMPORTANT]
> **🔥 v0.6.0 MAJOR UPGRADE:** Repository completely restructured with `.claude/` directory!
>
> **BREAKING CHANGE - Repository Structure Changed:**
> - All PAI infrastructure now lives in `.claude/` directory
> - Repository now properly mirrors your actual `~/.claude/` working system
> - Fixes major compatibility issues reported by users
> - **Action Required:** New installations should copy `.claude/` to `~/.claude/`
>
> [See full changelog below →](#-recent-updates)

<details>
<summary><strong>📅 Click to see all updates</strong></summary>

### Recent Manual Updates

- **✨ Oct 31:** v1.2.0 - Skills-as-Containers Migration - Complete architectural upgrade
- **✨ Oct 19:** Session-start hook now loads PAI skill - improved Skills system bootstrap
- **✨ Oct 18:** Major repo cleanup - fixed missing files, hooks, settings
- **✨ v0.5.0:** Skills-based architecture with 92.5% token reduction

### Automated Documentation Updates

<details>
<summary>📅 2025-10-20 - Settings: 1 updated</summary>

*Updated by pre-commit hook: 1 modified*
</details>

<details>
<summary>📅 2025-10-19 - Voice: 2 updated</summary>

*Updated by pre-commit hook: 3 modified*
</details>

<details>
<summary>📅 2025-10-19 - Skills: 1 updated, 5 removed</summary>

*Updated by pre-commit hook: 1 modified, 5 deleted*
</details>

<details>
<summary>📅 2025-10-19 - Hooks: 2 new, 1 removed, Settings: 1 updated</summary>

*Updated by pre-commit hook: 3 added, 1 modified, 1 deleted*
</details>

---

### Version History

<details>
<summary><strong>📅 v1.2.0 - Skills-as-Containers Migration 🔥 ARCHITECTURAL UPGRADE</strong></summary>

**The Problem:**
Commands were scattered in a flat global namespace (`~/.claude/commands/`), making it hard to discover related functionality, maintain consistency, and understand domain boundaries. The architecture needed hierarchical organization that matched how capabilities are naturally grouped.

**The Solution:**
Complete migration to Skills-as-Containers pattern:
- Moved 73 commands into skill-specific `workflows/` subdirectories
- Enhanced 21 skills with proper workflow organization
- Established deprecation pattern for future architectural upgrades
- Documented the complete migration process

**What Changed:**
```
Before (v0.6.0):
~/.claude/
├── commands/
│   ├── write-blog.md
│   ├── publish-blog.md
│   ├── quick-research.md
│   ├── extensive-research.md
│   └── [75+ scattered commands]
└── skills/
    ├── blogging/SKILL.md
    └── research/SKILL.md

After (v1.2.0):
~/.claude/
├── commands/               # Empty (commands moved to skills)
└── skills/
    ├── blogging/
    │   ├── SKILL.md
    │   └── workflows/
    │       ├── write.md
    │       └── publish.md
    └── research/
        ├── SKILL.md
        └── workflows/
            ├── quick.md
            └── extensive.md
```

**Architecture Benefits:**
- ✅ Domain knowledge colocated with workflows
- ✅ Clear ownership and responsibility
- ✅ Natural language routing: Skills → Workflows
- ✅ Easier discovery of related capabilities
- ✅ Better encapsulation of domain context

**Migration Stats:**
- 73 commands migrated to skill workflows
- 21 skills enhanced with workflows/ directories
- 1 new skill created (content-enhancement)
- Commands directory reduced from 75 files to 0
- Zero errors, 100% QA pass rate
- Complete in ~25 minutes using parallel agents

**Documentation:**
- See `docs/ARCHITECTURE.md` for Skills-as-Containers pattern
- Deprecation pattern established in `history/upgrades/deprecated/`
- Complete migration audit trail preserved

</details>

<details>
<summary><strong>📅 v0.6.0 - Repository Restructure with .claude/ Directory 🔥 MAJOR UPDATE</strong></summary>

**The Problem:**
Users reported issues with PAI not working correctly because the repository structure didn't match the actual working system. The real PAI system expects all infrastructure to live in `~/.claude/`, but the repo had everything at root level. This caused confusion and compatibility problems.

**The Solution:**
Complete repository restructure to mirror the actual working system:
- Created `.claude/` directory at repository root
- Moved ALL PAI infrastructure into `.claude/` (agents, commands, documentation, hooks, skills, voice-server, etc.)
- Kept GitHub infrastructure at root (README, LICENSE, .gitignore, .github, etc.)
- Repository now serves as a true reference implementation

**What Changed:**
```
Before (v0.5.0):
/PAI/
├── agents/
├── commands/
├── documentation/
├── hooks/
├── skills/
├── voice-server/
├── settings.json
├── .mcp.json
├── setup.sh
└── README.md

After (v0.6.0):
/PAI/
├── .claude/                 # ← NEW: All PAI infrastructure here
│   ├── agents/
│   ├── commands/
│   ├── documentation/
│   ├── hooks/
│   ├── skills/
│   ├── voice-server/
│   ├── settings.json
│   ├── .mcp.json
│   └── setup.sh
├── README.md               # GitHub infrastructure stays at root
├── LICENSE
└── .gitignore
```

**Why This Matters:**
1. **Proper Emulation:** Repository now accurately represents how PAI works in production
2. **Easier Setup:** Users can see exactly how their `~/.claude/` directory should be structured
3. **Less Confusion:** Clear separation between GitHub files and PAI infrastructure
4. **Better Documentation:** Structure itself serves as documentation
5. **Reference Implementation:** Can be copied/referenced directly for setup

**Migration:**
- No action required for existing installations
- New users get the correct structure from the start
- All documentation updated to reflect new paths

**Rationale:**
The PAI system is designed to live in `~/.claude/` on your system. By organizing the repository to mirror this structure, we make it immediately clear how PAI should be set up. This is especially important for new users who are trying to understand the system architecture and for contributors who need to know where files belong.

</details>

<details>
<summary><strong>📅 v0.5.0 - Skills-Based PAI Architecture (92.5% Token Reduction)</strong></summary>

**Major Architectural Improvement:**
- **Zero hook overhead** - Eliminated all context loading from UserPromptSubmit hook
- **92.5% token reduction** - From 4000 tokens/interaction to 300 tokens
- **Pure skills architecture** - Core identity in skill description (always in system prompt)
- **On-demand context** - Full context loaded only when explicitly needed

**What Changed:**
- Added YAML frontmatter to `skills/PAI/SKILL.md` with comprehensive system description
- Core identity + critical security now in skill description (always present)
- Removed `MINIMAL.md` entirely (no longer needed)
- Hook renamed to `update-tab-titles.ts` (only handles tab titles, zero context)
- Flat file structure in `skills/PAI/` (no `/contexts` subdirectory)

**Architecture:**
- **Tier 1 (Always On):** Skill description in system prompt (~300 tokens) - identity, critical security, architecture explanation
- **Tier 2 (On Demand):** `SKILL.md` body loaded when PAI skill invoked (~4000 tokens) - contacts, preferences, voice IDs, detailed security
- **Hook:** Only updates tab titles (0 tokens context overhead)

**Benefits:**
- Cleanest possible architecture - fully embraces Claude Code skills system
- Context always relevant - skill description always present, full context on-demand
- Easy to customize - clear YAML frontmatter with `[CUSTOMIZE:]` markers
- Scales efficiently - adding content doesn't multiply token costs

**Files:**
- `skills/PAI/SKILL.md` - Full context with YAML frontmatter
- `skills/PAI/contacts.md` - Contact templates
- `skills/PAI/preferences.md` - Stack preferences templates
- `skills/PAI/response-format.md` - Response format templates
- `skills/PAI/security-detailed.md` - Security procedures
- `skills/PAI/voice-ids.md` - Voice system configuration (optional)
- `hooks/update-tab-titles.ts` - Tab title updates only

</details>

<details>
<summary><strong>📅 v0.4.0 - Repository Restructure 🔥 BREAKING CHANGE</strong></summary>

**⚠️ Breaking Changes:**
- PAI_DIR environment variable: Change from `/path/to/PAI/PAI_DIRECTORY` to `/path/to/PAI`
- Repository renamed: `PAI` → `Personal_AI_Infrastructure`

**What Changed:**
- Moved all `PAI_DIRECTORY/` contents to repository root (agents/, skills/, commands/, etc.)
- Repository renamed for clarity and better SEO
- All functional directories now immediately visible on GitHub
- GitHub automatically redirects old URLs to new

**Migration:**
1. Update PAI_DIR: `export PAI_DIR="/path/to/PAI"` (remove `/PAI_DIRECTORY`)
2. Reload shell: `source ~/.zshrc`
3. Pull latest: `git pull`
4. Update remote: `git remote set-url origin git@github.com:danielmiessler/Personal_AI_Infrastructure.git`

</details>

<details>
<summary><strong>📅 v0.3.2 - Fabric Skill with Intelligent Pattern Selection</strong></summary>

Fabric skill now intelligently selects the right pattern from 242+ options based on user intent. Complete Fabric repository bundled locally. Categories: Security (15), Summarization (20), Extraction (30+), Analysis (35+), Creation (50+), Improvement (10), Rating (8).

</details>

<details>
<summary><strong>📅 v0.3.1 - Research Skills & API Key Infrastructure</strong></summary>

Multi-source research with parallel agent execution. New skills: `alex-hormozi-pitch`, `research`. New agents: `perplexity-researcher`, `claude-researcher`, `gemini-researcher`. Added `.env.example` with API key documentation.

</details>

<details>
<summary><strong>📅 v0.3.0 - Skills System Migration</strong></summary>

Migrated to [Anthropic's Skills architecture](https://www.anthropic.com/news/skills). Modular skill packages with progressive disclosure. Context system → Skills system. See [documentation](./documentation/skills-system.md) for details.

</details>

<details>
<summary><strong>📅 v0.2.4 - README Cleanup</strong></summary>

Collapsed updates section, reduced visual clutter, optimized space.

</details>

<details>
<summary><strong>📅 v0.2.3 - Visibility & Portability</strong></summary>

`.claude` → `PAI_DIRECTORY`, vendor agnostic, dynamic paths with `${PAI_DIR}`, full portability.

</details>

<details>
<summary><strong>📅 v0.2.2 - Voice System</strong></summary>

Migrated to macOS native Premium voices (zero cost, offline, private).

</details>

<details>
<summary><strong>📅 v0.2.0 - v0.1.0 - Initial Releases</strong></summary>

Public release with voice server, PAI_HOME support, comprehensive documentation, MCP detection, hooks system.

</details>

<details>
<summary><strong>📅 Previous Updates</strong></summary>

**September 20, 2025**
- 🗣️ Added `/voice-server` with ElevenLabs integration
- 🔧 Fixed hardcoded path issues
- 🪝 Working on missing hooks

**September 12, 2025**
- 🧠 Dynamic resource loading system
- ⚡ Submit-user-hook for context loading
- 🗺️ Dynamic routing via load-dynamic-requirements

</details>

</details>

---


---

