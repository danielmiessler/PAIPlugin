# PAI - Personal AI Infrastructure Plugin

> **🔗 This is the Claude Code plugin version of [PAI (Personal AI Infrastructure)](https://github.com/danielmiessler/PAI)**
>
> For full documentation, architecture details, and the complete PAI system, visit the [main PAI repository](https://github.com/danielmiessler/PAI).

Transform Claude Code into your Personal AI Infrastructure with skills, agents, and automation workflows.

## What is PAI?

PAI (Personal AI Infrastructure) is a comprehensive Claude Code plugin that provides:

- **40+ Skills**: Research, development, website management, image generation, blogging, security testing, and more
- **10+ Specialized Agents**: Researchers, engineers, designers, architects, security testers
- **Custom Commands**: 50+ slash commands for frequent workflows
- **Automation Workflows**: Pre-built patterns for common development tasks

## Installation

### For Individual Use:

```bash
# Install from GitHub
/plugin install https://github.com/danielmiessler/PAIPlugin
```

### For Teams (Auto-Install):

Add to `.claude/settings.json` in your project:

```json
{
  "extraKnownMarketplaces": ["https://github.com/danielmiessler/PAIPlugin"],
  "plugins": {
    "pai": {
      "enabled": true
    }
  }
}
```

## Features

### Research Skills

- **Multi-Source Research**: Parallel research using Perplexity, Claude, and Gemini
- **Quick/Standard/Extensive Modes**: 3, 9, or 24 parallel agents
- **Source Attribution**: Confidence levels and cross-validation
- **Comprehensive Synthesis**: Findings organized by domain with conflicting information noted

### Development Skills

- **Spec-Driven Development**: Constitutional principles, feature specs, implementation plans
- **Test-Driven Methodology**: Library-first, test-first, integration-first
- **GitHub Spec Kit**: Template-driven quality and compliance

### Specialized Agents

- **perplexity-researcher**: Fast web searches and current information
- **claude-researcher**: Deep analytical research with intelligent decomposition
- **gemini-researcher**: Multi-perspective synthesis
- **engineer**: Professional software engineering with TDD
- **architect**: Software architecture and design
- **pentester**: Security testing and vulnerability assessment
- **designer**: UX/UI design and prototyping
- **artist**: AI image generation

### Custom Commands

- `/conduct-research`: Launch parallel research workflows
- `/capture-learning`: Document problem-solving journeys
- `/create-custom-image`: Generate images for content
- And 40+ more...

## Configuration

### Voice System (Optional)

If you want voice notifications, set up the voice server:

1. Configure voice IDs in agent files (`agents/*.md`)
2. Update `voiceId:` frontmatter with your ElevenLabs voice IDs
3. Run voice server on port 8888

### Customization

1. Review and customize skills in `skills/` directories
2. Modify agent behaviors in `agents/` markdown files
3. Add your own commands in `commands/` directory
4. Update `skills/PAI/SKILL.md` with your personal context

## Project Structure

```
PAIPlugin/
├── .claude-plugin/
│   └── plugin.json          # Plugin manifest
├── agents/                  # Specialized AI agents
│   ├── perplexity-researcher.md
│   ├── claude-researcher.md
│   ├── gemini-researcher.md
│   ├── engineer.md
│   └── ...
├── commands/                # Custom slash commands
│   ├── conduct-research.md
│   ├── capture-learning.md
│   └── ...
├── skills/                  # Agent skills
│   ├── research/
│   ├── development/
│   ├── fabric/
│   └── ...
└── README.md               # This file
```

## Usage Examples

### Research Workflow

```bash
# Quick research (3 agents, 2 minute timeout)
/conduct-research quick research on Claude Code plugins

# Standard research (9 agents, 3 minute timeout)
/conduct-research latest developments in quantum computing

# Extensive research (24 agents, 10 minute timeout)
/conduct-research extensive research on AI consciousness
```

### Development Workflow

```bash
# Build features with spec-driven development
Load the development skill and say "add a feature for user authentication"
```

### Image Generation

```bash
# Create custom images for blog posts
/create-custom-image hero image for blog post about AI coding assistants
```

## Requirements

- Claude Code v2.0.12 or higher (plugin system support)
- macOS, Windows, or Linux
- Node.js 18+ (if using MCP servers)

## Contributing

Contributions welcome! Please:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## Security & Privacy

This plugin contains NO secrets, API keys, or personal data. All examples use placeholders.

**For Production Use:**
- Add your API keys via environment variables
- Customize skills with your personal context
- Never commit real credentials to version control

## License

MIT License - see LICENSE file

## Support

- Issues: https://github.com/danielmiessler/PAIPlugin/issues
- Documentation: https://github.com/danielmiessler/PAI
- Website: https://danielmiessler.com

## About PAI

This plugin is part of the **[Personal AI Infrastructure (PAI)](https://github.com/danielmiessler/PAI)** project.

**PAI** is a comprehensive system for building your own AI-powered workflows and infrastructure. This repository contains the Claude Code plugin version, making PAI's capabilities easily installable for Claude Code users.

**🔗 Learn More:**
- **Main PAI Repository**: https://github.com/danielmiessler/PAI
- **Full Documentation**: Complete architecture, setup guides, and philosophy
- **PAI Website**: https://danielmiessler.com

Created by Daniel Miessler ([@DanielMiessler](https://twitter.com/danielmiessler))
