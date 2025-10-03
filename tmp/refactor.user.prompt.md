# AI Architecture Assistant - System Refactoring & Simplification

## Context & Current State

The **AI-architecture-assistant** repository has evolved through multiple iterations and merges, resulting in:

**Problems:**

- **Over-engineering:** Too many similar prompts with overlapping purposes (3+ architecture system prompts, redundant workflows)
- **Confusing structure:** Files scattered across directories without clear workflow organization
- **Unclear separation of concerns:** Agents and prompts duplicate capabilities instead of working in concert
- **Missing knowledge management:** No shared data model or knowledge base for requirements/decisions
- **Convoluted documentation:** Multiple merges created messy, repetitive docs that confuse users
- **Unclear target audience:** Documentation doesn't speak to specific platforms or concrete use cases

**Current repository structure** (simplified):

```text
/requirements/        # Discovery and requirements gathering
/architecture/        # 12+ files including 3 similar system prompts
/proposals/          # Recently added executive approval workflow
/development/        # Prototype building
/delivery/           # Demo and handoff
/optimization/       # System optimization prompt
/examples/           # Example workflows
```

**Target users:**

**Primary Users (Builders):**

- Junior to mid-level AI engineers and architects at startups and small businesses
- Working primarily in Cursor and VS Code with AI agent augmentation
- Deploying to Anthropic Claude Projects/Workspaces or AWS Bedrock
- Need simple, intuitive workflows without deep AI expertise
- Building systems for both internal use and external clients

**Secondary Users (Decision Makers & Stakeholders):**

- **CEOs, CTOs, CFOs** - Approve budgets, funding, and strategic direction
- **VPs and Directors** - Provide requirements, validate business value, approve project scope
- **Product Managers** - Define use cases and success criteria during discovery
- **Domain Experts & Business Analysts** - Contribute technical and business requirements
- **Finance Teams** - Review cost estimates and ROI projections
- **Executive Leadership** - Make final go/no-go decisions based on proposals

**Key distinction:**

- **Builders** use the system to create architectures, estimates, and proposals
- **Decision Makers** consume outputs (proposals, plans, estimates) to make informed decisions
- System must serve BOTH audiences: technical depth for builders, business clarity for leadership

---

## Vision: Simplified Multi-Agent Architecture

**Goal:** Transform this into a clean, intuitive multi-agent system following these principles from leading AI research and providers (Anthropic, AWS, Mistral):

### Core Architecture Pattern

**Single-Agent-Per-Phase + Multi-Shot Prompting:**

```text
Phase 1: Requirements Agent
└─ Gathers requirements via discovery, stores in knowledge base

Phase 2: Architecture Agent  
└─ Designs system using requirements + user prompt library
   ├─ Tech stack selection (user prompt)
   ├─ Team composition (user prompt)
   ├─ LOE estimation (user prompt)
   ├─ Cost estimation (user prompt)
   └─ Project plan generation (user prompt)

Phase 3: Engineering Agent
└─ Builds prototypes and implementations

Phase 4: Deployment Agent
└─ Handles deployment and testing

Phase 5: Optimization Agent
└─ Improves entire system periodically
```

**Key principles:**

- **One system prompt per agent** (clear identity and role)
- **Shared knowledge base** for requirements and decisions (CRUD operations via tool calls)
- **JSON for data storage** - All knowledge base and configuration files use JSON format (not YAML) for better parsing, validation, and tool integration
- **Anthropic best practices** - Follow Anthropic's recommended prompt formats, XML tags for structure, and tool use patterns from their API documentation
- **Shared system configuration** for universal meta-data and instructions like constraints, platform settings, guidelines, and guardrails relevant to all agents and prompts throughout the repository. This is a read-only file for all agents to reference. AI engineers will updates this manually or as a human in the loop with coding agents.
- **User prompt library** for specific tasks (multi-shot prompting). At first, users will copy these prompts into chat interfaces, like Cursor's AI pane or Github copilot, backed by Agents or Chatmodes defined by the system prompts. This prompt library may also be referenced and queried by the agents themselves to grab relevant instructions based on user interactions the agents (system prompts) have with the user.
- **Clear workflow sequencing** (outputs from one phase feed the next)
- **Separation of concerns** (no capability overlap between agents)
- **Tool-based knowledge base access** - Agents use defined tools/functions to read and write to knowledge base files, following Anthropic's function calling patterns

**Reference pattern:** Similar to <https://github.com/Modular-Earth-LLC/job-finding-assistant> structure, though that is a consumer facing product and this is a developer facing product.

---

## Refactoring Tasks

### Task 1: Standardize File Naming

**Objective:** Make all files follow consistent naming conventions

**Actions:**

- Rename all files to use this pattern:
  - System prompts: `{descriptive_name}.system.prompt.md`
  - User prompts: `{descriptive_name}.user.prompt.md`
  - Guides/templates: `{descriptive_name}.guide.md` or `{descriptive_name}.template.md`

**Examples:**

- `technical-architect-agent.prompt.md` → `architecture_agent.system.prompt.md`
- `tech_stack_generation.user.prompt.md` → `tech_stack_selection.user.prompt.md` (clearer name)

**Success criteria:**

- All prompts follow naming convention consistently
- Names are descriptive and indicate purpose clearly
- Easy to distinguish system prompts from user prompts at a glance

---

### Task 2: Identify and Consolidate ALL Redundant Prompts

**Objective:** Systematically identify and eliminate redundancy across the ENTIRE repository, consolidating similar prompts into focused agents with clear separation of concerns

**Important:** This task requires comprehensive analysis. The examples below are illustrative, but you MUST identify ALL redundancies throughout the repository, not just those explicitly listed here.

---

#### Example 1: Architecture System Prompts (HIGH REDUNDANCY)

**Current redundancy:**

- `architecture/AI-architecture_assistant.system.prompt.md`
- `architecture/solutions-architect-system.prompt.md`  
- `architecture/technical-architect-agent.prompt.md`

**Problem:** All three serve overlapping purposes:

- Designing system architectures
- Creating technical designs
- Generating project plans
- Making technology recommendations
- Each contains 400-700 lines with significant overlap

**Consolidation approach:**

- **Analyze overlap:** Compare all three, identify unique capabilities
- **Design single architecture agent:** Create one unified `architecture_agent.system.prompt.md` that:
  - Takes requirements from knowledge base as input
  - Orchestrates user prompts for specific tasks (tech stack, LOE, costs, plans)
  - Generates architecture designs and Mermaid diagrams
  - Outputs decisions back to knowledge base
  - Preserves all unique capabilities (executive proposals, diagrams, LOE)
- **Delete redundant files:** Remove 2 obsolete system prompts after validation

---

#### Example 2: Requirements & Discovery Prompts (MEDIUM REDUNDANCY)

**Current redundancy:**

- `requirements/discovery-agent.prompt.md` - AI assistant for discovery sessions
- `requirements/requirements-extraction.prompt.md` - Structure meeting notes
- `requirements/quick-start-wizard.prompt.md` - 15-minute onboarding
- `requirements/discovery-guide.md` - 30-minute discovery process guide
- `requirements/workshop-guide.md` - 90-minute comprehensive workshop guide

**Problem:**

- Multiple approaches to requirements gathering without clear when-to-use guidance
- Overlap between `discovery-agent` and `requirements-extraction` (both structure requirements)
- `quick-start-wizard` duplicates some discovery agent capabilities
- Guides contain similar content about asking questions and capturing requirements
- Total ~1,500 lines across 5 files with overlapping purposes

**Consolidation approach:**

- **Single requirements agent:** Consolidate `discovery-agent` and `requirements-extraction` into one `requirements_agent.system.prompt.md` that can:
  - Facilitate discovery (interactive questioning)
  - Extract requirements from unstructured notes
  - Structure data into knowledge base format
  - Adapt approach based on project size (quick vs. comprehensive)
- **User prompts for scenarios:** Create distinct user prompts:
  - `quick_discovery.user.prompt.md` - 15-minute rapid assessment
  - `standard_discovery.user.prompt.md` - 30-minute focused session
  - `comprehensive_workshop.user.prompt.md` - 90-minute deep-dive
  - `extract_from_notes.user.prompt.md` - Post-meeting structuring
- **Single guide:** Merge `discovery-guide.md` and `workshop-guide.md` into unified `requirements_workflow.guide.md` showing when to use each approach
- **Delete:** `quick-start-wizard.prompt.md` (capabilities absorbed into requirements agent + user prompts)

---

#### Example 3: Proposal Prompts vs. Architecture Prompts (OVERLAP)

**Current redundancy:**

- `proposals/discovery-assessment-proposal.prompt.md`
- `proposals/poc-mvp-implementation-proposal.prompt.md`
- `proposals/project-proposal-template.prompt.md`
- These overlap with: `architecture/technical_project_plan_generation.user.prompt.md`, `architecture/project_cost_estimation.user.prompt.md`, `architecture/team_composition_generation.user.prompt.md`

**Problem:**

- Proposal prompts contain sections on architecture, costs, team composition, timelines
- This duplicates content in dedicated architecture user prompts
- Proposals should CONSUME outputs from architecture prompts, not recreate them
- Users confused about which to use when

**Consolidation approach:**

- **Reframe proposals as assembly prompts:** Transform proposal prompts to:
  - READ from knowledge base (requirements, architecture decisions, estimates)
  - ASSEMBLE information into executive-ready format
  - ADD proposal-specific content (business case, ROI, approval process)
  - Not duplicate detailed technical design or estimation
- **Clear workflow:** Architecture prompts run FIRST → outputs to knowledge base → proposal prompts assemble
- **Example refactor:**

  ```
  OLD: "proposals/poc-mvp-implementation-proposal.prompt.md" 
       - Contains tech stack selection logic (586 lines)
  
  NEW: "proposals/implementation_proposal_assembly.user.prompt.md"
       - Reads tech stack from knowledge_base/decisions.json via tool calls
       - Focuses on executive summary, business case, approval workflow (250 lines)
  ```

---

#### Example 4: Cost Estimation Redundancy (SCATTERED)

**Current redundancy:**

- `architecture/project_cost_estimation.user.prompt.md` - Infrastructure and development costs
- Proposal prompts each contain their own cost sections
- Tech stack prompt has cost estimation guidance
- LOE prompt calculates hours (which could convert to costs)

**Problem:**

- Cost estimation logic scattered across 4+ files
- Inconsistent approaches to calculating costs
- Users don't know which to use for what purpose

**Consolidation approach:**

- **Single authoritative cost user prompt:** One `cost_estimation.user.prompt.md` that:
  - Calculates infrastructure costs (from tech stack decisions)
  - Calculates development costs (from LOE hours + team composition)
  - Outputs to knowledge base for proposals to reference
  - Used by architecture agent, referenced by proposals
- **Remove cost sections from:** Proposal prompts (they read from knowledge base instead)
- **Clarify in tech stack prompt:** "See cost_estimation.user.prompt.md for detailed cost analysis"

---

#### Example 5: Guide and Template Redundancy

**Current redundancy:**

- `requirements/requirements-template.md`
- `architecture/architecture-template.md`
- Proposal prompts contain template sections
- Guides reference templates inconsistently

**Problem:**

- Templates scattered across directories
- Some templates embedded in prompts vs. standalone files
- Unclear which template to use when

**Consolidation approach:**

- **Centralized templates directory:** Move all to `/templates/`
  - `requirements_output.template.md`
  - `architecture_design.template.md`
  - `proposal_executive_summary.template.md`
- **Agents reference templates:** System prompts point to templates, don't embed them
- **Single templates guide:** `guides/using_templates.md` explains all templates

---

#### Comprehensive Consolidation Process

**Step 1: Discovery (You MUST do this)**

Systematically analyze the entire repository:

```bash
# Find all prompt files
find . -name "*.prompt.md" -o -name "*agent*.md" -o -name "*assistant*.md"

# Find all guides
find . -name "*guide*.md" -o -name "*template*.md"

# Analyze each file for:
1. Primary purpose - What is its core job?
2. Capabilities - What can it do?
3. Overlap - Which other files do similar things?
4. Dependencies - What does it reference?
5. Usage - How is it actually used in workflows?
```

**Step 2: Categorization**

Create a redundancy map:

| File | Type | Primary Purpose | Overlaps With | Keep/Merge/Delete |
|------|------|----------------|---------------|-------------------|
| `AI-architecture_assistant.system.prompt.md` | System | Architecture design | 2 other arch prompts | **Merge** |
| `solutions-architect-system.prompt.md` | System | Architecture + proposals | Above + proposals | **Merge** |
| `technical-architect-agent.prompt.md` | System | Architecture + Mermaid | Above 2 | **Keep** (base) |
| `discovery-agent.prompt.md` | System | Discovery sessions | requirements-extraction | **Merge** |
| `requirements-extraction.prompt.md` | User | Extract requirements | discovery-agent | **Merge** |
| ... | ... | ... | ... | ... |

**Step 3: Consolidation Plan**

For each redundant group:

1. **Identify canonical version** - Which file is the best starting point?
2. **Extract unique capabilities** - What does each file do that others don't?
3. **Design consolidated prompt** - How to preserve all functionality?
4. **Plan migration** - How to move content and update references?
5. **Validate preservation** - How to ensure nothing is lost?

**Step 4: Execute Consolidation**

For each consolidation:

1. Create new consolidated file
2. Migrate unique capabilities
3. Update all cross-references
4. Test with example workflows
5. Delete obsolete files
6. Update documentation

**Step 5: Validate**

After all consolidations:

- [ ] Run complete workflow end-to-end
- [ ] Verify all capabilities still accessible
- [ ] Check all documentation links work
- [ ] Confirm file count reduced significantly
- [ ] Test that new structure is clearer

---

### Success Criteria

**Quantitative:**

- ✅ Reduce system prompts from 10+ to ~5 focused agents
- ✅ Reduce total prompt files by 30-50%
- ✅ Eliminate duplicate content (measured by similar paragraphs across files)
- ✅ Each agent <500 lines (focused, not bloated)

**Qualitative:**

- ✅ Each agent has ONE clear purpose
- ✅ No capability duplication across agents
- ✅ All previous functionality preserved and accessible
- ✅ Users can easily determine which agent to use when
- ✅ Workflow sequences are clear and documented
- ✅ Knowledge base properly integrates all agents

**Validation:**

- ✅ Complete example workflow runs successfully
- ✅ Junior engineer can understand which files to use
- ✅ No broken references or missing capabilities
- ✅ Documentation accurately reflects new structure

---

### Task 3: Reorganize Repository Structure

**Objective:** Group files logically by workflow phase and file type

**Current issues:**

- Architecture directory has 12+ files (mix of system prompts, user prompts, guides)
- Proposals directory duplicates some architecture capabilities
- No clear visual workflow progression through directories

**Proposed structure:**

```
/ai_agents/                    # All system prompts (agent definitions)
├── requirements_agent.system.prompt.md
├── architecture_agent.system.prompt.md
├── engineering_agent.system.prompt.md
├── deployment_agent.system.prompt.md
└── optimization_agent.system.prompt.md

/user_prompts/                 # Task-specific instructions for agents
├── requirements/
│   ├── discovery_session.user.prompt.md
│   ├── extract_requirements.user.prompt.md
│   └── validate_requirements.user.prompt.md
├── architecture/
│   ├── tech_stack_selection.user.prompt.md
│   ├── team_composition.user.prompt.md
│   ├── loe_estimation.user.prompt.md
│   ├── cost_estimation.user.prompt.md
│   └── project_plan_generation.user.prompt.md
├── engineering/
│   └── prototype_builder.user.prompt.md
└── proposals/                 # Executive approval workflows
    ├── discovery_proposal.user.prompt.md
    └── implementation_proposal.user.prompt.md

/knowledge_base/               # Shared data store (NEW)
├── system_config.json         # Platform configs, constraints
├── requirements.json          # Current project requirements
└── decisions.json             # Architecture decisions log

/templates/                    # Reusable templates
├── requirements_template.md
├── architecture_template.md
└── proposal_template.md

/guides/                       # User documentation
├── getting_started.md
├── workflow_guide.md
├── platform_deployment.md     # Cursor, Claude, Bedrock
└── examples/
    └── email_automation_example.md

/docs/                         # Reference documentation
└── agent_design_patterns.md
```

**Migration approach:**

1. Create new directory structure
2. Move/consolidate files to appropriate locations
3. Update all cross-references and links
4. Delete empty directories and redundant files
5. Update README.md to reflect new structure

**Success criteria:**

- Clear workflow progression visible in directory structure
- Easy to find: agents vs. user prompts vs. templates vs. guides
- No redundant or sparse directories
- All links updated and working

---

### Task 4: Implement Knowledge Base Pattern

**Objective:** Create shared knowledge base that all agents read from and write to

**Reference pattern:** <https://github.com/Modular-Earth-LLC/job-finding-assistant/tree/main/inputs/knowledge-bases>

**Why needed:**

- Ensures consistency across workflow phases
- Prevents information loss between agents
- Enables traceability of requirements → architecture → implementation
- Supports documentation generation at the end

**Knowledge base design:**

All knowledge base files use **JSON format** for better parsing, validation, and integration with AI tools following Anthropic's recommendations.

**1. System Configuration** (`knowledge_base/system_config.json`):

```json
{
  "project": {
    "name": "",
    "type": "",  // web_app, api, data_pipeline, ml_model
    "organization": ""  // internal project or client name
  },
  "platform": {
    "target": "",  // cursor, claude_projects, aws_bedrock
    "deployment": ""  // cloud, on_prem, hybrid
  },
  "stakeholders": {
    "decision_makers": [
      {
        "role": "",  // CEO, CFO, CTO, VP
        "name": "",
        "approval_authority": ""  // budget, technical, strategic
      }
    ],
    "contributors": [
      {
        "role": "",  // PM, domain expert, analyst
        "name": "",
        "expertise": ""
      }
    ]
  },
  "constraints": {
    "budget_range": "",  // executive-approved budget
    "timeline_deadline": "",  // business-driven deadline
    "compliance": [],  // regulatory requirements
    "strategic_priority": ""  // high, medium, low
  },
  "team": {
    "size": 0,
    "experience_level": "",
    "skills": [],
    "availability": ""  // capacity constraints
  }
}
```

**2. Requirements Data** (`knowledge_base/requirements.json`):

```json
{
  "customer": {
    "legal_name": "",  // Customer's legal business name
    "brand_name": "",  // Customer's public-facing brand name
    "market_position": "",  // Strategic market position and business model
    "ai_adoption_stage": "",  // Current stage of AI adoption (beginner, intermediate, advanced)
    "business_model": "",  // How the customer makes money
    "key_stakeholders": [],  // Important people involved in the project
    "ai_history": ""  // Previous AI projects and experience
  },
  "use_case": {
    "title": "",  // Title of the specific use case
    "summary": "",  // Brief description of what the system will do
    "business_benefits": "",  // Quantifiable benefits to the customer's business
    "product_service_domain": "",  // Specific product, service, or internal tool domain
    "workflow_steps": [],  // Numbered steps describing the high-level workflow
    "target_users": [],  // Who will use this system
    "user_experience_goals": ""  // How user experience will improve
  },
  "business": {
    "problem": "",  // Business problem from leadership
    "current_state": "",  // How it's done today, costs, pain points
    "desired_outcome": "",  // What success looks like
    "business_value": {
      "revenue_impact": "",  // Increase/protect revenue
      "cost_savings": "",  // Reduce operational costs
      "strategic_value": "",  // Competitive advantage, market position
      "efficiency_gains": ""  // Time saved, automation
    },
    "success_metrics": [],  // KPIs that matter to leadership (ROI metrics)
    "challenges": [],  // Current challenges (e.g., hallucinations, consistency issues)
    "opportunities": [],  // Identified opportunities (e.g., reduce documentation time)
    "stakeholder_inputs": [  // Who provided what requirements
      {
        "stakeholder": "",  // CEO, CFO, PM, domain expert
        "requirements": [],
        "priorities": []
      }
    ]
  },
  "technical": {
    "functional_requirements": [],
    "non_functional_requirements": [],
    "ai_services": [],  // AI services, libraries, and frameworks to evaluate
    "data_assessment": [],  // How data readiness will be assessed (structure, size, completeness)
    "data_sources": [],  // Data sources required for integration
    "api_integrations": [],  // APIs or systems required for integration
    "compliance": [],  // Compliance programs and regulations (HIPAA, GDPR, SOC, PCI)
    "performance_targets": {},
    "evaluation_criteria": "",  // Summarization of evaluation criteria
    "benchmark_metrics": [],  // Quantifiable metrics for benchmarking (accuracy, latency, cost)
    "primary_platform_models": [],  // Models available on primary cloud platform
    "alternative_platform_models": []  // Models from alternative platforms
  },
  "project_scope": {
    "deliverable_format": "",  // 1-5 page report or interactive dashboard
    "level_of_effort": "",  // 1-3 weeks estimate
    "timeline_weeks": 0,
    "models_to_evaluate": [],  // 3-6 AI models or API endpoints to evaluate
    "reference_materials": [],  // Technical documentation referenced
    "reference_architectures": [],  // Reference solution architectures mentioned
    "recommended_cloud_services": [],  // Recommended cloud services
    "other_software_services": []  // Other software services and libraries
  },
  "financial": {
    "expected_roi": "",  // Return on investment projection
    "payback_period": "",  // When investment is recovered
    "total_cost_ownership": "",  // 3-year TCO estimate
    "budget_constraints": ""  // Hard limits from finance
  },
  "risks": {
    "business_risks": [],  // What leadership cares about
    "technical_risks": [],  // What engineers care about
    "mitigation_strategies": [],
    "assumptions": []
  }
}
```

**3. Architecture Decisions** (`knowledge_base/decisions.json`):

```json
{
  "executive_summary": {  // For leadership consumption
    "recommended_approach": "",
    "total_investment": "",  // One-time + ongoing
    "expected_timeline": "",  // Weeks to delivery
    "confidence_level": "",  // High/Medium/Low
    "key_risks": [],
    "go_no_go_recommendation": ""
  },
  "tech_stack": {
    "languages": [],
    "frameworks": [],
    "databases": [],
    "cloud_services": [],
    "rationale": "",  // Technical justification
    "business_rationale": ""  // Why this matters to leadership
  },
  "team_composition": {
    "roles": [],
    "allocation": {},
    "hiring_needs": [],
    "hiring_timeline": "",
    "team_cost_estimate": ""
  },
  "estimates": {
    "total_engineering_hours": 0,
    "timeline_weeks": 0,
    "complexity_rating": "",  // Low/Medium/High/Very High
    "confidence_level": ""  // How certain are we
  },
  "costs": {
    "development_cost": 0,  // Internal time value
    "infrastructure_cost": 0,  // Cloud, services
    "third_party_cost": 0,  // Tools, licenses
    "total_investment": 0,
    "ongoing_monthly_cost": 0,
    "roi_projection": ""
  },
  "model_evaluation": {
    "selected_models": [],  // Final models chosen for evaluation
    "evaluation_methodology": "",  // How models will be tested
    "benchmark_results": {},  // Performance comparison results
    "recommended_model": "",  // Best performing model
    "evaluation_timeline": "",  // How long evaluation will take
    "success_criteria": []  // What constitutes successful evaluation
  },
  "risks_and_mitigation": {
    "technical_risks": [],
    "business_risks": [],
    "mitigation_plans": []
  }
}
```

**Agent CRUD operations via Tools:**

Agents access knowledge base through **tool calls** following Anthropic's function calling patterns:

- **Requirements Agent:** WRITE to `requirements.json` via `write_requirements` tool
- **Architecture Agent:** READ `requirements.json` via `read_requirements` tool, WRITE to `decisions.json` via `write_decisions` tool
- **Engineering Agent:** READ both files, UPDATE `decisions.json` with implementation details
- **All agents:** READ `system_config.json` for constraints and platform info via `read_config` tool

**Tool definitions follow Anthropic's JSON schema format** (see: <https://docs.anthropic.com/en/docs/build-with-claude/tool-use>)

**Example agent integration** (reference <https://github.com/Modular-Earth-LLC/job-finding-assistant/blob/main/AI_assistants/job_market_positioning.system.prompt.md>):

```markdown
## Your Knowledge Base Access

You have access to these tools for interacting with the knowledge base:

### Available Tools:

**read_config**: Read system configuration
- Input: None
- Returns: JSON object from `knowledge_base/system_config.json`

**read_requirements**: Read current requirements
- Input: None  
- Returns: JSON object from `knowledge_base/requirements.json`

**write_decisions**: Write architecture decisions
- Input: `decisions` (JSON object)
- Effect: Writes to `knowledge_base/decisions.json`

**read_decisions**: Read existing decisions
- Input: None
- Returns: JSON object from `knowledge_base/decisions.json`

**Workflow:**
1. Use `read_config` to get constraints and platform settings
2. Use `read_requirements` to get business and technical requirements
3. Generate architecture based on these inputs
4. Use `write_decisions` to save your architecture decisions
5. VALIDATE decisions align with requirements

**Follow Anthropic's tool use patterns:**
- Use XML tags for structured thinking: `<thinking>`, `<analysis>`, `<decision>`
- Request tool use explicitly when needed
- Parse tool results before proceeding
- Handle tool errors gracefully
```

**Success criteria:**

- Knowledge base structure implemented with **JSON files** (not YAML)
- All agents updated to use **tool-based knowledge base access**
- Tools follow **Anthropic's function calling patterns and JSON schemas**
- CRUD operations clearly defined in each agent prompt with tool specifications
- Agents use **XML tags** for structured reasoning (`<thinking>`, `<analysis>`, etc.)
- Data flows documented in workflow guide
- Example project data populated for testing
- Tool definitions validated against Anthropic API documentation

---

### Task 4b: Implement Anthropic Best Practices for Prompt Design

**Objective:** Ensure all system prompts follow Anthropic's recommended formatting, structure, and tool use patterns

**Reference:** <https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering>

**Key Anthropic Recommendations to Implement:**

**1. Use XML Tags for Structure**

Anthropic recommends using XML tags to provide clear structure in prompts:

```markdown
## Your Task

<task_description>
You are an architecture agent that designs AI systems.
</task_description>

<capabilities>
- Design system architectures
- Select technology stacks
- Estimate project timelines
</capabilities>

<instructions>
When a user asks you to design a system:
1. First, use the read_requirements tool to get requirements
2. Then analyze within <thinking> tags
3. Finally, present your recommendation
</instructions>
```

**2. Provide Examples in Prompts**

Use `<example>` tags to show desired behavior:

```markdown
<example>
User: "Design an email automation system"

Agent: <thinking>I should first gather requirements before designing.</thinking>

I'll help you design an email automation system. Let me start by gathering requirements.

<function_calls>
<invoke name="read_requirements">
</invoke>
</function_calls>

[After receiving requirements...]

Based on the requirements, I recommend:
- Tech Stack: Python + LangChain + Claude API
- Architecture: [Details]
- Estimated timeline: 6-8 weeks

<function_calls>
<invoke name="write_decisions">
<parameter name="decisions">{
  "tech_stack": {...},
  "timeline": "6-8 weeks"
}</parameter>
</invoke>
</function_calls>
</example>
```

**3. Chain of Thought with XML Tags**

Use `<thinking>` tags for reasoning (Anthropic's models are trained to recognize these):

```markdown
When user provides requirements:

<thinking>
Let me analyze the requirements:
- They need email automation
- 100 emails per day mentioned
- Integration with Gmail required
- Budget: $5k/month

Based on this, I should:
1. Choose cost-effective LLM (Haiku for high volume)
2. Use Gmail API for integration
3. Estimate ~40 hours development
</thinking>

Based on your requirements, I recommend...
```

**4. Structured Tool Definitions**

Define tools using JSON schema format per Anthropic's specification:

```json
{
  "name": "write_decisions",
  "description": "Write architecture decisions to the knowledge base",
  "input_schema": {
    "type": "object",
    "properties": {
      "decisions": {
        "type": "object",
        "description": "Architecture decisions in JSON format",
        "properties": {
          "tech_stack": {"type": "object"},
          "estimates": {"type": "object"},
          "costs": {"type": "object"}
        },
        "required": ["tech_stack"]
      }
    },
    "required": ["decisions"]
  }
}
```

**5. Use Prefill for Consistency**

In user prompts, guide responses by starting the assistant's message:

```markdown
**User Prompt:**
Generate a tech stack for this project.

**Assistant (prefilled):**
I'll analyze the requirements and recommend a tech stack.

<thinking>
Let me first read the requirements...
```

**6. Clear Role and Formatting Instructions**

```markdown
## Your Response Format

Always structure your responses as:

<thinking>
[Your reasoning process]
</thinking>

**Recommendation:** [Clear, concise recommendation]

**Technical Details:**
- [Detail 1]
- [Detail 2]

<function_calls>
[Any necessary tool calls]
</function_calls>
```

---

**Anthropic-Specific Enhancements to Apply:**

1. **Add XML structure tags** to all system prompts:
   - `<role>`, `<capabilities>`, `<instructions>`, `<examples>`, `<constraints>`

2. **Include thinking prompts** in agent behavior:
   - Instruct agents to use `<thinking>` tags before decisions
   - Show reasoning process transparently

3. **Proper tool definitions** for all knowledge base operations:
   - Define tools with JSON schemas
   - Include descriptions, parameters, required fields
   - Follow Anthropic's tool use documentation

4. **Response formatting guidelines** in each agent:
   - Clear structure expected in outputs
   - Use of XML tags for organization
   - Consistent patterns across agents

5. **Chain-of-thought integration:**
   - Guide agents to reason step-by-step
   - Use `<analysis>`, `<evaluation>`, `<decision>` tags
   - Make reasoning visible to users

**Reference Documentation:**

- Anthropic Prompt Engineering: <https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering>
- Tool Use Guide: <https://docs.anthropic.com/en/docs/build-with-claude/tool-use>
- XML Tag Best Practices: <https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/use-xml-tags>

**Success Criteria:**

- ✅ All system prompts use XML tags for structure
- ✅ Tool definitions follow Anthropic's JSON schema format
- ✅ Agents instructed to use `<thinking>` tags
- ✅ Examples provided using `<example>` tags
- ✅ Response formats clearly specified
- ✅ Validated against Anthropic documentation
- ✅ Compatible with Claude API, Cursor (Claude backend), AWS Bedrock

---

### Task 5: Define Clear Separation of Concerns

**Objective:** Ensure each agent/prompt has unique, non-overlapping responsibilities

**Current issues:**

- User prompts duplicate some agent capabilities
- Workflow sequence unclear (which prompts lead into others)
- Some agents try to do everything vs. orchestrating user prompts

**Clear responsibilities:**

**Requirements Agent** (`requirements_agent.system.prompt.md`):

- **Does:** Facilitates discovery, asks questions, structures data
- **Uses:** `discovery_session.user.prompt.md`, `extract_requirements.user.prompt.md`
- **Outputs:** Writes to `knowledge_base/requirements.json` via tool calls
- **Does NOT:** Make architecture decisions or generate tech stacks

**Architecture Agent** (`architecture_agent.system.prompt.md`):

- **Does:** Orchestrates architecture design, maintains consistency
- **Uses:** Multiple user prompts in sequence:
  1. `tech_stack_selection.user.prompt.md`
  2. `team_composition.user.prompt.md`
  3. `loe_estimation.user.prompt.md`
  4. `cost_estimation.user.prompt.md`
  5. `project_plan_generation.user.prompt.md`
- **Reads:** `knowledge_base/requirements.json`, `system_config.json` via tool calls
- **Writes:** `knowledge_base/decisions.json` via tool calls
- **Does NOT:** Contain detailed tech stack selection logic (that's in user prompts)

**Key principle:**

- System prompts define ROLES and ORCHESTRATION
- User prompts define SPECIFIC TASKS and DETAILED LOGIC
- Multi-shot prompting workflow: User sends sequence of user prompts to agent

**Workflow sequence documentation:**

```text
Architecture Phase Sequence:

1. User: "Use tech_stack_selection.user.prompt.md"
   Agent: Reads requirements → Generates tech stack → Writes to decisions

2. User: "Use team_composition.user.prompt.md"  
   Agent: Reads tech stack decision → Generates team plan → Writes to decisions

3. User: "Use loe_estimation.user.prompt.md"
   Agent: Reads team composition → Estimates effort → Writes to decisions

4. User: "Use cost_estimation.user.prompt.md"
   Agent: Reads tech stack → Calculates costs → Writes to decisions

5. User: "Use project_plan_generation.user.prompt.md"
   Agent: Reads all decisions → Generates comprehensive plan
```

**Success criteria:**

- Each agent has unique, well-defined role
- User prompts work in documented sequences
- No capability duplication across agents or prompts
- Clear workflow documentation showing which prompts feed into others
- Multi-shot prompting pattern clearly explained
- All agents use Anthropic's recommended XML tags and tool patterns

---

### Task 6: Simplify and Rewrite Documentation

**Objective:** Create clear, beginner-friendly documentation from scratch

**Current issues:**

- Multiple merges created redundant content
- Too abstract, not enough concrete examples
- Doesn't speak to target platforms (Cursor, Claude, Bedrock)
- Lost valuable examples and storytelling during iterations

**Target audience specifics:**

**Primary Audience (Technical Builders):**

- **Who:** Junior to mid-level AI engineers and architects at startups/small businesses
- **Experience level:** May be new to AI agent concepts and patterns
- **Tools:** Primarily Cursor and VS Code projects
- **Deployment targets:** Anthropic Claude Projects, AWS Bedrock
- **Need:** Step-by-step guidance with concrete platform examples

**Secondary Audience (Business Decision Makers):**

- **Who:** CEOs, CTOs, CFOs, VPs, Product Managers, Finance Teams
- **Experience level:** Technical understanding varies; may not be developers
- **Tools:** Read proposals, architecture docs, cost estimates (PDF, presentations)
- **Need:** Clear business value, ROI justification, risk assessment, executive summaries
- **Decision context:** Approve/reject projects, allocate budgets, validate strategic alignment

**Documentation must serve BOTH:**

- Technical depth for builders to execute
- Business clarity for leadership to decide
- Translations between technical and business concepts

**New documentation structure:**

**For Technical Builders:**

**1. Getting Started Guide** (`guides/getting_started.md`):

- 15-minute quick start for Cursor users
- "I have a project idea" → working agent in 15 minutes
- Platform-specific setup instructions
- First successful workflow walkthrough

**2. Workflow Guide** (`guides/workflow_guide.md`):

- Visual workflow diagram showing all phases
- Step-by-step for complete project lifecycle
- When to use which agent and which user prompts
- Knowledge base interaction patterns
- Concrete example: "Building an email automation agent"

**3. Platform Deployment Guide** (`guides/platform_deployment.md`):

- **Cursor setup:** How to create custom agents with these system prompts
- **Claude Projects:** How to set up project knowledge and custom instructions
- **AWS Bedrock:** How to deploy as agent with knowledge base
- Real screenshots and step-by-step tutorials

**4. Agent Design Patterns** (`docs/agent_design_patterns.md`):

- Consolidate from current scattered pattern docs
- Keep the good examples and storytelling
- 9 core patterns with when to use each
- Reference examples from the repository

---

**For Business Decision Makers:**

**5. Executive Overview** (`guides/executive_overview.md`):

- What this system does and why it matters (business value)
- How it reduces AI project risk and accelerates delivery
- ROI case studies and success metrics
- 5-minute read for busy executives

**6. Understanding AI Proposals Guide** (`guides/reading_proposals.md`):

- How to evaluate AI project proposals
- Key questions to ask about architecture, costs, timeline
- Red flags and risk indicators
- Checklist for approval decisions
- Translation of technical terms to business impact

**7. Requirements Discovery for Leaders** (`guides/stakeholder_discovery.md`):

- How to effectively provide requirements as a non-technical stakeholder
- What information architects need from leadership
- How to articulate business value and constraints
- Examples of good vs. poor requirement statements

**Writing principles:**

**For Technical Content:**

- Write like you're explaining to a friend, not writing academic paper
- Use concrete examples from real projects
- Show, don't just tell (include code snippets, configs)
- Use analogies and metaphors that resonate with engineers
- Include "common mistakes" and "troubleshooting" sections
- Liberal use of visuals, diagrams, emoji for scannability

**For Business/Leadership Content:**

- Lead with business value and ROI, not technical details
- Use executive summaries and clear recommendations
- Translate technical concepts to business impact
- Include risk assessment and mitigation strategies
- Provide comparison options with clear trade-offs
- Use data and metrics to support claims
- Respect time constraints (5-minute reads for executives)

**Example tone shifts:**

**For Engineers (Old → New):**

**Old:** "This framework provides a comprehensive methodology for agent system architecture leveraging multi-shot prompting patterns and knowledge-centric design."

**New:** "Think of this like building with LEGO blocks 🧱. Each agent is a specialized block (Requirements, Architecture, Engineering). The knowledge base is your instruction manual that all blocks reference. User prompts are the specific building steps. Put them together in sequence, and you get a complete AI system."

---

**For Leadership (Technical → Business):**

**Technical Version:** "The architecture agent orchestrates multiple user prompts including tech stack selection, LOE estimation, and cost calculation, writing decisions to a YAML knowledge base for consumption by downstream agents."

**Business Version:** "This system helps you make informed decisions about AI projects by providing clear cost estimates, realistic timelines, and validated technical approaches. It reduces project risk by catching issues early and ensures your team can actually deliver what they propose. Expected ROI: 3-5x faster planning, 40% fewer project failures."

**Success criteria:**

- Documentation rewritten from scratch (not just edited)
- Getting started guide gets user to success in <15 minutes
- Platform-specific examples for Cursor, Claude, Bedrock
- No redundant content across docs
- Good examples and storytelling preserved from old docs
- Beginner-friendly tone and language
- Visual diagrams showing workflows
- User testing: Can a junior engineer follow docs successfully?

---

### Task 7: Update Optimization Agent

**Objective:** Make optimization prompt abstract and flexible for any repository state

**Current issue:**

- `optimization/optimize-ai-architecture-system.user.prompt.md` is outdated
- References old file structure and workflow
- Too specific to current implementation

**Requirements:**

The optimization agent should be able to:

1. **Discover current structure** - Analyze repository without hardcoded paths
2. **Assess against principles** - Evaluate adherence to AI best practices
3. **Identify improvements** - Find redundancy, unclear workflows, documentation gaps
4. **Propose changes** - Suggest specific refactorings with rationale
5. **Execute safely** - Make changes without breaking existing functionality
6. **Validate improvements** - Test that system still works after optimization

**Optimization prompt structure:**

```markdown
# System Optimization Analysis

## Discovery Phase
1. Map current repository structure (find all .prompt.md files)
2. Identify all agents (system prompts)
3. Catalog all user prompts and their purposes
4. Analyze knowledge base (if exists)
5. Review documentation completeness

## Assessment Phase
1. Check adherence to principles:
   - Clear separation of concerns?
   - Consistent naming conventions?
   - Logical file organization?
   - Knowledge base properly used (JSON format)?
   - Tool-based knowledge base access following Anthropic patterns?
   - XML tags used for prompt structure?
   - Documentation up-to-date and serves dual audience (technical + business)?

2. Identify anti-patterns:
   - Capability duplication
   - Unclear workflows
   - Missing documentation
   - Broken references
   - YAML files (should be JSON)
   - Direct file reads (should use tools)
   - Missing XML structure tags
   - Lack of business/leadership perspective

## Improvement Phase
1. Propose specific changes with rationale
2. Estimate impact and effort
3. Prioritize by value and risk
4. Generate refactoring plan

## Execution Phase
1. Make changes incrementally
2. Update documentation alongside code
3. Test after each change
4. Validate entire system works

## Validation Phase
1. Run example workflows end-to-end
2. Check all cross-references
3. Verify documentation accuracy
4. Generate improvement report
```

**Success criteria:**

- Optimization prompt works regardless of exact file names/structure
- Can analyze and improve the system autonomously
- Discovers current state rather than assuming it
- Proposes safe, incremental changes
- Includes validation and testing steps
- Can be run periodically (monthly, quarterly) for ongoing improvement

---

## Success Criteria for Complete Refactoring

### Technical Success

✅ **Simplified structure:**

- 5 agents vs. current 10+ prompts
- Clear directory organization
- No redundant files
- Consistent naming

✅ **Knowledge base implemented:**

- 3 JSON files with clear data model
- All agents use tool-based CRUD operations following Anthropic patterns
- Requirements flow through to decisions
- Tool definitions follow Anthropic's JSON schema format

✅ **Clear separation of concerns:**

- Each agent has unique role
- User prompts in documented sequences
- Multi-shot prompting pattern clear

✅ **Working end-to-end:**

- Can run complete workflow from requirements to implementation
- Knowledge base populated correctly
- All agents function as expected

### User Experience Success

✅ **For Technical Builders (Beginner-friendly):**

- Junior engineer can get started in <15 minutes
- Documentation uses simple language
- Concrete platform examples provided
- Clear workflow with visual diagrams
- Step-by-step guides available
- Common questions answered
- Platform-specific setup (Cursor, Claude, Bedrock)

✅ **For Business Decision Makers (Decision-ready):**

- Executives can evaluate proposals in <15 minutes
- Business value and ROI clearly articulated
- Technical concepts translated to business impact
- Risk assessment included with mitigation strategies
- Clear recommendations (go/no-go with rationale)
- Cost and timeline estimates with confidence levels
- Comparison of alternatives with trade-offs
- Success metrics aligned with business KPIs

### Maintenance Success

✅ **Easy to iterate:**

- Optimization agent can improve system
- Changes don't break existing functionality
- Other AI agents can understand and update

✅ **Sustainable:**

- Less complexity = easier to maintain
- Good documentation = easier to onboard
- Knowledge base = consistency over time

---

## Constraints & Guardrails

### Must Preserve

- ✅ All core functionality (don't lose capabilities)
- ✅ Mermaid diagram generation (recently fixed)
- ✅ LOE estimation framework (non-cost focused)
- ✅ Executive proposal workflows (valuable for users)
- ✅ Good examples and storytelling from documentation
- ✅ Agent design patterns library (9 patterns)

### Must Not

- ❌ Break existing workflows users may be using
- ❌ Increase complexity (goal is simplification)
- ❌ Make it harder for beginners to understand
- ❌ Lose reference to source materials and research
- ❌ Remove documentation without replacing it

### Validation Required

Before considering complete:

1. Run example workflow end-to-end successfully
2. Verify all links and cross-references work
3. Test documentation with representative user (both technical and business audiences)
4. Ensure knowledge base operations work with JSON format
5. Validate tool calls work correctly following Anthropic patterns
6. Test XML tags render and function properly
7. Verify prompts work in Cursor, Claude Projects, and AWS Bedrock
8. Confirm optimization agent can analyze new structure
9. Validate JSON schemas are correct and parseable

---

## Execution Approach

**Iterative refinement:**

1. Complete tasks in order (dependencies matter)
2. Validate after each major change
3. Update documentation as you go (not at end)
4. Test with real example projects
5. Refine based on testing results
6. Iterate up to 3 times per task if needed

**Reference materials:**

- Follow patterns from: <https://github.com/Modular-Earth-LLC/job-finding-assistant>
- Apply AI best practices from Anthropic, AWS Bedrock research
- Use prompt engineering principles from your own training
- Learn from what works in current repository

**Quality standards:**

- Favor simplicity over features
- Optimize for beginner understanding
- Choose clarity over cleverness
- Document as you build
- Test everything

---

## Final Note

This refactoring should result in a system that is:

- **Simple** to understand and use
- **Intuitive** in its workflow and organization
- **Powerful** in capabilities (don't lose functionality)
- **Maintainable** by humans and AI agents
- **Beginner-friendly** for technical builders
- **Executive-ready** for business decision makers
- **Production-ready** for deployment on target platforms

**Critical Dual-Audience Requirement:**

The system must serve TWO distinct audiences simultaneously:

1. **Technical Builders** who need depth, examples, and step-by-step guidance to create architectures and build systems
2. **Business Leaders** who need clarity, business value translation, and decision-ready recommendations to approve and fund projects

**Success means:**

- An AI engineer can use this system to produce complete, professional proposals
- A CEO/CFO can read those proposals and make confident go/no-go decisions
- Both audiences feel the system speaks to their needs and concerns
- Technical rigor does NOT come at the expense of business clarity
- Business focus does NOT sacrifice technical depth

**This applies to both:**

- **Internal projects** - Engineering teams proposing to their own leadership
- **External/client projects** - Consultants and agencies proposing to client leadership

The goal is not to add more features, but to **clarify and simplify** what already exists while establishing **proper foundations** (knowledge base, clear roles, dual-audience docs) for future growth.

---

## Critical Technical Requirements Summary

**Data Format:**

- ✅ Use **JSON** for all knowledge base and configuration files (NOT YAML)
- ✅ JSON provides better parsing, validation, and tool integration
- ✅ Compatible with Anthropic's function calling patterns

**Anthropic Integration:**

- ✅ Follow **Anthropic's prompt engineering best practices** from official documentation
- ✅ Use **XML tags** for structure: `<role>`, `<instructions>`, `<example>`, `<thinking>`, `<analysis>`
- ✅ Implement **tool use patterns** following Anthropic's JSON schema specifications
- ✅ Define all knowledge base operations as **tools** with proper schemas
- ✅ Include **chain-of-thought** reasoning with XML tags
- ✅ Validate compatibility with: **Claude API**, **Cursor (Claude backend)**, **AWS Bedrock**

**Dual Audience:**

- ✅ **Technical builders** get depth, examples, step-by-step guidance
- ✅ **Business leaders** (CEO, CFO, CTO) get ROI, risk assessment, clear recommendations
- ✅ Every output serves both: technical rigor + business clarity
- ✅ Applicable to both **internal projects** and **external client work**

**References:**

- Anthropic Prompt Engineering: <https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering>
- Anthropic Tool Use: <https://docs.anthropic.com/en/docs/build-with-claude/tool-use>  
- XML Tags Guide: <https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/use-xml-tags>
- Job Finding Assistant Pattern: <https://github.com/Modular-Earth-LLC/job-finding-assistant>

---

Take your time. Do excellent work. This refactoring will make the system significantly more valuable to ALL users - builders AND decision makers - while following industry best practices from Anthropic for maximum compatibility and effectiveness.
