# AI Solution Architecture Framework

**A practical toolkit for designing and building AI agent systems—from requirements to prototype in 1-2 weeks.**

---

## What This Is

A streamlined framework for anyone doing AI solution architecture. Whether you're a consultant working with stakeholders, an engineer building internal tools, or a product team prototyping features—this gives you the structure to go from idea to working prototype fast.

**Core workflow:**

1. **Discover** → Understand the problem (30 min)
2. **Document** → Capture requirements (90 min)
3. **Design** → Architect the solution (2-4 hours)
4. **Build** → Create prototype (1-2 weeks)
5. **Demo** → Validate and iterate (1 hour)

**Everything is copy-paste ready.** No complex setup. Just guides, templates, and AI assistant prompts you can use immediately.

---

## Quick Start

### Core Process (1-2 Weeks)

```bash
1. Discovery (30 min)
   → Use: requirements/discovery-guide.md
   → Understand workflows and identify opportunities

2. Requirements Workshop (90 min)
   → Use: requirements/workshop-guide.md + requirements-agent.prompt.md
   → Document detailed requirements

3. Architecture Design (2-4 hours)
   → Use: architecture/design-guide.md + technical-architect-agent.prompt.md
   → Design agent system and select tech stack

4. Prototype Development (1-2 weeks)
   → Use: development/prototype-guide.md + prototype-builder-agent.prompt.md
   → Build working system

5. Demo & Iterate (1 hour)
   → Use: delivery/demo-guide.md
   → Validate, gather feedback, refine
```

### Using the AI Assistants

Copy any agent prompt into **Cursor**, **Claude Projects**, **ChatGPT**, or **Mistral** for real-time assistance:

- **`requirements/discovery-agent.prompt.md`** - Helps run discovery sessions
- **`architecture/technical-architect-agent.prompt.md`** - Designs system architecture  
- **`development/prototype-builder-agent.prompt.md`** - Generates code and agent prompts
- **Architecture workflow prompts** (5 specialized prompts for requirements analysis, tech stack selection, team composition, project planning, cost estimation)

---

## Repository Structure

```
/requirements/
├── discovery-guide.md              # How to run discovery sessions
├── workshop-guide.md               # How to run requirements workshops  
├── requirements-template.md        # Requirements document template
└── discovery-agent.prompt.md       # AI assistant for requirements

/architecture/
├── design-guide.md                 # How to design agent systems
├── architecture-template.md        # Architecture document template
├── agent-design-patterns.md        # Reusable agent patterns
├── technical-architect-agent.prompt.md  # AI assistant for architecture
└── [5 workflow prompts]            # Specialized architecture prompts

/development/
├── prototype-guide.md              # How to build prototypes
├── development-checklist.md        # 2-week dev checklist
└── prototype-builder-agent.prompt.md  # AI assistant for prototyping

/delivery/
├── demo-guide.md                   # How to demo effectively
└── handoff-checklist.md            # Project handoff checklist
```

---

## What You Get

### ✅ Proven Process

- Battle-tested workflow from real projects
- Optimized for 1-2 week execution by one person
- Focus on working prototypes, not perfect systems
- Clear decision points and quality checks

### ✅ AI Agent Patterns

Reusable agent patterns for common scenarios:

- **Specialist Agents** - Single-task focus
- **Workflow Agents** - Multi-step processes
- **Document Generators** - Formatted outputs
- **Research Agents** - Information gathering
- **Review Agents** - Validation and QA
- **Router Agents** - Orchestration and coordination

Each pattern includes when to use it, implementation details, and testing approaches.

### ✅ Platform Agnostic

Works with your tools:

- **LLMs:** Claude, GPT-4, Mistral, or any LLM
- **Development:** Python, Node.js, any language
- **Deployment:** Cloud, on-premise, or local
- **AI Tools:** Cursor, Claude Projects, ChatGPT, etc.

### ✅ Copy-Paste Friendly

Every resource is designed for immediate use:

- Clear step-by-step instructions
- Real example scripts
- Working code templates
- No complex configuration

---

## Who This Is For

**✅ Perfect for:**

- AI engineers building agent systems
- Solution architects designing AI implementations
- Product engineers prototyping AI features
- Technical leads planning AI projects
- Anyone gathering requirements for AI solutions

**⚠️ Less useful for:**

- ML researchers focused on model development
- Data scientists building predictive models
- Non-technical stakeholders (this is hands-on technical)

---

## Philosophy

### Function Over Perfection

Build working systems that demonstrate value:

- Prototype to prove concepts
- Iterate based on real feedback
- Ship functional code fast
- Optimize for clarity and maintainability

### Human-First Design

AI augments, doesn't replace judgment:

- Clear processes you can follow manually
- AI assistants provide guidance when helpful
- Templates are starting points, not rigid rules
- Adapt everything to your specific context

### Practical, Not Academic

Real-world focused:

- What works in actual projects
- Clear recommendations over endless options
- Examples from real use cases
- Honest about trade-offs and limitations

---

## Usage Examples

### Example 1: Simple Automation (1-2 weeks)

**Scenario:** Need to automate 1-2 repetitive tasks

**Process:**

1. 30-min discovery → identify automation opportunity
2. Skip formal workshop, capture requirements in conversation
3. Use "Specialist Agent" pattern from agent-design-patterns.md
4. Build prototype in 3-5 days
5. Quick demo and iterate

**Result:** 1-2 specialized agents, 20-40 hours effort

---

### Example 2: Multi-Agent System (3-4 weeks)

**Scenario:** Multiple coordinated workflows

**Process:**

1. Discovery session → understand scope
2. Full 90-min requirements workshop
3. Design multi-agent architecture
4. Build prototype over 2-3 weeks  
5. Demo, gather feedback, handoff

**Result:** 3-5 coordinated agents, 80-160 hours effort

---

### Example 3: Using with Cursor

```bash
# Setup
1. Open this repo in Cursor
2. Open requirements/discovery-agent.prompt.md
3. Copy entire prompt into Cursor chat
4. Cursor now provides real-time discovery guidance

# During requirements session
YOU: "Stakeholder mentioned spending 8 hours/week on manual reports"

CURSOR: 
🔴 PAIN POINT IDENTIFIED: Manual report generation
Classification: HIGH - Document generation task
Suggested follow-up: "Walk me through creating one report..."
Potential solution: Report automation agent
```

---

## Key Features

### Rapid Requirements Capture

- 30-min discovery sessions
- 90-min comprehensive workshops
- Structured templates that work
- AI assistant for real-time guidance

### Agent Design Patterns

- Proven patterns for common scenarios
- Complete prompt templates
- Integration approaches
- Testing strategies

### Fast Prototyping

- 1-2 week development cycles
- Code generation support
- Demo scenario templates
- Iteration framework

---

## Documentation Standards

All guides follow these principles:

1. **Actionable** - Clear next steps, always
2. **Scannable** - Headings, bullets, clear formatting
3. **Example-Rich** - Real examples, not abstract concepts
4. **Honest** - What doesn't work, not just what does
5. **Concise** - Respect your time

---

## Getting Started

1. **Read** `requirements/discovery-guide.md`
2. **Use it** for your next requirements conversation
3. **Copy** agent prompts into your AI tool of choice
4. **Follow** the process from discovery → demo
5. **Adapt** everything to your specific needs

---

## Contributing

This is a living framework. Contributions welcome:

- Better workshop questions
- Additional agent patterns
- Real-world case studies  
- Process improvements
- Bug fixes and clarifications

Open issues or submit PRs. All contributions appreciated.

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
- **Requirements Engineering** - Structured requirements gathering

Inspired by real projects and the AI engineering community.

---

**Version:** 3.0 (Universal Refactor - October 2025)  
**Status:** Production-ready

---

**Start here:** [`requirements/discovery-guide.md`](requirements/discovery-guide.md)
