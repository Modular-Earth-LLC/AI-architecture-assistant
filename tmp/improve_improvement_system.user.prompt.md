# Task: Refactor AI Architecture Assistant Self-Improvement System

**Purpose:** Transform the optimization agent into a generic, reusable optimizer and create specialized self-improvement workflows for each agent in the AI Architecture Assistant system.

**Complexity:** Advanced multi-phase refactoring task
**Risk Level:** Medium (affects core system optimization capabilities)

---

## Context & Motivation

The current `optimization_agent.system.prompt.md` is tightly coupled to this repository's structure, explicitly referencing specific files and workflows. This limits its reusability for optimizing user-designed AI systems.

**Goals:**

1. **Generalize the Optimization Agent** - Make it work for ANY AI system
2. **Create Specialized Self-Improvement Workflow** - Purpose-built prompt for improving this framework
3. **Build Agent-Specific Improvement Prompts** - Targeted refinement tools for each agent
4. **Enable Automated Improvement Pipeline** - Allow optimization agent to orchestrate improvements

---

## Task Breakdown

### Phase 1: Generalize the Optimization Agent

**Objective:** Refactor `optimization_agent.system.prompt.md` (`{{OPTIMIZATION_AGENT_PATH}}`) to be system-agnostic.

**Inspiration:** [The [Prompt Engineering Assistant's self-improvement prompt](https://github.com/Modular-Earth-LLC/AI-engineering-assistant/blob/main/user_prompts/improve_prompt_engineering_assistant.user.prompt.md)](https://github.com/Modular-Earth-LLC/AI-engineering-assistant/blob/main/user_prompts/improve_system_of_prompts.user.prompt.md) demonstrates this pattern effectively. Note: do not reference defaults prompts. Ask the user which prompts to optimize or whether to optimize all prompts found in a location like a folder or git repository.

**Actions:**

1. Remove explicit references to this repository's files and directory structure
2. Convert repository-specific examples to generic patterns
3. Ensure discovery-driven approach works for ANY AI system (including this one)
4. Maintain all existing capabilities (user system optimization + meta-system optimization)
5. Ensure Mode 2 (meta-optimization) triggers from user prompts, not hardcoded awareness

**Validation Criteria:**

- [ ] No hardcoded references to `ai_agents/`, `user_prompts/`, etc.
- [ ] Examples demonstrate both user systems and generic "AI framework" optimization
- [ ] Discovery process remains comprehensive and systematic
- [ ] All safety guardrails preserved

---

### Phase 2: Create System-Wide Self-Improvement User Prompt

**Objective:** Build a comprehensive user prompt at `user_prompts/optimization/improve_ai_architecture_assistant.user.prompt.md` (`{{SYSTEM_IMPROVEMENT_PROMPT_PATH}}`) for optimizing the entire AI Architecture Assistant framework.

**Requirements:**

**Target Location:** `user_prompts/optimization/improve_ai_architecture_assistant.user.prompt.md`

**Inspiration:** The [Prompt Engineering Assistant's self-improvement prompt](https://github.com/Modular-Earth-LLC/AI-engineering-assistant/blob/main/user_prompts/improve_prompt_engineering_assistant.user.prompt.md) demonstrates this pattern effectively.

**Prompt Structure:**

1. **Role & Mission**: Instruct optimization agent on meta-system improvement
2. **Discovery Targets**:
   - All agents in `ai_agents/`
   - All user prompts in `user_prompts/`
   - Knowledge base in `knowledge_base/`
   - Documentation in `guides/`, `docs/`, `templates/`
3. **Improvement Focus Areas**:
   - Prompt engineering best practices (Anthropic, OpenAI patterns)
   - Multi-agent coordination patterns
   - Knowledge base utilization
   - User experience and workflow clarity
   - Documentation completeness
4. **Orchestration Logic**:
   - Discover system state
   - Identify which agents/prompts need improvement
   - Call specialized agent improvement prompts (from Phase 3)
   - Validate improvements holistically
   - Test end-to-end workflows
5. **Success Criteria**: Measurable improvements in clarity, maintainability, effectiveness

**Validation Criteria:**

- [ ] Prompt is executable by the generalized optimization agent
- [ ] Covers all system components comprehensively
- [ ] References agent-specific improvement prompts (Phase 3)
- [ ] Includes validation and testing steps
- [ ] Maintains backward compatibility awareness

---

### Phase 3: Create Agent-Specific Improvement Prompts

**Objective:** Build targeted self-improvement prompts for each agent, analogous to the prompt engineering assistant's approach.

**Target Agents & Locations:**

| Agent | System Prompt | Improvement Prompt Location | Focus Area |
|-------|--------------|---------------------------|------------|
| Requirements Agent | `ai_agents/requirements_agent.system.prompt.md` | `user_prompts/requirements/improve_requirements_agent.user.prompt.md` | Requirement elicitation, workshop facilitation |
| Architecture Agent | `ai_agents/architecture_agent.system.prompt.md` | `user_prompts/architecture/improve_architecture_agent.user.prompt.md` | System design, tech stack selection, diagramming |
| Engineering Agent | `ai_agents/engineering_agent.system.prompt.md` | `user_prompts/engineering/improve_engineering_agent.user.prompt.md` | Code generation, prototype building, API design |
| Deployment Agent | `ai_agents/deployment_agent.system.prompt.md` | `user_prompts/deployment/improve_deployment_agent.user.prompt.md` | Cloud deployment, infrastructure, CI/CD |
| Optimization Agent | `ai_agents/optimization_agent.system.prompt.md` | `user_prompts/optimization/improve_optimization_agent.user.prompt.md` | Discovery-driven optimization, refactoring |
| Supervisor Agent | `supervisor_agent.system.prompt.md` | `user_prompts/improve_supervisor_agent.user.prompt.md` | Workflow orchestration, agent coordination |

**Prompt Structure for Each Agent:**

1. **Agent Context**: Role, capabilities, typical workflows
2. **Improvement Focus**: Domain-specific best practices (e.g., Anthropic prompt patterns, AWS best practices)
3. **Test Scenarios**: Representative tasks to validate improvements
4. **Success Metrics**: How to measure improvement effectiveness
5. **Safety Guardrails**: Preserve existing capabilities, validate workflows

**Design Principles:**

- **Platform-Agnostic**: Work with Cursor/Claude, GitHub Copilot/GPT, or other platforms
- **Version-Resilient**: Don't hardcode model versions (Claude Sonnet 4.5, GPT-5)
- **Modular**: Each prompt is independent and focused
- **Testable**: Include validation criteria

**Validation Criteria:**

- [ ] Six improvement prompts created (one per agent)
- [ ] Each prompt can be executed by the prompt engineering assistant
- [ ] Prompts are specific to agent's domain expertise
- [ ] Test scenarios cover common use cases
- [ ] Platform and version agnostic

---

### Phase 4: Enhance Optimization Agent Orchestration

**Objective:** Update `user_prompts/optimization/improve_ai_architecture_assistant.user.prompt.md` to orchestrate agent-specific improvements during meta-system optimization.

**Enhancements:**

1. **Improvement Prompt Awareness**:
   - Add section explaining specialized improvement prompts exist
   - Document when to apply system-wide vs. agent-specific improvements

2. **Orchestration Workflow**:

   ```text
   Meta-System Optimization Process:
   1. Execute system-wide discovery (as implemented by the @optimization_agent.system.prompt.md hosted in Cursor custom agent chat mode that is intended to recieve the @improve_ai_architecture_assistant.user.prompt.md)
   2. Identify all agents that could be improved
   3. For each agent:
      a. Review and improve agent improvement prompts themselves first (meta-improvement)
      b. Execute agent-specific improvement prompts targeted that their respective agent
      c. Validate improvements don't break workflows.
   4. Systematically validate and improve the entire AI system, framework, and workflows.
   5. Test end-to-end system workflows
   6. Generate optimization report
   ```

3. **Self-Improvement Recursion Safety**:
   - Detect recursion, gain self awareness of meta-optimization
   - Apply improvements to agents and prompts before executing the prompts to improve themselves
   - Prevent infinite loops

4. **Validation Integration**:
   - Cross-reference all agents after improvements
   - Test knowledge base integration
   - Validate user workflows still function, fix and improve them as necessary.

**Validation Criteria:**

- [ ] Optimization agent can orchestrate calling of agent-specific improvement prompts
- [ ] Recursion guardrails prevent infinite loops
- [ ] System-wide improvement and validation workflow is defined
- [ ] Clear guidance on when to use each improvement prompt, including the system-wide optimization prompt and each agent-specific improvement prompt.

---

## Variables

**{{OPTIMIZATION_AGENT_PATH}}**: `ai_agents/optimization_agent.system.prompt.md`  
**{{SYSTEM_IMPROVEMENT_PROMPT_PATH}}**: `user_prompts/optimization/improve_ai_architecture_assistant.user.prompt.md`  
**{{AI_AGENTS_DIR}}**: `ai_agents/`  
**{{USER_PROMPTS_DIR}}**: `user_prompts/`  
**{{REPO_ROOT}}**: `C:\Users\paulp\OneDrive\Documents\GitHub\AI-architecture-assistant`

---

## Success Criteria

**Overall Success Indicators:**

✅ **Separation of Concerns**

- Optimization agent is generic and reusable
- Self-improvement logic lives in user prompts, not system prompts

✅ **Comprehensive Coverage**

- All 6 agents have specialized improvement prompts
- System-wide improvement prompt coordinates all improvements

✅ **Functional Validation**

- All existing optimization workflows still work
- New improvement workflows successfully execute
- End-to-end system workflows validated

✅ **Quality Standards**

- Prompts follow best practices (structured, clear, testable)
- Platform-agnostic design
- Safety guardrails prevent breaking changes

✅ **Documentation**

- Clear usage instructions for each improvement prompt
- Examples demonstrate effectiveness
- Orchestration logic well-documented

---

## Safety & Validation Requirements

**Before Making Changes:**

- [ ] Read and understand ALL current agent prompts
- [ ] Map existing cross-references and dependencies
- [ ] Identify critical workflows that must continue working

**During Implementation:**

- [ ] Make incremental changes (complete one phase before next)
- [ ] Test after each major change
- [ ] Preserve all existing capabilities
- [ ] Use version control (git) for easy rollback

**After Implementation:**

- [ ] Test key user workflows:
  - [ ] Requirements → Architecture → Engineering → Deployment
  - [ ] Individual agent improvements
  - [ ] System-wide optimization
- [ ] Validate no broken references
- [ ] Confirm all examples still work
- [ ] Generate summary of changes

**Risk Mitigation:**

- Archive current versions before refactoring
- Test with simple examples before complex scenarios
- Get user approval before executing (don't assume)

---

## Execution Approach

**Recommended Sequence:**

1. **Phase 1 First** (Generalize optimization agent) - Foundation for everything else
2. **Phase 2** (Create agent-specific prompts) - Independent, parallelizable work
3. **Phase 3** (Create system-wide prompt) - Needs Phase 2 outputs to reference
4. **Phase 4 Last** (Enhance orchestration) - Integrates everything together

**Tool Requirements:**

- File editing capabilities
- Testing/validation capabilities

---

## Clarification Checkpoint

**Before proceeding, please confirm:**

1. **Scope Understanding**: Does the task description make sense? Any ambiguity in requirements?
2. **Safety Concerns**: Are there breaking changes or risks I haven't addressed?
3. **Execution Preferences**: Should I proceed with all phases, or would you like to review after each phase?
4. **Platform Constraints**: Any character limits or platform-specific constraints for the improvement prompts?
5. **Priority**: Are all phases equally important, or should I prioritize certain aspects?

**If anything is unclear or could generate unsafe behavior, please clarify before I proceed with implementation.**

Remember, the final system you are creating will be used as follows:

1. The user loads up the optimization_agent.system.prompt.md as a custom agent chat mode in Cursor, backed by Claude Sonnet 4.5 / Code or Github Copilot backed by Open AI models like GPT 5 /codex (still, though, keep all these prompts general enough to work on other platforms and future versions of Claude and Opus).
2. The user sends the improve_ai_architecture_assistant.user.prompt.md to the optimization_agent.system.prompt.md.
3. The optimization_agent.system.prompt.md will then call each of the agent-specific improvement prompts, as well as the system-wide improvement prompt, to improve the entire AI system, framework, and workflows.
4. The optimization_agent.system.prompt.md will then test the end-to-end system workflows.
5. The optimization_agent.system.prompt.md will then generate an optimization report.
