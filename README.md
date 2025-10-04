# AI Architecture Assistant 🤖🏗️

**Transform AI ideas into production-ready architectures in hours, not weeks.**

A multi-agent system that guides you through the complete AI development lifecycle—from requirements gathering to deployment—following industry best practices (AWS Well-Architected, TDSP/MLOps workflows, Anthropic prompt engineering).

**Perfect for:** Junior to mid-level AI engineers and architects building GenAI systems

**Deployment:** Cursor | Claude Projects | AWS Bedrock | Platform-Agnostic

---

## What This System Does

Think of this like having 5 expert AI consultants on your team:

1. **Supervisor Agent** 🎯 - Your guide who routes you to the right expert
2. **Requirements Agent** 📋 - Helps you understand what to build (discovery sessions)
3. **Architecture Agent** 🏛️ - Designs your AI system (tech stack, diagrams, cost estimates)
4. **Engineering Agent** 👨‍💻 - Builds working prototypes (code, UI, demos)
5. **Deployment Agent** 🚀 - Deploys to your platform (Cursor, AWS Bedrock, etc.)
6. **Optimization Agent** ⚡ - Improves your AI systems (and this system itself!)

**The magic:** These agents work together like a well-orchestrated team, passing information through a shared knowledge base, so you get consistent, high-quality results.

---

## 🚀 Quick Start (15 Minutes)

### Step 1: Choose Your Entry Point

**First time building an AI system?**
→ Start with the **Supervisor Agent** - it will guide you through everything

**Have a specific task?**
→ Jump to the appropriate specialized agent (see Agent Guide below)

### Step 2: Set Up Your Environment

**Option A: Cursor (Easiest)**

1. Open this repository in Cursor
2. Create a new Custom Chat Mode
3. Copy the contents of `supervisor_agent.system.prompt.md`
4. Paste into Custom Instructions → Save as "AI Architecture Assistant"
5. Start chatting: "I want to build an AI system"

**Option B: Claude Projects**

1. Create new Claude Project named "AI Architecture Assistant"
2. Copy `supervisor_agent.system.prompt.md` → Paste as Custom Instructions
3. Upload `knowledge_base/` folder to Project Knowledge
4. Start conversation: "Help me design an AI system"

**Option C: AWS Bedrock (Enterprise)**
→ See `guides/platform_deployment.md` for full Bedrock multi-agent setup

### Step 3: Your First AI System

**Try the example:** Design a Financial Operations Assistant for solo-entrepreneurs

```
You: "I'm a solo-entrepreneur spending 10 hours/week on invoicing, 
expense tracking, and financial reports. Can AI help?"

Supervisor Agent: "Absolutely! Let me connect you with the Requirements Agent..."

[15-minute discovery session]

Requirements Agent: "✅ Requirements complete. Ready for architecture design?"

[2-hour architecture design]

Architecture Agent: "✅ Design complete. Tech stack: Python + Claude + Streamlit.
Cost: $75K development + $200/mo infrastructure. Ready to build prototype?"

[8-12 hour prototype development]

Engineering Agent: "✅ Prototype built! Location: outputs/prototypes/financial-operations-assistant/"

[Demo to stakeholders, gather feedback]

Deployment Agent: "✅ Deployed to Cursor as custom chat modes. Ready for production?"
```

**Result:** Working multi-agent financial assistant in ~1 week ⏱️

---

## 📚 Agent Guide - When to Use Each Agent

### Use Supervisor Agent When

- ✅ You're new to this system
- ✅ You're not sure which agent to use
- ✅ You want guided workflow through multiple phases
- ✅ You want seamless agent transitions

**Location:** `supervisor_agent.system.prompt.md`

---

### Use Requirements Agent When

- ✅ Starting a new AI project (gather requirements)
- ✅ Conducting discovery sessions with stakeholders
- ✅ Parsing meeting notes into structured requirements
- ✅ Classifying pain points by AI suitability

**Location:** `ai_agents/requirements_agent.system.prompt.md`

**User Prompts:**

- `user_prompts/requirements/quick_discovery.user.prompt.md` - 15-min rapid assessment
- `user_prompts/requirements/standard_discovery.user.prompt.md` - 30-min session
- `user_prompts/requirements/comprehensive_workshop.user.prompt.md` - 90-min deep-dive
- `user_prompts/requirements/extract_requirements.user.prompt.md` - Parse notes

**Output:** `knowledge_base/user_requirements.json`

---

### Use Architecture Agent When

- ✅ Designing AI system architecture
- ✅ Selecting tech stack (LLM providers, frameworks, infrastructure)
- ✅ Generating architecture diagrams
- ✅ Estimating costs and timelines
- ✅ Creating project plans
- ✅ Assembling executive proposals

**Location:** `ai_agents/architecture_agent.system.prompt.md`

**User Prompts (Multi-Shot Sequence):**

1. `user_prompts/architecture/tech_stack_selection.user.prompt.md`
2. `user_prompts/architecture/architecture_diagram_generation.user.prompt.md`
3. `user_prompts/architecture/team_composition.user.prompt.md`
4. `user_prompts/architecture/loe_estimation.user.prompt.md`
5. `user_prompts/architecture/cost_estimation.user.prompt.md`
6. `user_prompts/architecture/project_plan_generation.user.prompt.md`

**Proposal Assembly:**

- `user_prompts/proposals/discovery_proposal_assembly.user.prompt.md`
- `user_prompts/proposals/implementation_proposal_assembly.user.prompt.md`

**Output:** `knowledge_base/design_decisions.json`

---

### Use Engineering Agent When

- ✅ Building prototypes from architecture designs
- ✅ Generating agent code (Python, Node.js)
- ✅ Creating UIs (Streamlit, React, CLI)
- ✅ Writing demo scenarios and test cases

**Location:** `ai_agents/engineering_agent.system.prompt.md`

**User Prompts:**

- `user_prompts/engineering/prototype_builder.user.prompt.md`

**Output:** `outputs/prototypes/[project-name]/`

---

### Use Deployment Agent When

- ✅ Deploying prototypes to target platforms
- ✅ Creating testing strategies
- ✅ Assessing production readiness
- ✅ Generating handoff documentation

**Location:** `ai_agents/deployment_agent.system.prompt.md`

**User Prompts:**

- `user_prompts/deployment/platform_deployment.user.prompt.md`
- `user_prompts/deployment/testing_strategy.user.prompt.md`

---

### Use Optimization Agent When

- ✅ Improving deployed AI systems
- ✅ Refactoring prompts for efficiency
- ✅ Reducing LLM API costs
- ✅ Optimizing this AI Architecture Assistant system itself

**Location:** `ai_agents/optimization_agent.system.prompt.md`

**User Prompts:**

- `user_prompts/optimization/system_optimization.user.prompt.md` - Optimize any AI system
- `user_prompts/optimization/improve_ai_architecture_assistant.user.prompt.md` - System-wide improvement
- `user_prompts/optimization/improve_requirements_agent.user.prompt.md` - Targeted agent improvement
- `user_prompts/optimization/improve_architecture_agent.user.prompt.md` - Targeted agent improvement
- `user_prompts/optimization/improve_engineering_agent.user.prompt.md` - Targeted agent improvement
- `user_prompts/optimization/improve_deployment_agent.user.prompt.md` - Targeted agent improvement
- `user_prompts/optimization/improve_optimization_agent.user.prompt.md` - Self-improvement
- `user_prompts/optimization/improve_supervisor_agent.user.prompt.md` - Targeted agent improvement

---

## 📁 Repository Structure

```
AI-architecture-assistant/
├── supervisor_agent.system.prompt.md       # START HERE - Your main orchestrator
│
├── ai_agents/                              # Specialized agents (copy to chat modes)
│   ├── requirements_agent.system.prompt.md
│   ├── architecture_agent.system.prompt.md
│   ├── engineering_agent.system.prompt.md
│   ├── deployment_agent.system.prompt.md
│   └── optimization_agent.system.prompt.md
│
├── user_prompts/                           # Task-specific instructions
│   ├── requirements/                       # Discovery session prompts
│   ├── architecture/                       # Design step prompts
│   ├── proposals/                          # Executive proposal assembly
│   ├── engineering/                        # Implementation prompts
│   ├── deployment/                         # Deployment prompts
│   └── optimization/                       # System & agent improvement prompts
│
├── knowledge_base/                         # Shared data (JSON)
│   ├── system_config.json                  # Platform, constraints, stakeholders
│   ├── user_requirements.json              # Discovery outputs
│   └── design_decisions.json               # Architecture outputs
│
├── outputs/                                # Generated prototypes
│   └── prototypes/[project-name]/          # Your built AI systems
│
├── guides/                                 # User documentation
│   ├── getting_started.md                  # New users start here
│   ├── workflow_guide.md                   # Complete lifecycle
│   ├── platform_deployment.md              # Platform-specific setup
│   ├── executive_overview.md               # For business leaders
│   └── examples/                           # Example projects
│
├── templates/                              # Reusable templates
└── docs/                                   # Reference documentation
    └── agent_design_patterns.md            # AI agent patterns library
```

---

## 🎓 Learning Path for Junior Engineers

### Level 1: First AI System (2-3 hours)

1. **Read:** This README (you're here! ✅)
2. **Try:** Follow Quick Start above with financial operations example
3. **Practice:** Complete one discovery → design → prototype cycle
4. **Understand:** How agents work together through knowledge base

### Level 2: Independent Usage (1 week)

1. **Read:** `guides/getting_started.md` (deep dive)
2. **Read:** `guides/workflow_guide.md` (complete lifecycle)
3. **Try:** Design your own AI system for a real problem
4. **Practice:** All 6 architecture design steps

### Level 3: Advanced Patterns (2 weeks)

1. **Read:** `docs/agent_design_patterns.md` (9 reusable patterns)
2. **Study:** Financial operations assistant in `outputs/prototypes/`
3. **Try:** Build multi-agent system with 3+ agents
4. **Master:** AWS Well-Architected principles application

---

## 💡 Key Concepts

### Multi-Agent Architecture

This system uses a **supervisor-worker pattern** (like AWS Bedrock multi-agent orchestration):

- **Supervisor** routes requests to specialized workers
- **Workers** (agents) each handle specific domains
- **Knowledge base** stores shared state
- **User prompts** provide task-specific instructions

### Knowledge Base Pattern

All agents read/write to JSON files for consistency:

- `system_config.json` - Your project settings (you configure once)
- `user_requirements.json` - Requirements Agent writes, Architecture Agent reads
- `design_decisions.json` - Architecture Agent writes, Engineering Agent reads

This prevents information loss and enables traceability.

### Multi-Shot Prompting

Architecture Agent doesn't do everything itself—it orchestrates 6 separate user prompts in sequence:

1. Tech stack selection
2. Architecture diagram generation
3. Team composition
4. LOE estimation
5. Cost estimation
6. Project plan generation

Each produces a specific deliverable that informs the next.

---

## 🎯 Primary Example: Financial Operations Assistant

Throughout this system, we use a **multi-agent financial operations assistant for solo-entrepreneurs** as the reference example. This is inspired by (but more well-architected than) the [financial-assistant-for-families](https://github.com/Modular-Earth-LLC/financial-assistant-for-families) reference.

**Why this example:**

- Real-world use case most people understand
- Demonstrates multi-agent coordination
- Shows knowledge base pattern
- Covers all design steps
- Includes both technical and business perspectives

**What it does:**

- Automates invoicing (saves 2 hrs/week)
- Categorizes expenses (saves 3 hrs/week)
- Generates financial reports (saves 5 hrs/week)
- Provides financial insights and forecasting

**Architecture:**

- 2 specialized agents (Operations + Analytics)
- Shared knowledge base (local JSON)
- Streamlit UI for non-technical users
- Claude Sonnet for complex analysis, Haiku for simple categorization

You can follow this example through the entire system to understand how each phase works.

---

## 🎭 Deployment Scenarios

This system supports multiple deployment patterns:

### Scenario A: Cursor Custom Chat Modes (Development)

- Each agent runs independently
- Manual switching between agents
- Knowledge base via file system
- **Best for:** Small teams, local development, rapid iteration

### Scenario B: Cursor Supervisor Mode (Integrated)

- Supervisor dynamically loads specialized agents
- Automatic agent transitions
- Seamless workflow
- **Best for:** Integrated development experience

### Scenario C: AWS Bedrock Multi-Agent (Production)

- Supervisor as Bedrock orchestrator agent
- Specialized agents as Bedrock sub-agents
- User prompts via Bedrock Prompt Management
- Knowledge base via Bedrock Knowledge Bases
- **Best for:** Enterprise, scalable production deployments

See `guides/platform_deployment.md` for detailed setup instructions for each scenario.

---

## 🔧 For AI Engineers: Under the Hood

### How It Works

**Phase 0: Requirements**

```
User → Requirements Agent → Conduct discovery
                          → Classify pain points (HIGH/MEDIUM/LOW)
                          → Match to agent patterns
                          → Write user_requirements.json
```

**Phase 1: Architecture**

```
User → Architecture Agent → Read user_requirements.json
                          → Execute 6-step design process
                          → Enforce AWS Well-Architected
                          → Write design_decisions.json
                          → Optionally assemble executive proposals
```

**Phase 2: Engineering**

```
User → Engineering Agent → Read design_decisions.json
                         → Generate agent prompts
                         → Write implementation code
                         → Create UI and demos
                         → Output to outputs/prototypes/
```

**Phase 3: Deployment**

```
User → Deployment Agent → Read prototype from outputs/
                        → Create platform-specific deployment guide
                        → Generate testing strategy
                        → Assess production readiness
```

**Phase 4: Optimization**

```
User → Optimization Agent → Discover system state
                          → Assess against best practices
                          → Identify improvements
                          → Execute safe refactorings
```

### Knowledge Base Schema

**system_config.json** (Read-only for agents)

- Project info, platform settings
- Stakeholders (decision makers, contributors)
- Constraints (budget, timeline, compliance)
- Team capabilities and gaps

**user_requirements.json** (Written by Requirements Agent)

- Customer context
- Use case and business value
- Functional and non-functional requirements
- AI services, data, integrations
- Risks and financial projections

**design_decisions.json** (Written by Architecture Agent)

- Executive summary (for leaders)
- Tech stack selections with rationale
- Architecture diagram and component specifications
- Team composition and hiring needs
- LOE estimates (hours, timeline, complexity)
- Cost projections (development + infrastructure + TCO)
- Project plan (phased roadmap, milestones, risks)

### Anthropic Best Practices Integration

All agents follow Anthropic's recommended patterns:

- **XML tags** for structure: `<role>`, `<capabilities>`, `<instructions>`, `<examples>`, `<thinking>`
- **Tool-based knowledge base access** (conceptual - adapt to platform)
- **Chain-of-thought reasoning** with `<thinking>` tags
- **Concrete examples** in `<example>` tags
- **Multi-shot prompting** for complex workflows

### AWS Well-Architected Enforcement

Architecture Agent validates all designs against:

- **6 Core Pillars:** Operational Excellence, Security, Reliability, Performance Efficiency, Cost Optimization, Sustainability
- **ML Lens:** Machine learning best practices
- **GenAI Lens:** Generative AI specific guidance (RAG, prompt management, responsible AI)

References:

- [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/)
- [Machine Learning Lens](https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/)
- [Generative AI Lens](https://docs.aws.amazon.com/wellarchitected/latest/generative-ai-lens/)

---

## 📖 Documentation Guide

### For Technical Builders (AI Engineers)

**Start here:**

1. `guides/getting_started.md` - Detailed getting started guide
2. `guides/workflow_guide.md` - Complete lifecycle walkthrough
3. `guides/platform_deployment.md` - Platform-specific setup (Cursor, Claude, Bedrock)

**Reference:**

- `docs/agent_design_patterns.md` - 9 reusable AI agent patterns
- Knowledge base JSON files - Schema documentation in comments

**Examples:**

- `guides/examples/financial_operations_assistant.md` - Complete example
- `outputs/prototypes/` - Generated prototypes

### For Business Leaders (CTOs, CFOs, VPs)

**Start here:**

1. `guides/executive_overview.md` - Understanding multi-agent systems and ROI
2. `guides/reading_proposals.md` - How to evaluate technical proposals and plans

**What you'll receive from this system:**

- Executive proposals (go/no-go recommendations)
- Technical project plans (architecture diagrams, timelines, costs)
- Prototypes (working demos you can interact with)

These outputs are designed for **dual-audience**: technical depth for engineers, business clarity for decision-makers.

---

## 🏗️ Complete Workflow Example

**Real-world scenario:** Solo-entrepreneur wants to automate financial operations

```
Day 1: Requirements (15-30 minutes)
├─ Chat with Requirements Agent
├─ Answer discovery questions
└─ Output: user_requirements.json ✅

Day 1-2: Architecture Design (2-4 hours)
├─ Chat with Architecture Agent
├─ Execute 6 design steps:
│  1. Tech stack selection (30 min)
│  2. Architecture diagram (20 min)
│  3. Team composition (20 min)
│  4. LOE estimation (30 min)
│  5. Cost estimation (20 min)
│  6. Project plan (40 min)
└─ Output: design_decisions.json ✅

Day 2: Executive Proposal (30 minutes)
├─ Architecture Agent assembles proposal
└─ Output: Implementation proposal document ✅

[Executive reviews and approves]

Day 3-5: Prototype Development (8-12 hours)
├─ Engineering Agent builds prototype
├─ Generates agent prompts
├─ Writes Python code
├─ Creates Streamlit UI
├─ Builds 5 demo scenarios
└─ Output: outputs/prototypes/financial-operations-assistant/ ✅

Day 5: Deployment (2-4 hours)
├─ Deployment Agent creates deployment guide
├─ Sets up testing strategy
├─ Assesses production readiness
└─ Prototype deployed to Cursor custom chat modes ✅

[Stakeholders interact with prototype, provide feedback]

Day 6-7: Iteration (4-8 hours)
├─ Optimization Agent analyzes feedback
├─ Proposes improvements
└─ Refined prototype ✅

Total Time: 1 week from idea to working multi-agent AI system
```

---

## 🛠️ Maintenance & Optimization

### Keeping This System Current

**The Optimization Agent has a comprehensive self-improvement system:**

**Option 1: System-Wide Optimization (Orchestrated)**

```
You: Load Optimization Agent + Send @improve_ai_architecture_assistant.user.prompt.md

Optimization Agent: [Discovers entire framework]
                   → [Assesses all agents against best practices]
                   → [Executes 6 agent-specific improvements]
                   → [Validates end-to-end workflows]
                   → [Generates comprehensive report]
```

**Option 2: Agent-Specific Improvement (Targeted)**

```
You: Load Prompt Engineering Assistant + Send @improve_requirements_agent.user.prompt.md

Prompt Engineering Assistant: [Focuses on Requirements Agent]
                             → [Domain-specific improvements]
                             → [Validation & testing]
                             → [Independent improvement report]
```

**Key Features:**

- ✅ **Context-Agnostic:** Works with Optimization Agent OR Prompt Engineering Assistant
- ✅ **Loosely Coupled:** Each improvement prompt is independent
- ✅ **Recursion Safe:** Iteration tracking prevents infinite loops
- ✅ **Platform-Agnostic:** Works across Cursor, GitHub Copilot, AWS Bedrock

**Recommended optimization cycle:** Quarterly or after 5+ project uses

### Contributing Improvements

If you discover improvements:

1. Use Optimization Agent to analyze
2. Create proposals with evidence
3. Test thoroughly before committing
4. Update documentation alongside code

---

## ❓ FAQ

**Q: Do I need to use all agents?**  
A: No! Use Supervisor Agent for guidance, or jump directly to the agent you need. The system is flexible.

**Q: Can I use this for non-AI systems?**  
A: The Requirements and Architecture agents work for any software system, but the examples focus on GenAI.

**Q: What if I only need architecture diagrams?**  
A: Use Architecture Agent directly with the architecture_diagram_generation user prompt.

**Q: How do I customize this for my organization?**  
A: Edit `knowledge_base/system_config.json` with your platform, constraints, and preferences.

**Q: What LLM models work best with this?**  
A: Designed for Claude (Sonnet, Opus) but works with GPT-4, Gemini, or other LLMs. Anthropic patterns are platform-agnostic.

**Q: Can this run locally for privacy?**  
A: Yes! Use local LLMs (Ollama) and file-based knowledge base. See platform_deployment guide.

**Q: How do proposals work?**  
A: Architecture Agent assembles proposals from knowledge base data. You present to executives, they approve/reject, then Engineering Agent builds if approved.

---

## 🤝 Support & Resources

### Learning Resources

- **Anthropic Prompt Engineering:** <https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering>
- **AWS Well-Architected:** <https://aws.amazon.com/architecture/well-architected/>
- **AWS Multi-Agent Orchestration:** <https://aws.amazon.com/solutions/guidance/multi-agent-orchestration-on-aws/>
- **Microsoft TDSP:** <https://github.com/Azure/Microsoft-TDSP/>

### Getting Help

- Check `guides/` directory for detailed documentation
- Review examples in `guides/examples/`
- Use Optimization Agent to analyze issues
- Review `docs/agent_design_patterns.md` for architecture patterns

---

## 🎉 Success Stories

**Expected outcomes using this system:**

- ⚡ **Faster design:** 2-4 hours for complete architecture (vs. days of manual work)
- 💰 **Cost clarity:** Accurate estimates prevent budget overruns
- 🎯 **Better decisions:** Evidence-based recommendations, not guesswork
- 🚀 **Rapid prototyping:** Working systems in 1 week (vs. months)
- 📈 **Continuous improvement:** Optimization Agent keeps systems current

---

## 📋 License

[Your license here]

---

## 🙏 Acknowledgments

This system incorporates best practices from:

- AWS Well-Architected Framework
- Anthropic prompt engineering guidelines
- Microsoft Team Data Science Process (TDSP)
- MLOps.org standards
- AWS Multi-Agent Orchestration patterns
- Strands Agents SDK principles

Inspired by: [financial-assistant-for-families](https://github.com/Modular-Earth-LLC/financial-assistant-for-families)

---

**Version:** 1.1  
**Last Updated:** 2025-10-04  
**Status:** Production-ready with comprehensive self-improvement system

---

**Ready to build your first AI system? Start with the Supervisor Agent and say "I want to build an AI system" 🚀**
