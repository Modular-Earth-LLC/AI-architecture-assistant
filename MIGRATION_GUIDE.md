# Migration Guide - Old to New Structure

**For:** Users of pre-refactor AI Architecture Assistant  
**Date:** 2025-10-03  
**Impact:** Major structural refactoring

---

## What Changed

### Old Structure → New Structure

**Old:**
```
/requirements/          # 6 files (discovery, extraction, wizard, guides)
/architecture/          # 12 files (3 system prompts, 5 user prompts, guides)
/proposals/             # 3 files (proposal prompts)
/development/           # 2 files (prototype builder, guide)
/delivery/              # 2 files (demo, handoff)
/optimization/          # 1 file
```

**New:**
```
/supervisor_agent.system.prompt.md    # NEW: Root orchestrator
/ai_agents/                           # NEW: 5 specialized agents
/user_prompts/                        # NEW: 15 task-specific prompts
/knowledge_base/                      # NEW: JSON shared state
/guides/                              # Reorganized documentation
/outputs/                             # NEW: Presentations + prototypes
/templates/                           # Reorganized templates
/docs/                                # Reference documentation
/archive/pre-refactor-2025-10/        # OLD files archived here
```

---

## File Mapping

### System Prompts (Agents)

| Old File | New File | Notes |
|----------|----------|-------|
| `requirements/discovery-agent.prompt.md` | `ai_agents/requirements_agent.system.prompt.md` | Consolidated |
| `architecture/AI-architecture_assistant.system.prompt.md` | `ai_agents/architecture_agent.system.prompt.md` | Consolidated (3→1) |
| `architecture/solutions-architect-system.prompt.md` | `ai_agents/architecture_agent.system.prompt.md` | Merged |
| `architecture/technical-architect-agent.prompt.md` | `ai_agents/architecture_agent.system.prompt.md` | Merged |
| `development/prototype-builder-agent.prompt.md` | `ai_agents/engineering_agent.system.prompt.md` | Renamed |
| N/A | `ai_agents/deployment_agent.system.prompt.md` | NEW |
| N/A | `ai_agents/optimization_agent.system.prompt.md` | NEW (refactored from user prompt) |
| N/A | `supervisor_agent.system.prompt.md` | NEW (root orchestrator) |

---

### User Prompts

| Old File | New File | Notes |
|----------|----------|-------|
| `requirements/quick-start-wizard.prompt.md` | `user_prompts/requirements/quick_discovery.user.prompt.md` | Extracted 15-min flow |
| N/A | `user_prompts/requirements/standard_discovery.user.prompt.md` | NEW |
| N/A | `user_prompts/requirements/comprehensive_workshop.user.prompt.md` | NEW |
| `requirements/requirements-extraction.prompt.md` | `user_prompts/requirements/extract_requirements.user.prompt.md` | Moved |
| `architecture/tech_stack_generation.user.prompt.md` | `user_prompts/architecture/tech_stack_selection.user.prompt.md` | Renamed |
| `architecture/loe_estimation_detailed.user.prompt.md` | `user_prompts/architecture/loe_estimation.user.prompt.md` | Moved |
| `architecture/project_cost_estimation.user.prompt.md` | `user_prompts/architecture/cost_estimation.user.prompt.md` | Moved |
| `architecture/team_composition_generation.user.prompt.md` | `user_prompts/architecture/team_composition.user.prompt.md` | Moved |
| `architecture/technical_project_plan_generation.user.prompt.md` | `user_prompts/architecture/project_plan_generation.user.prompt.md` | Moved |
| N/A | `user_prompts/architecture/architecture_diagram_generation.user.prompt.md` | NEW |
| `proposals/discovery-assessment-proposal.prompt.md` | `user_prompts/proposals/discovery_proposal_assembly.user.prompt.md` | Refactored |
| `proposals/poc-mvp-implementation-proposal.prompt.md` | `user_prompts/proposals/implementation_proposal_assembly.user.prompt.md` | Refactored |
| N/A | `user_prompts/proposals/pitch_deck_assembly.user.prompt.md` | NEW |
| N/A | `user_prompts/proposals/internal_proposal_assembly.user.prompt.md` | NEW |
| `optimization/optimize-ai-architecture-system.user.prompt.md` | `user_prompts/optimization/system_optimization.user.prompt.md` | Refactored |

---

### Guides & Templates

| Old File | New File | Notes |
|----------|----------|-------|
| `requirements/discovery-guide.md` | Archived | Replaced by user prompts |
| `requirements/workshop-guide.md` | Archived | Replaced by user prompts |
| `architecture/design-guide.md` | Archived | Incorporated into agents |
| `architecture/agent-design-patterns.md` | `docs/agent_design_patterns.md` | Moved to docs |
| `architecture/architecture-template.md` | `templates/architecture-template.md` | Moved to templates |
| `requirements/requirements-template.md` | `templates/requirements-template.md` | Moved to templates |
| `development/development-checklist.md` | `templates/development-checklist.md` | Moved to templates |
| `delivery/handoff-checklist.md` | `templates/handoff-checklist.md` | Moved to templates |
| `development/prototype-guide.md` | `guides/prototype-guide.md` | Moved to guides |
| `delivery/demo-guide.md` | `guides/demo-guide.md` | Moved to guides |
| `examples/email-automation.md` | `guides/examples/email-automation.md` | Moved to guides |

---

## Major Changes

### 1. Knowledge Base Pattern (NEW)

**Old:** No shared data structure  
**New:** JSON files in `knowledge_base/`

- `system_config.json` - Platform settings, constraints
- `user_requirements.json` - Requirements Agent output
- `design_decisions.json` - Architecture Agent output

**Action:** Populate these for each new project

---

### 2. Multi-Agent Orchestration (NEW)

**Old:** Use agents directly  
**New:** Supervisor orchestrates specialized agents

**Workflow:**
```
Supervisor Agent → Routes to appropriate specialized agent
                → Maintains context
                → Guides through complete workflow
```

**Action:** Start with Supervisor Agent, let it route you

---

### 3. Proposals Refactored (MAJOR CHANGE)

**Old:** Proposals contained architecture/cost logic  
**New:** Proposals READ from knowledge base (assembly-only)

**Old workflow:**
```
Run proposal prompt → Does architecture + costs → Generates proposal
```

**New workflow:**
```
Complete architecture (6 steps) → Design_decisions.json populated
Run proposal assembly → READS from knowledge base → Assembles proposal
```

**Action:** Complete architecture BEFORE proposals

---

### 4. Presentation Infrastructure (NEW)

**Old:** No presentation support  
**New:** `outputs/presentations/` for stakeholder deliverables

**Structure:**
```
outputs/presentations/[project]/
├── requirements/           # Requirements summaries
├── architecture/           # Design step outputs
├── diagrams/              # Architecture diagrams
└── proposals/             # Assembled proposals/pitch decks
```

**Action:** Use proposal assembly prompts to generate presentations

---

## Migration Steps

### If You Have In-Progress Projects

**Option A: Continue with Old Structure**
- Old files are archived in `archive/pre-refactor-2025-10/`
- You can continue using them to complete current projects
- Migrate to new structure for next project

**Option B: Migrate to New Structure**

1. **Extract your project data:**
   - Copy your notes/requirements to text file
   - Copy any architecture decisions made

2. **Use new system:**
   - Run Requirements Agent with `extract_requirements.user.prompt.md`
   - Paste your old notes
   - Agent structures into new user_requirements.json format

3. **Continue with new workflow:**
   - Run Architecture Agent (6-step process)
   - Assemble proposals
   - Proceed to engineering

---

### If Starting Fresh

**Simply use the new structure:**

1. **Read:** README.md (15-min overview)
2. **Deploy:** Choose platform (see this guide)
3. **Start:** Supervisor Agent or Requirements Agent
4. **Follow:** Workflow guide for complete lifecycle

**No migration needed** - you're starting with the new system.

---

## Breaking Changes

### 1. File References

**Old references like:**
```markdown
See: architecture/technical-architect-agent.prompt.md
See: requirements/discovery-guide.md
```

**Update to:**
```markdown
See: ai_agents/architecture_agent.system.prompt.md
See: user_prompts/requirements/quick_discovery.user.prompt.md
```

---

### 2. Workflow Sequence

**Old:** Could run proposals directly (they did architecture internally)  
**New:** Must complete architecture BEFORE proposals

**Old workflow:**
```
Discovery → Proposal (includes architecture) → Build
```

**New workflow:**
```
Discovery → Architecture (6 steps) → Proposal (assembly) → Build
```

**Why:** Separation of concerns, reusability, no duplication

---

### 3. Knowledge Base Required

**Old:** Optional note-taking  
**New:** Knowledge base is central to workflow

**Action:**
- Ensure `knowledge_base/` files exist
- Agents read/write to these automatically
- Track in git for version history

---

## Benefits of New Structure

**You get:**
1. ✅ **Clearer workflow** - Supervisor guides you
2. ✅ **No redundancy** - 0% duplication vs. 40% before
3. ✅ **Better organization** - Logical directory structure
4. ✅ **Knowledge persistence** - JSON shared state
5. ✅ **Dual-audience outputs** - Technical + business
6. ✅ **Presentation-ready** - Pitch decks and proposals assemble automatically
7. ✅ **Platform flexibility** - Deploy to Cursor, Claude, Bedrock
8. ✅ **Best practices** - AWS Well-Architected, Anthropic patterns integrated

---

## Support

**Questions about migration?**
- Check README.md for system overview
- See guides/workflow_guide.md for complete lifecycle
- Review guides/executive_overview.md if presenting to leadership

**Old files needed?**
- All archived in `archive/pre-refactor-2025-10/`
- Can reference if needed
- Will be removed in future cleanup

---

**Version:** 1.0  
**Migration Date:** 2025-10-03  
**Impact:** Major structural improvement  
**Effort:** 5-15 minutes to understand new structure
