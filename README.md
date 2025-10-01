# AI Architecture Assistant

**A practical framework for AI engineers and architects to gather requirements, design multi-agent systems, and deliver AI solutions.**

---

## For AI Engineers and Architects

This repository provides a structured, battle-tested process for taking AI projects from initial client conversation to working prototype. If you design and build AI agent systems, this toolkit helps you:

- **Gather complete requirements** using proven workshop techniques
- **Design robust architectures** with reusable patterns
- **Build working prototypes** fast using agent design templates
- **Deliver professional solutions** with proper handoff documentation

**Everything is copy-paste friendly.** No complex setup, no APIs to configure. Just guides, templates, and prompts you can use immediately.

---

## Quick Start

### For Your Next Project

1. **Discovery** (30 min)
   - Use [`requirements/discovery-guide.md`](requirements/discovery-guide.md)
   - Understand client needs and identify AI opportunities

2. **Requirements** (90 min)
   - Use [`requirements/workshop-guide.md`](requirements/workshop-guide.md)
   - Capture detailed workflows and create requirements doc

3. **Architecture** (2-4 hours)
   - Use [`architecture/design-guide.md`](architecture/design-guide.md)
   - Design agents and select technology stack

4. **Development** (2-4 weeks)
   - Use [`development/prototype-guide.md`](development/prototype-guide.md)
   - Build functional prototype with agent patterns

5. **Delivery** (1-2 days)
   - Use [`delivery/demo-guide.md`](delivery/demo-guide.md)
   - Demo system and gather feedback
   - Use [`delivery/handoff-checklist.md`](delivery/handoff-checklist.md)
   - Complete project handoff

### Using the Agent Prompts

This toolkit includes specialized AI assistant prompts for use in **Cursor**, **Claude Projects**, or **Claude Workspaces**:

**During requirements:**
- Copy [`requirements/discovery-agent.prompt.md`](requirements/discovery-agent.prompt.md) into your AI workspace
- Use for real-time guidance during discovery sessions and workshops

**During architecture:**
- Copy [`architecture/technical-architect-agent.prompt.md`](architecture/technical-architect-agent.prompt.md)
- Get architecture recommendations and design patterns

**During development:**
- Copy [`development/prototype-builder-agent.prompt.md`](development/prototype-builder-agent.prompt.md)
- Generate agent prompts, code templates, and demo scenarios

**Advanced workflows:**
- Use prompts in [`architecture/`](architecture/) for specialized tasks:
  - Requirements analysis
  - Tech stack selection
  - Team composition planning
  - Project estimation

---

## What's Included

### Requirements Phase

📁 **requirements/**

- **[discovery-guide.md](requirements/discovery-guide.md)** - Run effective 30-minute discovery sessions
- **[workshop-guide.md](requirements/workshop-guide.md)** - Conduct 90-minute requirements workshops
- **[requirements-template.md](requirements/requirements-template.md)** - Complete requirements document template
- **[discovery-agent.prompt.md](requirements/discovery-agent.prompt.md)** - AI assistant for requirements gathering

### Architecture Phase

📁 **architecture/**

- **[design-guide.md](architecture/design-guide.md)** - Design multi-agent AI systems
- **[architecture-template.md](architecture/architecture-template.md)** - System architecture document template
- **[agent-design-patterns.md](architecture/agent-design-patterns.md)** - Reusable agent patterns with examples
- **[technical-architect-agent.prompt.md](architecture/technical-architect-agent.prompt.md)** - AI assistant for architecture design
- **5 specialized prompts** for requirements analysis, tech stack, team planning, project planning, cost estimation

### Development Phase

📁 **development/**

- **[prototype-guide.md](development/prototype-guide.md)** - Build working AI agent prototypes
- **[development-checklist.md](development/development-checklist.md)** - 2-week sprint checklist
- **[prototype-builder-agent.prompt.md](development/prototype-builder-agent.prompt.md)** - AI assistant for rapid prototyping

### Delivery Phase

📁 **delivery/**

- **[demo-guide.md](delivery/demo-guide.md)** - Conduct effective prototype demonstrations
- **[handoff-checklist.md](delivery/handoff-checklist.md)** - Complete project handoff process
- **[communication-templates.md](delivery/communication-templates.md)** - Professional email and meeting templates

---

## Three Quick-Start Scenarios

### Scenario 1: Simple Automation (1-2 weeks)

**When:** Client needs to automate 1-2 repetitive tasks

**Use:**
1. [`requirements/discovery-guide.md`](requirements/discovery-guide.md) - 30 min discovery call
2. Skip formal workshop, capture requirements in conversation
3. [`architecture/agent-design-patterns.md`](architecture/agent-design-patterns.md) - Use "Specialist Agent" pattern
4. [`development/prototype-guide.md`](development/prototype-guide.md) - Build in 3-5 days
5. [`delivery/demo-guide.md`](delivery/demo-guide.md) - Quick demo and handoff

**Timeline:** 1-2 weeks  
**Agents:** 1-2 specialist agents  
**Effort:** 20-40 hours

### Scenario 2: Standard Multi-Agent System (3-4 weeks)

**When:** Client needs coordinated agents for multiple workflows

**Use:**
1. [`requirements/discovery-guide.md`](requirements/discovery-guide.md) - Discovery session
2. [`requirements/workshop-guide.md`](requirements/workshop-guide.md) - Full requirements workshop
3. [`architecture/design-guide.md`](architecture/design-guide.md) - Design system architecture
4. [`development/prototype-guide.md`](development/prototype-guide.md) - Build in 2-3 weeks
5. [`delivery/demo-guide.md`](delivery/demo-guide.md) + [`delivery/handoff-checklist.md`](delivery/handoff-checklist.md) - Demo and handoff

**Timeline:** 3-4 weeks  
**Agents:** 3-5 coordinated agents  
**Effort:** 80-160 hours

### Scenario 3: Complex Enterprise System (6-12 weeks)

**When:** Large organization, multiple integrations, high complexity

**Use:**
1. Full requirements process with multiple stakeholders
2. Complete architecture documentation
3. Use all specialized architecture prompts (tech stack, team composition, cost estimation)
4. Phased development approach
5. Comprehensive handoff with knowledge transfer

**Timeline:** 6-12 weeks  
**Agents:** 7+ agents with complex workflows  
**Effort:** 320+ hours

---

## Key Features

### ✅ Copy-Paste Workflows

Every guide is designed to be used immediately:
- Clear step-by-step instructions
- Real example scripts and prompts
- No complex setup required
- Works with any AI platform

### ✅ Agent Design Patterns

Proven patterns for common scenarios:
- Specialist agents (focused on single tasks)
- Workflow agents (multi-step processes)
- Document generators (formatted output)
- Research & synthesis agents
- Review & validation agents
- Coordinator/router agents

Each pattern includes:
- When to use it
- Complete prompt templates
- Testing approaches
- Common variations

### ✅ Platform Agnostic

Works with your preferred tools:
- **LLM Platforms:** Anthropic Claude, OpenAI, Azure OpenAI, others
- **Development:** Python, Node.js, any language
- **Deployment:** Cloud, on-premise, serverless
- **AI Tools:** Cursor, Claude Projects, Claude Workspaces

### ✅ Real-World Tested

These processes have been used to deliver actual client projects. Not theoretical—practical and battle-tested.

---

## Philosophy

### Human-First, AI-Augmented

This toolkit is designed for **manual execution** first:
- Copy guides into your workflow
- Follow step-by-step processes
- Use templates as starting points
- Leverage AI assistants where helpful

You don't need complex automation. You need clear processes.

### Function Over Perfection

The goal is **working systems**, not perfect systems:
- Prototype to prove value
- Iterate based on feedback
- Ship functional code fast
- Optimize for clarity and maintainability

### Practical, Not Academic

This is a **practitioner's toolkit**:
- Focus on what works in real projects
- Clear recommendations, not endless options
- Examples from actual use cases
- Honest about trade-offs and limitations

---

## Who This Is For

### ✅ Great for:

- **AI Engineers** building agent systems for clients or internal projects
- **Solution Architects** designing AI implementations
- **Independent Consultants** delivering AI solutions
- **Product Engineers** prototyping AI features
- **Engineering Managers** planning AI projects

### ⚠️ Less useful for:

- ML researchers focused on model development
- Data scientists building predictive models
- Salespeople (this is technical, not sales-focused)
- Non-technical business owners (too hands-on)

---

## Example Usage

### Using Discovery Guide

```bash
# Before client meeting
1. Read requirements/discovery-guide.md
2. Prepare 3-5 relevant AI use case examples
3. Set up note-taking system

# During 30-min discovery call
1. Follow question structure from guide
2. Capture pain points and technology stack
3. Identify AI opportunities

# Within 1 hour after
1. Use meeting summary template
2. Categorize pain points (HIGH/MEDIUM/LOW for AI)
3. Determine next steps
```

### Using Agent Design Patterns

```bash
# When designing an agent
1. Read architecture/agent-design-patterns.md
2. Choose pattern matching your need:
   - Specialist Agent for focused tasks
   - Document Generator for formatted outputs
   - Research Agent for information gathering
3. Copy prompt template
4. Customize with your domain specifics
5. Test and iterate
```

### Using with Cursor AI

```bash
# Setup
1. Open this repo in Cursor
2. Copy requirements/discovery-agent.prompt.md
3. Paste into Cursor chat
4. Cursor will now provide real-time guidance

# During requirements workshop
YOU: "Client just described spending 8 hours/week on manual reporting"
CURSOR: "🔴 PAIN POINT IDENTIFIED: Manual report generation
         Classification: HIGH - Document generation task
         Suggested follow-up: 'Walk me through creating one report...'
         Potential solution: Report automation agent"
```

---

## Documentation Standards

All guides in this repository follow these principles:

1. **Actionable** - Every guide includes clear next steps
2. **Scannable** - Use headings, bullets, and formatting
3. **Example-Rich** - Real examples, not abstract concepts
4. **Honest** - Include what doesn't work, not just what does
5. **Concise** - Respect your time, no unnecessary length

---

## Contributing

This toolkit is maintained as a resource for the AI architecture community.

### Ways to Contribute

**Share improvements:**
- Better workshop questions
- Additional agent patterns
- Real-world case studies
- Process refinements

**Submit pull requests:**
- Fix errors or unclear sections
- Add missing use cases
- Improve examples
- Enhance templates

**Provide feedback:**
- Open issues for suggestions
- Share what works/doesn't work for you
- Request additional guides or patterns

---

## License

MIT License - Use freely for commercial and personal projects

---

## Author

**Paul Prae**  
AI Architect & Engineer

- Email: <hireme@paulprae.com>
- LinkedIn: [linkedin.com/in/paulprae](https://linkedin.com/in/paulprae)
- GitHub: [github.com/praeducer](https://github.com/praeducer)

---

## Acknowledgments

Built on principles from:
- **Service-as-Software** (Foundation Capital) - AI-native business models
- **AI Agent Orchestration** (LangChain, AutoGen) - Multi-agent patterns
- **Solution Architecture** - Enterprise architecture methodologies
- **Consulting Best Practices** - Requirements gathering and client delivery

Inspired by real client engagements and the generous sharing of the AI engineering community.

---

## Quick Links

**Core Guides:**
- [Discovery Guide](requirements/discovery-guide.md) - Start here for new projects
- [Workshop Guide](requirements/workshop-guide.md) - Detailed requirements gathering
- [Design Guide](architecture/design-guide.md) - System architecture design
- [Agent Patterns](architecture/agent-design-patterns.md) - Reusable agent designs
- [Prototype Guide](development/prototype-guide.md) - Build working systems
- [Demo Guide](delivery/demo-guide.md) - Effective demonstrations

**Templates:**
- [Requirements Template](requirements/requirements-template.md)
- [Architecture Template](architecture/architecture-template.md)
- [Communication Templates](delivery/communication-templates.md)

**AI Assistants:**
- [Discovery Agent](requirements/discovery-agent.prompt.md)
- [Technical Architect Agent](architecture/technical-architect-agent.prompt.md)
- [Prototype Builder Agent](development/prototype-builder-agent.prompt.md)

---

**Version:** 2.0 (Refactored October 2025)  
**Status:** Production-ready for manual execution

---

**Get Started:** Read [`requirements/discovery-guide.md`](requirements/discovery-guide.md) and use it for your next client conversation.
