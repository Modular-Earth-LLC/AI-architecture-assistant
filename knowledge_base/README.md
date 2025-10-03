# Knowledge Base - Shared Data Store

**Purpose:** Centralized JSON-based data storage for requirements, decisions, and configuration across all AI agents in the Architecture Assistant system.

**Format:** JSON (not YAML) for better parsing, validation, and tool integration following Anthropic recommendations.

---

## Overview

The knowledge base enables agents to share information consistently without losing context. Think of it as the "memory" of the AI Architecture Assistant system.

```
Requirements Agent → WRITES user_requirements.json
                         ↓
Architecture Agent → READS user_requirements.json
                   → WRITES design_decisions.json
                         ↓
Engineering Agent → READS both files
                  → BUILDS prototype based on them
                         ↓
Deployment Agent → READS design_decisions.json
                 → DEPLOYS system

All Agents → READ system_config.json (platform settings, constraints)
```

---

## Files in This Directory

### 1. `system_config.json` (READ-ONLY for Agents)

**Purpose:** Platform settings, constraints, stakeholders, team information

**Updated by:** AI engineers manually or through human-in-the-loop

**Used by:** All agents (read configuration to inform decisions)

**Key Sections:**
- `project`: Name, type, organization, description
- `platform`: Target deployment (Cursor, AWS Bedrock, etc.), region
- `stakeholders`: Decision makers, contributors, end users
- `constraints`: Budget, timeline, compliance, technical, priority
- `team`: Size, skills, gaps, hiring/training budget
- `preferences`: Development methodology, quality standards, testing requirements
- `risk_tolerance`: Innovation vs. stability, cost vs. speed, build vs. buy

**When to update:**
- At project start (initial configuration)
- When constraints change (budget increase, new deadline)
- When team changes (new hires, skill development)
- When stakeholders change (new decision makers)

---

### 2. `user_requirements.json` (Written by Requirements Agent)

**Purpose:** All requirements gathered during discovery phase

**Written by:** Requirements Agent (primary), Architecture Agent (technical details)

**Read by:** Architecture Agent, Engineering Agent, all downstream agents

**Key Sections:**
- `customer`: Organization context, AI adoption stage, history
- `use_case`: Title, summary, problem statement, target users, workflows
- `business`: Problem, current state, desired outcome, business value, success metrics
- `technical`: Functional/non-functional requirements, AI services, data, integrations
- `project_scope`: In/out of scope, assumptions, constraints, phased approach
- `financial`: Expected ROI, TCO, budget constraints
- `risks`: Business and technical risks with mitigation
- `_metadata`: Discovery method, completeness score, validation status

**Lifecycle:**
1. Requirements Agent populates during discovery session
2. Architecture Agent may add technical details during design
3. Updated if requirements evolve during implementation
4. Version controlled in git (track requirement changes)

**Completeness Check:**
- `incomplete`: Missing critical information
- `partial`: Some gaps remain
- `complete`: Ready for architecture design

---

### 3. `design_decisions.json` (Written by Architecture Agent)

**Purpose:** All architecture decisions, estimates, costs, plans

**Written by:** Architecture Agent (primary), Engineering Agent (implementation learnings)

**Read by:** Engineering Agent, Deployment Agent, Proposal assembly prompts

**Key Sections:**
- `executive_summary`: For business leaders (recommendation, investment, timeline, risks)
- `tech_stack`: LLM providers, frameworks, backend/frontend, databases, infrastructure
- `architecture_design`: Diagram, components, data flows, security boundaries
- `team_composition`: Required roles, skills, hiring needs, team allocation
- `estimates`: Engineering hours, timeline, complexity, confidence, buffers
- `costs`: Development, infrastructure, third-party, TCO, ROI projections
- `model_evaluation`: AI models evaluated, benchmark results, selection rationale
- `project_plan`: Phased roadmap, milestones, dependencies, success criteria
- `risks_and_mitigation`: Technical and business risks with strategies
- `compliance_and_security`: Security design, compliance alignment, responsible AI
- `_metadata`: Design process completion status, validation, approvals

**Lifecycle:**
1. Architecture Agent populates through 6-step design process
2. Engineering Agent may add implementation notes
3. Optimization Agent may update based on improvements
4. Version controlled in git (track architecture evolution)

**Design Process Tracking:**
```json
"_metadata": {
  "steps_completed": {
    "step_1_tech_stack": false,
    "step_2_architecture_diagram": false,
    "step_3_team_composition": false,
    "step_4_loe_estimation": false,
    "step_5_cost_estimation": false,
    "step_6_project_plan": false
  }
}
```

---

## How Agents Interact with Knowledge Base

### Agent Access Patterns

**Requirements Agent:**
```
READ:  system_config.json (constraints, stakeholders)
WRITE: user_requirements.json (discovery outputs)
```

**Architecture Agent:**
```
READ:  system_config.json (platform, constraints)
READ:  user_requirements.json (what to design)
WRITE: design_decisions.json (architecture, estimates, costs, plans)
UPDATE: user_requirements.json (if gathering additional technical details)
```

**Engineering Agent:**
```
READ: user_requirements.json (why building this)
READ: design_decisions.json (what to build, tech stack, architecture)
UPDATE: design_decisions.json (implementation learnings)
```

**Deployment Agent:**
```
READ: design_decisions.json (what to deploy, how)
```

**Optimization Agent:**
```
READ: All files (comprehensive analysis)
UPDATE: Any file (based on optimization findings)
```

### Tool-Based Access (Conceptual)

Following Anthropic patterns, agents conceptually use "tools" to access knowledge base:

**Example Tool Definitions:**
```json
{
  "name": "read_config",
  "description": "Read system configuration",
  "input_schema": {"type": "object", "properties": {}},
  "returns": "JSON from system_config.json"
},
{
  "name": "read_requirements",
  "description": "Read current user requirements",
  "input_schema": {"type": "object", "properties": {}},
  "returns": "JSON from user_requirements.json"
},
{
  "name": "write_requirements",
  "description": "Write or update user requirements",
  "input_schema": {
    "type": "object",
    "properties": {
      "requirements": {"type": "object", "description": "Requirements data"}
    },
    "required": ["requirements"]
  }
},
{
  "name": "read_design_decisions",
  "description": "Read architecture design decisions",
  "input_schema": {"type": "object", "properties": {}},
  "returns": "JSON from design_decisions.json"
},
{
  "name": "write_design_decisions",
  "description": "Write or update design decisions",
  "input_schema": {
    "type": "object",
    "properties": {
      "decisions": {"type": "object", "description": "Design decisions data"}
    },
    "required": ["decisions"]
  }
}
```

**Platform Adaptation:**
- **Cursor:** File system reads/writes
- **AWS Bedrock:** Knowledge Base API calls
- **Claude API:** File attachments or embeddings
- **Custom:** Your platform's storage mechanism

---

## For AI Engineers: How to Use the Knowledge Base

### Starting a New Project

**Step 1: Configure System**

Edit `system_config.json`:
```json
{
  "project": {
    "name": "My AI System",
    "type": "genai_assistant",
    "organization": "My Company"
  },
  "platform": {
    "target": "cursor",
    "deployment": "cloud",
    "region": "us-east-1"
  },
  "constraints": {
    "budget": {"range": "$50,000 - $75,000"},
    "timeline": {"deadline": "2025-12-31"}
  }
  // ... fill in other sections
}
```

**Step 2: Run Requirements Agent**

Requirements Agent will populate `user_requirements.json` during discovery.

**Step 3: Run Architecture Agent**

Architecture Agent will populate `design_decisions.json` through 6-step design process.

**Step 4: Review JSON Files**

Before Engineering Agent builds prototype, review both files for completeness:
```bash
# Check requirements completeness
cat user_requirements.json | grep "completeness_score"

# Check design process completion
cat design_decisions.json | grep "design_process_completed"
```

---

### Mid-Project Updates

**Updating Requirements:**
```json
// user_requirements.json
{
  "business": {
    "desired_outcome": {
      "success_definition": "NEW SUCCESS CRITERIA HERE"
    }
  },
  "_metadata": {
    "last_updated": "2025-10-05",
    "validation_status": "updated - requires architecture review"
  }
}
```

**Updating Design Decisions:**
```json
// design_decisions.json
{
  "tech_stack": {
    "primary_stack": {
      "llm_platform": {
        "provider": "anthropic",  // Changed from "openai"
        "models": ["claude-3-sonnet-20240229"]
      }
    },
    "last_updated": "2025-10-05"
  },
  "_change_history": [
    {
      "date": "2025-10-05",
      "section_updated": "tech_stack.llm_platform",
      "reason": "Privacy policy requires non-OpenAI provider",
      "updated_by": "architect",
      "approval_status": "approved"
    }
  ]
}
```

**After updates:**
- Re-run affected design steps (see Architecture Agent's cascade analysis)
- Update `_change_history` to track modifications
- Commit to git for version history

---

### Troubleshooting

**Problem: Agent can't find knowledge base files**

Solution:
- Ensure you're running agent from repository root
- Check file paths: `knowledge_base/user_requirements.json` (relative path)
- Verify JSON files exist and are valid

**Problem: JSON parsing errors**

Solution:
- Validate JSON syntax: https://jsonlint.com/
- Check for trailing commas (not allowed in JSON)
- Ensure all strings use double quotes, not single
- Use JSON schema validator

**Problem: Missing required fields**

Solution:
- Check `_comment` fields for field descriptions
- See `_example` section for complete working example
- Run through appropriate agent to populate (don't manually fill if unsure)

**Problem: Conflicts between user_requirements and design_decisions**

Solution:
- user_requirements is source of truth for WHAT and WHY
- design_decisions is source of truth for HOW and HOW MUCH
- If conflicts: Architecture Agent should reconcile
- Use `_change_history` to track resolution

---

## Schema Validation

### Validating JSON Files

**Online validators:**
- JSONLint: https://jsonlint.com/
- JSON Schema Validator: https://www.jsonschemavalidator.net/

**Command-line (Python):**
```bash
python -m json.tool knowledge_base/user_requirements.json
# If valid: prints formatted JSON
# If invalid: shows error
```

**Command-line (Node.js):**
```bash
node -e "JSON.parse(require('fs').readFileSync('knowledge_base/user_requirements.json'))"
# If valid: no output
# If invalid: throws error
```

### Required Fields

**system_config.json minimum:**
- `project.name`
- `platform.target`
- `constraints.budget.range`
- `team.current_size`

**user_requirements.json minimum:**
- `use_case.title`
- `business.problem`
- `business.business_value`
- `technical.functional_requirements` (at least 1)
- `_metadata.completeness_score`

**design_decisions.json minimum:**
- `executive_summary` (all fields)
- `tech_stack.primary_stack` (all subsections)
- `estimates.total_engineering_hours`
- `costs.total_cost_of_ownership`

---

## Version Control Best Practices

**Commit frequently:**
```bash
# After Requirements Agent completes
git add knowledge_base/user_requirements.json
git commit -m "Add requirements for [project-name]"

# After each Architecture Agent design step
git add knowledge_base/design_decisions.json
git commit -m "Complete tech stack selection for [project-name]"

# Before major changes
git commit -m "Checkpoint before updating tech stack"
```

**Use branches for experimentation:**
```bash
# Try alternative architecture
git checkout -b experiment-alternative-stack
# Make changes, test
# If successful: merge
# If unsuccessful: delete branch
```

**Tag releases:**
```bash
# When architecture design complete
git tag -a "v1.0-architecture-complete" -m "Architecture design finalized"

# When prototype complete
git tag -a "v1.0-prototype" -m "Financial operations assistant prototype"
```

---

## Example: Complete Financial Operations Assistant

**See:** `_example` sections in each JSON file for a complete worked example

**Project:** Financial Operations Assistant for Solo-Entrepreneurs

**Files:**
- `system_config.json._example` - Solo-entrepreneur configuration
- `user_requirements.json._example` (embedded) - Complete requirements
- `design_decisions.json._example` (would be added after architecture phase)

**Usage:**
1. Copy `_example` sections to top level
2. Customize for your specific project
3. Remove `_example` sections when done

---

## For Platform Deployment

### Cursor Deployment
- Knowledge base stays as JSON files
- Agents read via file system
- Version controlled in git
- **Access pattern:** Direct file I/O

### Claude Projects Deployment
- Upload JSON files to Project Knowledge
- Agents query via project knowledge search
- **Access pattern:** Claude Projects knowledge API

### AWS Bedrock Deployment
- Create Bedrock Knowledge Base
- Ingest JSON files
- Agents query via Bedrock Knowledge Base API
- **Access pattern:** Vector search or structured queries

### Self-Hosted Deployment
- Store JSON locally or in private database
- Agents access via file system or API
- **Access pattern:** Your implementation choice

---

## Questions?

**Where do I start?**
→ Run Requirements Agent first - it will populate user_requirements.json

**What if I make a mistake?**
→ Use git to revert: `git checkout knowledge_base/[file]`

**Can I edit JSON files manually?**
→ Yes, but use agents when possible (they ensure schema compliance)

**What if I want different fields?**
→ Extend the schema - add custom fields with `custom_` prefix

**How do I validate my JSON?**
→ Use online JSON validator or command-line tools (see Schema Validation section)

---

## Summary

**Knowledge base = Shared memory across agents**

- `system_config.json` - Your project configuration (you manage)
- `user_requirements.json` - What to build (Requirements Agent writes)
- `design_decisions.json` - How to build it (Architecture Agent writes)

**Benefits:**
- ✅ Consistency across workflow phases
- ✅ No information loss between agents
- ✅ Traceability (requirements → design → implementation)
- ✅ Version history (git tracks all changes)

**Best practices:**
- Keep JSON valid (run validators)
- Commit frequently (track evolution)
- Use agents to update (ensures schema compliance)
- Review changes before committing

---

**Version:** 1.0  
**Last Updated:** 2025-10-03  
**Format:** JSON following Anthropic tool use patterns
