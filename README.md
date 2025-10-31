# PAI - Personal AI Infrastructure

**Open-source personal AI infrastructure for orchestrating your life and work**

![Static Badge](https://img.shields.io/badge/mission-upgrade_humans_using_AI-8B5CF6)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Claude Code](https://img.shields.io/badge/Powered%20by-Claude%20Code-blue)](https://claude.ai/code)
[![PAI Video](https://img.shields.io/badge/🎥_Watch-PAI_Video-6B46C1)](https://youtu.be/iKwRWwabkEc)

> **🔌 This is the Claude Code plugin version of PAI**
>
> Install with one command to get the full Personal AI Infrastructure. For advanced setup or the standalone version, visit the [main PAI repository](https://github.com/danielmiessler/Personal_AI_Infrastructure).

---

## 🎯 What is PAI?

> **Core Mission:** Augment humans with AI capabilities so they can survive and thrive in a world full of AI.

**It doesn't matter how powerful AI becomes if it's not accessible to everyone.**

Right now, AI is trapped behind corporate APIs, expensive subscriptions, and complex interfaces that only developers can use. Meanwhile, billions of people who could benefit from AI augmentation—artists, teachers, small business owners, researchers, parents—are left behind.

**PAI exists to solve this.** This project's goal is to give the most powerful AI capabilities, in the form of a complete platform, to everyone on Earth.

### What You Get

PAI is your **personal AI that actually knows you**—all your projects, your style, your data—and can handle anything you throw at it. Whether you're an artist transitioning to independence, a founder building a company, or someone managing complex life needs, PAI becomes whatever you need it to be.

**PAI is an open-source, full personal AI platform that's completely agnostic to who you are and what you're trying to accomplish.**

### Real Capabilities

<table>
<tr>
<td width="33%" valign="top">

### 💼 Professional

**Content Creation**
- Write blog posts in your style
- Publish directly to production
- Enhance existing content

**Business Analytics**
- Newsletter metrics tracking
- Website performance analysis
- Client deliverables generation

**Development**
- Code analysis and review
- Browser automation setup
- API infrastructure management

</td>
<td width="33%" valign="top">

### 🏠 Personal Life

**Financial Intelligence**
- Analyze bank statements
- Track spending patterns
- Parse PDFs for bills/expenses

**Memory & Conversations**
- Search recorded meetings
- Query conversation history
- Find event discussions

**Health Tracking**
- Monitor wellness metrics
- Track medical records
- Analyze sleep/fitness data

</td>
<td width="33%" valign="top">

### 🔬 Research & Learning

**Knowledge Capture**
- Extract insights from content
- Document learnings
- Deep web investigations

**Communication**
- Automated email outreach
- SMS notifications
- Team messaging integration

**Productivity**
- Task management
- Idea visualization
- Context-aware information access

</td>
</tr>
</table>

---

## 🚀 Quick Start (Plugin Installation)

### Prerequisites

**1. Get Claude Code**

Visit https://claude.ai/code to get Claude Code (Anthropic's official AI CLI).

**2. Install Bun Runtime**

```bash
brew install oven-sh/bun/bun
```

### Install PAI Plugin

**Option 1: One-Command Install (Easiest)**

```bash
claude-code plugin install github:danielmiessler/PAIPlugin
```

**Option 2: Manual Install**

```bash
# Clone the plugin
git clone https://github.com/danielmiessler/PAIPlugin.git ~/.claude/plugins/PAI

# Run setup
cd ~/.claude/plugins/PAI
./setup.sh
```

### Configure

```bash
# Create environment file
cp ~/.claude/.env.example ~/.claude/.env

# Add your API keys (optional - for research agents)
vim ~/.claude/.env
```

### Launch

Open Claude Code and start using your Personal AI Infrastructure!

```bash
claude
```

---

## 🌟 Why PAI is Different

> *This system is designed from the very beginning to be available to anybody and to grow and scale with you throughout your life.*

- **🔓 Open Framework**: No vendor lock-in, complete transparency, you own everything
- **🌍 Universal**: Works for anyone, anywhere, in any profession or life situation
- **🤖 Platform Independent**: Core structure works with Claude, GPT, Gemini, or any AI platform
- **🧠 Persistent Memory**: Your AI remembers every context, project, and conversation
- **🎯 Task Agnostic**: From writing a blog to tracking medical data to running a business
- **📁 Plain Text**: All configuration in human-readable files you can edit and understand
- **🔌 Extensible**: Add your own skills, agents, and integrations

---

## 🏗️ Architecture

PAI is built on four core primitives that work together:

**💡 Skills** - Meta-containers for domain expertise
- Package workflows, knowledge, and procedural guidance
- Auto-load based on natural language triggers
- Progressive disclosure prevents context bloat

**⚡ Workflows** - Discrete task workflows within Skills
- Self-contained, step-by-step workflows in `workflows/` subdirectories
- Auto-selected by natural language or invoked explicitly
- Like "exported functions" from a Skill module

**🤖 Agents** - Orchestration workers for parallelization
- Enable parallel execution of independent tasks
- Primarily invoke Skills/Workflows (not standalone knowledge bases)
- Best for background work where results are logged

**🔌 MCPs vs Direct Code** - Implementation flexibility
- Use MCPs for standardized platform services
- Use direct API code for domain-specific integrations

### How They Work Together

```
User Intent → Natural Language Trigger
    ↓
SKILL (Container for Domain)
    ↓
WORKFLOW (Specific Task)
    ↓
Implementation (Direct Code or MCPs)
    ↑
Invoked by AGENTS (for parallelization)
```

**Example:**

```
You: "Do extensive research on AI agent planning"
  ↓
Research Skill loads
  ↓
workflows/extensive-research.md selected
  ↓
Launches 24 parallel researcher agents
  ↓
Results consolidated and saved
```

📖 **[Read the full architecture documentation](./docs/ARCHITECTURE.md)**

---

## 📚 Included Skills

| Skill | What It Does | Example Usage |
|:------|:-------------|:--------------|
| **🔍 research** | Multi-source research with parallel agents | "Research quantum computing trends" |
| **🧵 fabric** | 242+ AI patterns (threat modeling, summarization, extraction) | "Create a threat model for our API" |
| **💻 development** | Full-stack development with architect and engineer agents | "Build a meditation timer app" |
| **🎨 design** | UX/UI design with shadcn/ui and Figma integration | "Design a dashboard for analytics" |
| **🔒 ffuf** | Web fuzzing for penetration testing | "Test this API for vulnerabilities" |
| **📊 alex-hormozi-pitch** | Create irresistible offers using $100M Offers framework | "Create a pitch for my SaaS product" |
| **🌐 web-scraping** | Extract data from websites (BrightData + Apify) | "Scrape product listings from this site" |
| **📖 ref-documentation** | Search technical docs (React, Next.js, 100+ frameworks) | "How do I use React hooks?" |
| **▶️ youtube-extraction** | Extract transcripts and content from YouTube videos | "Summarize this YouTube video" |
| **🎭 webapp-testing** | Browser automation and visual testing | "Test the login flow" |

---

## 📖 Documentation

| Guide | Purpose | Time |
|-------|---------|------|
| [Architecture](./docs/ARCHITECTURE.md) | Understand how PAI works | 15 min |
| [Migration Guide](./docs/MIGRATION.md) | Upgrade to v1.2.0 | 10 min |
| [Full PAI README](./docs/PAI-README.md) | Complete documentation | 20 min |

---

## 🚀 Recent Updates

> [!IMPORTANT]
> **🔥 v1.2.0 - Skills-as-Containers Migration** - Complete architectural upgrade

<details>
<summary><strong>📅 Click to see recent updates</strong></summary>

### Latest Changes

- **✨ Oct 31, 2025:** v1.2.0 - Skills-as-Containers Migration - Complete architectural upgrade
- **✨ Oct 19:** Session-start hook now loads CORE skill - improved Skills system bootstrap
- **✨ Oct 18:** Major repo cleanup - fixed missing files, hooks, settings
- **✨ v0.5.0:** Skills-based architecture with 92.5% token reduction

### v1.2.0 Highlights

**What Changed:**
- Moved 73 commands into skill-specific `workflows/` subdirectories
- Enhanced 21 skills with proper workflow organization
- Created example-skill demonstration
- Renamed PAI skill → CORE skill

**Architecture Benefits:**
- ✅ Domain knowledge colocated with workflows
- ✅ Clear ownership and responsibility
- ✅ Natural language routing: Skills → Workflows
- ✅ Easier discovery of related capabilities
- ✅ Better encapsulation of domain context

**Migration Stats:**
- 73 commands migrated to skill workflows
- 21 skills enhanced with workflows/ directories
- Zero errors, 100% QA pass rate
- Complete in ~25 minutes using parallel agents

📖 See [MIGRATION.md](./docs/MIGRATION.md) for complete upgrade guide

</details>

---

## 🤝 Community

### Get Help

- **🐛 Report Issues:** https://github.com/danielmiessler/Personal_AI_Infrastructure/issues
- **💬 Discussions:** https://github.com/danielmiessler/Personal_AI_Infrastructure/discussions
- **📖 Full Documentation:** https://github.com/danielmiessler/Personal_AI_Infrastructure

### Contribute

**⭐ Star the repos** to stay updated:
- [PAI Main Repository](https://github.com/danielmiessler/Personal_AI_Infrastructure)
- [PAI Plugin](https://github.com/danielmiessler/PAIPlugin)

---

## 🙏 Acknowledgments

Special thanks to contributors who have enhanced PAI:

- **[Joseph Thacker (@rez0)](https://twitter.com/rez0__)** - FFUF skill with comprehensive web fuzzing guidance

---

## 📄 License

PAI is MIT licensed. See [LICENSE](./LICENSE) for details.

---

## 🌍 The Path to Human 3.0

> *"Humans are what matter. AI is only as useful as it is to people. A system like this is needed to level the field with AI and help us get to [Human 3.0](https://danielmiessler.com/blog/how-my-projects-fit-together)."*

**Created by [Daniel Miessler](https://danielmiessler.com)**

📧 **[Newsletter](https://newsletter.danielmiessler.com)** • 📝 **[Blog](https://danielmiessler.com/blog)** • 💼 **[LinkedIn](https://linkedin.com/in/danielmiessler)** • 🎬 **[YouTube](https://www.youtube.com/@unsupervised-learning)**

---

**Questions?** See the [full PAI documentation](https://github.com/danielmiessler/Personal_AI_Infrastructure) for comprehensive guides, examples, and architecture details.
