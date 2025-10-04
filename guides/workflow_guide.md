# Complete Workflow Guide - AI Architecture Assistant

**Purpose:** Step-by-step guide through the complete AI system design lifecycle  
**Time:** 2-3 weeks from idea to deployed prototype  
**Example:** Financial Operations Assistant for Solo-Entrepreneurs

---

## Overview

This guide walks you through using the AI Architecture Assistant to design, build, and deploy a complete AI system. We'll use the **Financial Operations Assistant** as our example throughout.

---

## Workflow Phases

```
Phase 0: Requirements (15 min - 2 hrs)
    ↓ user_requirements.json
Phase 1: Architecture (2-4 hrs)
    ↓ design_decisions.json
Phase 2: Proposals (30 min)
    ↓ Pitch deck or Internal proposal
Phase 3: Engineering (1-2 weeks)
    ↓ outputs/prototypes/[project]/
Phase 4: Deployment (2-4 hrs)
    ↓ Deployed system
Phase 5: Optimization (ongoing)
    ↓ Improved system
```

---

## Phase 0: Requirements Discovery

**Agent:** Requirements Agent (`ai_agents/requirements_agent.system.prompt.md`)

### Step 1: Choose Discovery Method

**Option A: Quick Discovery (15 min) - RECOMMENDED FOR FIRST PROJECT**
- **User Prompt:** `user_prompts/requirements/quick_discovery.user.prompt.md`
- **Best for:** Solo-entrepreneurs, simple use cases
- **Process:** Answer 10 questions
- **Output:** Complete requirements in 15 minutes

**Option B: Standard Discovery (30-45 min)**
- **User Prompt:** `user_prompts/requirements/standard_discovery.user.prompt.md`
- **Best for:** Small to medium teams
- **Process:** 4-section structured interview

**Option C: Comprehensive Workshop (90 min)**
- **User Prompt:** `user_prompts/requirements/comprehensive_workshop.user.prompt.md`
- **Best for:** Enterprise, multi-stakeholder

### Step 2: Run Discovery

**In Cursor:**
1. Open custom chat with Requirements Agent
2. Copy `quick_discovery.user.prompt.md` contents
3. Paste into chat
4. Answer the 10 questions

**Example (Financial Operations):**
```
Q1: What problem are you solving?
> "I spend 10 hours/week on invoicing, expense tracking, and financial reports"

Q2: How do you handle this today?
> "QuickBooks for invoicing, Excel for expenses, manual P&L compilation"

[... continue through Q10]
```

### Step 3: Review Requirements Output

```
✅ Knowledge base updated: knowledge_base/user_requirements.json

Review the generated requirements summary:
- Problem clearly stated?
- Business value quantified? ($60K/year for financial ops example)
- AI suitability assessed? (HIGH for financial ops)
- Ready for architecture? (COMPLETE status)
```

---

## Phase 1: Architecture Design

**Agent:** Architecture Agent (`ai_agents/architecture_agent.system.prompt.md`)

### Complete 6-Step Design Process

**Step 1: Tech Stack Selection (30 min)**
- **User Prompt:** `user_prompts/architecture/tech_stack_selection.user.prompt.md`
- **Output:** Technology recommendations with rationale
- **Saves to:** design_decisions.json → tech_stack

**Example Output:**
```
LLM: Claude Sonnet 3.5
Backend: Python + FastAPI
Frontend: Streamlit
Database: Local JSON/SQLite
Cost: ~$100-150/month
```

---

**Step 2: Architecture Diagram (20 min)**
- **User Prompt:** `user_prompts/architecture/architecture_diagram_generation.user.prompt.md`
- **Choose platform:** Mermaid (recommended), ASCII, Lucidchart, draw.io, Google Draw
- **Output:** Visual system architecture
- **Saves to:** design_decisions.json → architecture_design, outputs/presentations/[project]/diagrams/

**Example:** Multi-agent diagram showing Operations Agent + Analytics Agent

---

**Step 3: Team Composition (20 min)**
- **User Prompt:** `user_prompts/architecture/team_composition.user.prompt.md`
- **Output:** Required roles, skills, hiring needs
- **Saves to:** design_decisions.json → team_composition

**Example:** 1-2 engineers, 4-6 weeks, Python skills needed

---

**Step 4: LOE Estimation (30 min)**
- **User Prompt:** `user_prompts/architecture/loe_estimation.user.prompt.md`
- **Output:** Engineering hours, timeline, complexity
- **Saves to:** design_decisions.json → estimates

**Example:** 320 hours, 6 weeks, Medium complexity

---

**Step 5: Cost Estimation (20 min)**
- **User Prompt:** `user_prompts/architecture/cost_estimation.user.prompt.md`
- **Output:** Development + infrastructure + TCO + ROI
- **Saves to:** design_decisions.json → costs

**Example:** $65K development + $150/month operations, 100% Year 1 ROI

---

**Step 6: Project Plan (40 min)**
- **User Prompt:** `user_prompts/architecture/project_plan_generation.user.prompt.md`
- **Output:** Phased roadmap, milestones, risks
- **Saves to:** design_decisions.json → project_plan

**Example:** Phase 1 (MVP 4 weeks), Phase 2 (API integration 2 weeks)

---

### Review Architecture Outputs

**Check:** `outputs/presentations/[project-name]/`
```
architecture/
├── tech_stack_selection.md
├── architecture_diagram.mermaid
├── team_composition.md
├── loe_estimates.md
├── cost_analysis.md
└── project_plan.md
```

---

## Phase 2: Proposal Assembly

**Agent:** Architecture Agent (assembly mode)

### Choose Proposal Type

**Option A: Pitch Deck (for clients/investors)**
- **User Prompt:** `user_prompts/proposals/pitch_deck_assembly.user.prompt.md`
- **Format:** 15-slide presentation
- **Focus:** ROI, value proposition, technical credibility
- **Output:** `outputs/presentations/[project]/proposals/pitch_deck.md`

**Option B: Internal Proposal (for executives)**
- **User Prompt:** `user_prompts/proposals/internal_proposal_assembly.user.prompt.md`
- **Format:** 18-slide presentation + 2-page executive summary
- **Focus:** Strategic alignment, change management, comprehensive risk
- **Output:** `outputs/presentations/[project]/proposals/internal_proposal.md`

### Assemble Proposal

**Process:**
1. Architecture Agent reads from knowledge base
2. Reads from `outputs/presentations/[project]/`
3. Assembles into presentation format
4. Generates Markdown → Convert to PowerPoint/Google Slides

**Review before presenting to stakeholders!**

---

## Phase 3: Engineering (Prototype Development)

**Agent:** Engineering Agent (`ai_agents/engineering_agent.system.prompt.md`)

### Build Prototype

**Process:**
1. Engineering Agent reads design_decisions.json
2. Generates agent prompts for YOUR system
3. Writes implementation code
4. Creates UI (Streamlit/React/CLI)
5. Builds demo scenarios
6. Outputs to: `outputs/prototypes/[project-name]/`

**Timeline:** 1-2 weeks depending on complexity

### Prototype Structure

```
outputs/prototypes/financial-operations-assistant/
├── README.md                  # Quick start guide
├── requirements.txt           # Dependencies
├── .env.example              # Configuration template
├── prompts/
│   ├── financial_operations_agent.md
│   └── analytics_agent.md
├── src/agents/
│   ├── financial_operations.py
│   └── analytics.py
├── ui/streamlit_app.py
├── demos/demo_scenarios.py
└── docs/
```

### Test Prototype

```bash
cd outputs/prototypes/financial-operations-assistant/
pip install -r requirements.txt
cp .env.example .env
# Add your ANTHROPIC_API_KEY to .env
streamlit run ui/streamlit_app.py
python demos/demo_scenarios.py
```

---

## Phase 4: Deployment

**Agent:** Deployment Agent (`ai_agents/deployment_agent.system.prompt.md`)

### Deploy to Platform

**Choose target platform** (from system_config.json):

**Cursor:** Copy agent prompts to custom chat modes  
**Claude Projects:** Upload prompts + knowledge base  
**AWS Bedrock:** Deploy as multi-agent system  
**Self-hosted:** Ollama + Open WebUI

**Process:**
1. Deployment Agent reads design_decisions.json
2. Creates platform-specific deployment guide
3. Generates testing strategy
4. Assesses production readiness

**Output:** Deployed prototype ready for stakeholder demos

---

## Phase 5: Optimization

**Agent:** Optimization Agent (`ai_agents/optimization_agent.system.prompt.md`)

### Continuous Improvement

**User Prompt:** `user_prompts/optimization/system_optimization.user.prompt.md`

**Process:**
1. Optimization Agent discovers current system state
2. Assesses against best practices
3. Identifies improvement opportunities
4. Proposes prioritized optimizations
5. Executes safe, incremental improvements

**Frequency:** Monthly or quarterly

---

## Example: Financial Operations Assistant (Complete Flow)

### Day 1: Requirements (15 minutes)

```
You → Supervisor Agent: "I want to build an AI system"
Supervisor → Requirements Agent (Quick Discovery)

[10 questions about financial admin pain points]

Result: user_requirements.json populated
- Problem: 10 hrs/week on financial tasks
- Value: $60K/year opportunity cost
- AI Suitability: HIGH
```

### Day 1-2: Architecture (2-3 hours)

```
You → Architecture Agent: "Design the architecture"

Step 1: Tech Stack → Claude Sonnet + Python + Streamlit
Step 2: Diagram → Multi-agent architecture (2 agents)
Step 3: Team → 2 engineers, 6 weeks
Step 4: LOE → 320 hours
Step 5: Cost → $65K dev + $150/mo ops
Step 6: Plan → Phased roadmap

Result: design_decisions.json complete
Result: outputs/presentations/financial-operations-assistant/ populated
```

### Day 2: Proposal (30 minutes)

```
You → Architecture Agent: "Create pitch deck"

Assembly: Reads knowledge base + presentation assets
Generates: 15-slide pitch deck

Result: pitch_deck.md ready for clients/investors
```

### Day 3-10: Engineering (1-2 weeks)

```
You → Engineering Agent: "Build the prototype"

Generates:
- 2 agent prompts (Operations, Analytics)
- Python implementation (~800 lines)
- Streamlit UI
- 5 demo scenarios
- Complete documentation

Result: outputs/prototypes/financial-operations-assistant/ complete
```

### Day 10: Deployment (2-4 hours)

```
You → Deployment Agent: "Deploy to Cursor"

Creates: Cursor custom chat mode setup guide
Tests: UAT scenarios
Assesses: Production readiness (65% - prototype level)

Result: Prototype deployed and accessible
```

### Ongoing: Optimization

```
Month 1, 3, 6: Optimization Agent

Discovers: Current system performance
Proposes: Cost reductions (use Haiku for categorization = 60% savings)
Implements: Safe improvements

Result: Continuously improving system
```

---

## Tips for Success

**Do:**
- ✅ Follow the phases in order (requirements → architecture → engineering)
- ✅ Use the financial operations example first to learn the system
- ✅ Review knowledge base files after each phase
- ✅ Commit to git after major milestones
- ✅ Test thoroughly before presenting to stakeholders

**Don't:**
- ❌ Skip requirements (leads to rework)
- ❌ Rush architecture (quality design prevents expensive mistakes)
- ❌ Deploy without testing (validate with demos first)
- ❌ Ignore the knowledge base (it maintains context)

---

## Troubleshooting

**Problem:** Requirements Agent can't find knowledge base  
**Solution:** Run from repository root, check paths are `knowledge_base/user_requirements.json`

**Problem:** Architecture steps producing errors  
**Solution:** Ensure previous step completed (check design_decisions.json._metadata)

**Problem:** Engineering Agent doesn't know what to build  
**Solution:** Verify design_decisions.json is complete (all 6 steps)

**Problem:** Proposals missing data  
**Solution:** Complete all architecture steps first, then assemble

---

## Quick Reference

**Start here:** Supervisor Agent (`supervisor_agent.system.prompt.md`)  
**Knowledge base:** `knowledge_base/` (JSON files)  
**User prompts:** `user_prompts/` (task-specific instructions)  
**Outputs:** `outputs/presentations/` and `outputs/prototypes/`  
**Reference:** `docs/agent_design_patterns.md`

**Questions?** See README.md or guides/executive_overview.md

---

**Version:** 1.0  
**Last Updated:** 2025-10-03  
**Estimated Time:** 2-3 weeks from idea to deployed prototype
