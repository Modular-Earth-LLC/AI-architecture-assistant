# System Optimization - User Prompt

**Phase:** Continuous Improvement (Post-Deployment or Periodic)  
**Purpose:** Systematically improve ANY AI system (user-designed systems or this framework itself)  
**Agent:** Optimization Agent  
**Approach:** Discovery-driven, evidence-based, incremental refactoring  
**Output:** Optimization report + implemented improvements

---

## Purpose

Systematically analyze and improve AI systems following discovery-driven optimization principles. Works for:
- **User-designed AI systems** (outputs/prototypes/[project]/)
- **This AI Architecture Assistant framework** (meta-optimization)
- **External AI systems** (any repository or codebase)

**Key Principle:** Discover current state first, assess against best practices, then propose and execute safe, incremental improvements.

---

## When to Use This Prompt

**For User AI Systems:**
- After prototype deployment (optimize performance, costs, UX)
- Quarterly improvement cycles (ongoing enhancement)
- When issues reported (systematic debugging and improvement)
- Before scaling to production (harden and optimize)

**For AI Architecture Assistant (Meta-Optimization):**
- After 5+ projects built with the system (gather learnings)
- Quarterly reviews (keep current with AI best practices)
- When new AI techniques emerge (integrate improvements)
- User feedback indicates confusion or gaps (systematic enhancement)

**Timing:**
- **User systems:** Monthly or quarterly
- **Meta-system:** Quarterly or bi-annually
- **Ad-hoc:** When specific issues identified

---

## Instructions for Optimization Agent

When user invokes this prompt, execute the comprehensive optimization workflow:

### Phase 1: Discovery & Analysis (30-60 minutes)

#### Step 1: Identify Optimization Target

```
<thinking>
What am I optimizing?
- Directory path: [Specify]
- System type: [User AI system / AI Architecture Assistant / External system]
- Scope: [Full system / Specific components]
</thinking>

**Optimization Target Identified:**

**System:** [Name]  
**Location:** [Path]  
**Type:** [Multi-agent / Single agent / Prompt library / Framework]  
**Purpose:** [What this system does]

Beginning comprehensive discovery...
```

---

#### Step 2: System Discovery (File Mapping)

```
<thinking>
Discovery process:

1. List all files in scope:
   - System prompts (.system.prompt.md): [COUNT] files
   - User prompts (.user.prompt.md): [COUNT] files
   - Knowledge base (.json): [COUNT] files
   - Documentation (.md): [COUNT] files
   - Code (.py, .js, etc.): [COUNT] files

2. Categorize by purpose:
   - Agent definitions: [FILES]
   - Task-specific prompts: [FILES]
   - Configuration/data: [FILES]
   - Guides: [FILES]
   - Templates: [FILES]
   - Examples: [FILES]
   - Code implementations: [FILES]

3. Map relationships:
   - [File A] references [Files B, C, D]
   - [File E] duplicates content from [File F]
   - [File G] is orphaned (no references)
   - [File H] is obsolete (superseded by [File I])

4. Identify entry points:
   - User starts with: [File/workflow]
   - Critical path: [Sequence]
</thinking>

✅ **System Discovery Complete**

**System Profile:**
- **Total files:** [COUNT]
- **System structure:** [Description]
- **Entry points:** [Primary, secondary]
- **Target audience:** [Who uses this]
- **Deployment:** [Platform/environment]
```

---

#### Step 3: Best Practices Assessment

Evaluate against established best practices:

**Assessment Framework:**

```
<thinking>
Assessing against AI system best practices:

A. Prompt Engineering (Anthropic/OpenAI standards):
   ✓ Clear role and mission statements
   ✓ XML-structured instructions
   ✓ Concrete examples provided
   ✓ Error handling guidance
   ✓ Chain-of-thought reasoning
   ✗ [Issues found]

B. Multi-Agent Architecture (AWS/Anthropic patterns):
   ✓ Clear separation of concerns
   ✓ No capability duplication
   ✓ Defined coordination patterns
   ✗ [Issues found]

C. Knowledge Management (Data/state handling):
   ✓ Structured data formats (JSON preferred)
   ✓ Schema definitions
   ✓ Version control friendly
   ✗ [Issues found]

D. Repository Organization:
   ✓ Logical directory structure
   ✓ Consistent naming conventions
   ✓ No redundant files
   ✗ [Issues found]

E. Documentation Quality:
   ✓ Clear getting started guide
   ✓ Workflow documentation
   ✓ Examples provided
   ✓ Dual-audience (technical + business)
   ✗ [Issues found]

F. User Experience:
   ✓ <15 min to first result
   ✓ Clear agent/prompt selection
   ✓ Platform-specific guidance
   ✗ [Issues found]

G. Code Quality (if applicable):
   ✓ Modular and maintainable
   ✓ Error handling
   ✓ Tested
   ✗ [Issues found]

Overall Compliance Score: [X/10]
</thinking>

✅ **Best Practices Assessment Complete**

**Strengths:**
- [What's working well - be specific]

**Improvement Opportunities:**
- [Anti-pattern 1]: [Description]
- [Gap 1]: [What's missing]
- [Redundancy 1]: [Duplicate content]
- [Inefficiency 1]: [Performance/cost issue]

**Compliance Score:** [X/10] across [Y] assessment dimensions
```

---

#### Step 4: Identify Specific Optimization Opportunities

```
**Optimization Opportunities Identified:**

**Category 1: Performance Optimizations**

1. **[Opportunity Title]**
   - **Current state:** [Problem description]
   - **Impact:** [HIGH/MEDIUM/LOW]
   - **Benefit:** [Quantified improvement - e.g., "30% faster responses"]
   - **Effort:** [Hours estimate]
   - **Risk:** [LOW/MEDIUM/HIGH]
   - **Priority:** [1-5]

**Category 2: Cost Optimizations**

[Same structure...]

**Category 3: User Experience Optimizations**

[Same structure...]

**Category 4: Quality Optimizations**

[Same structure...]

**Category 5: Structural Optimizations**

[Same structure...]

**Summary:**
- **Total opportunities:** [COUNT]
- **High-impact, low-effort (Quick Wins):** [COUNT]
- **High-impact, high-effort (Strategic):** [COUNT]
- **Low-impact (Refinements):** [COUNT]
```

---

### Phase 2: Optimization Planning (30 minutes)

#### Step 5: Prioritize & Plan Improvements

```
**Optimization Plan:**

**Batch 1: Quick Wins** (High Impact, Low Effort - Do First)
**Estimated Time:** [Hours]

1. **[Optimization 1]**
   - Current: [Problem]
   - Proposed: [Solution]
   - Expected benefit: [Outcome]
   - Implementation steps:
     a. [Step 1]
     b. [Step 2]
   - Validation: [How to test it worked]

2. **[Optimization 2]**
   [Same structure...]

**Batch 2: Strategic Improvements** (High Impact, High Effort)
**Estimated Time:** [Hours]

[Same structure...]

**Batch 3: Refinements** (Low Impact, Low Effort - If Time Permits)
**Estimated Time:** [Hours]

[Same structure...]

**Total Estimated Effort:** [Hours]

**Expected Impact:**
- Performance: [Improvement estimate]
- Cost: [Savings estimate]
- User experience: [Improvement description]
- Maintainability: [Improvement description]

**Risk Assessment:** [Overall risk level of proposed changes]
```

**Get user approval before proceeding:**
```
**Recommendation:** Start with Batch 1 (Quick Wins) to validate approach.

**Shall I proceed with Batch 1 optimizations?**
[Yes / Modify plan / Review details first]
```

---

### Phase 3: Implementation (Variable - Depends on Changes)

#### Step 6: Execute Improvements Incrementally

**For each optimization:**

```
✅ **Executing Optimization [N]: [Title]**

**Implementation Steps:**

<thinking>
1. What am I changing?
   - Files affected: [List]
   - Type of change: [Consolidation / Refactoring / Addition / Deletion]

2. How to execute safely?
   - Backup: [What to preserve]
   - Incremental: [Break into small steps]
   - Validation: [How to test]

3. What could go wrong?
   - Risk: [Identified risk]
   - Mitigation: [How to prevent]
</thinking>

**Step 1:** [Action taken]
**Before:**
[Show current state - relevant excerpt]

**After:**
[Show optimized state - changes made]

**Step 2:** [Next action]
[Same pattern...]

**Validation:**
✅ [Test 1]: PASS - [Result]
✅ [Test 2]: PASS - [Result]

**Status:** Optimization [N] complete ✅

---

[Continue for all approved optimizations]
```

---

### Phase 4: Validation & Reporting (30 minutes)

#### Step 7: Comprehensive Validation

```
**Validation Results:**

**Changes Implemented:** [COUNT] optimizations

**Critical Workflow Testing:**
- [ ] Requirements → Architecture workflow: [PASS/FAIL]
- [ ] Architecture → Engineering workflow: [PASS/FAIL]
- [ ] Knowledge base read/write: [PASS/FAIL]
- [ ] Cross-references updated: [PASS/FAIL]
- [ ] Documentation accurate: [PASS/FAIL]
- [ ] Examples still work: [PASS/FAIL]

**Measured Improvements:**
- **Performance:** [Before] → [After] ([+X%] improvement)
- **Cost:** $[Before]/mo → $[After]/mo ([Y%] reduction)
- **User experience:** [Specific improvement measured]
- **Maintainability:** [Specific improvement - e.g., "File count reduced 30%"]

**Issues Encountered:** [Any problems and how resolved]

**Residual Issues:** [Known limitations or issues to address in future]
```

---

#### Step 8: Generate Optimization Report

```markdown
# Optimization Report - [System Name]

**Optimization Date:** [Date]  
**System Analyzed:** [Name and location]  
**Optimizations Completed:** [COUNT]  
**Total Effort:** [Hours actual vs. estimated]

---

## Executive Summary

**System Before Optimization:**
- [Key metrics/characteristics]

**Optimizations Implemented:**
- [Category 1]: [COUNT] improvements
- [Category 2]: [COUNT] improvements

**Measured Impact:**
- [Improvement 1]: [Quantified]
- [Improvement 2]: [Quantified]
- [Improvement 3]: [Quantified]

**System After Optimization:**
- [New metrics/characteristics]

**Overall Improvement:** [Percentage or description]

---

## Detailed Optimization Log

### Batch 1: Quick Wins

**Optimization 1: [Title]**
- **Before:** [Problem]
- **After:** [Solution]
- **Impact:** [Measured benefit]
- **Files Changed:** [List]
- **Validation:** ✅ Tested and working

[... continue for all optimizations]

---

## Validation Summary

**All Critical Workflows:** ✅ PASS

**Specific Tests:**
- [Test 1]: ✅ PASS
- [Test 2]: ✅ PASS
- [Test 3]: ✅ PASS

**Regression Issues:** [None / List if any]

---

## Recommendations for Future

**Next Optimization Cycle (Suggested: [Timeframe]):**
- [Future improvement 1]
- [Future improvement 2]

**Monitoring Recommendations:**
- Track: [Metric to monitor]
- Alert if: [Condition]

**Continuous Improvement:**
- [Specific ongoing practice]

---

**Files Modified:** [COUNT] files  
**Lines Changed:** +[Additions] / -[Deletions]  
**Net Change:** [Description]

**Git Commit Message:**
```
Optimize [system]: [Brief description of changes]

- [Change 1]
- [Change 2]
- [Change 3]

Measured improvements: [Key metric]
```

---

**Optimization Complete** ✅

**Status:** System validated and operational with improvements.

**Recommended Next Steps:**
- Monitor [metrics] for [duration]
- Schedule next optimization: [Date]
- Gather user feedback on improvements
```

---

## Optimization Principles (Applied Throughout)

### Discovery-Driven

**Never assume structure:**
- ✅ Analyze file system to discover current state
- ✅ Read files to understand content and relationships
- ✅ Map workflows to understand user experience
- ❌ Don't assume file names, locations, or purposes

### Evidence-Based

**Every optimization needs justification:**
- What problem does this solve? (Evidence of issue)
- What's the expected benefit? (Quantified impact)
- What's the effort required? (Realistic estimate)
- What's the risk? (Honest assessment)

### Incremental & Safe

**Refactoring principles:**
1. **Discover before changing** - Comprehensive analysis first
2. **Validate before deleting** - Ensure no capability loss
3. **Incremental changes** - Small, testable improvements
4. **Test after each change** - Validate nothing broke
5. **Document changes** - Clear change history
6. **Preserve version history** - Enable rollbacks (git commits)

### Priority-Driven

**Impact vs. Effort Matrix:**

```
High Impact, Low Effort → Do First (Quick Wins)
High Impact, High Effort → Plan Carefully (Strategic Improvements)
Low Impact, Low Effort → Do If Time (Refinements)
Low Impact, High Effort → Defer (Not worth it)
```

---

## Best Practices Checklist

### For AI Architecture Assistant (Meta-Optimization)

**When optimizing this repository, validate against:**

#### Architecture

- [ ] **Supervisor-worker pattern:** 1 supervisor + N specialized agents
- [ ] **Clear separation:** Each agent has unique, non-overlapping domain
- [ ] **Knowledge base:** JSON format, proper schemas, tool-based access patterns
- [ ] **Multi-shot prompting:** Architecture Agent orchestrates separate user prompts
- [ ] **Platform-agnostic:** Works on Cursor, Claude Projects, AWS Bedrock

#### Prompt Engineering

- [ ] **Anthropic best practices:** XML tags (`<role>`, `<instructions>`, `<examples>`, `<thinking>`)
- [ ] **Concrete examples:** Real use cases (financial operations assistant)
- [ ] **Tool definitions:** Conceptual JSON schemas for knowledge base access
- [ ] **Chain-of-thought:** `<thinking>` tags for reasoning
- [ ] **Dual-audience:** Technical depth + business clarity

#### Knowledge Management

- [ ] **JSON format:** Not YAML (better parsing, validation)
- [ ] **Clear schemas:** system_config, user_requirements, design_decisions
- [ ] **Agent access patterns:** READ/WRITE/UPDATE clearly defined
- [ ] **Version control:** Git-friendly, trackable changes

#### Repository Organization

- [ ] **Logical structure:** `/ai_agents`, `/user_prompts`, `/knowledge_base`, `/guides`, `/outputs`
- [ ] **Naming conventions:** .system.prompt.md, .user.prompt.md, .guide.md
- [ ] **No redundancy:** No capability duplication across files
- [ ] **Clear workflow:** Obvious progression through directories

#### Documentation

- [ ] **Beginner-friendly README:** Junior engineers productive in <15 min
- [ ] **Executive overview:** Business leaders understand value in <15 min
- [ ] **Knowledge base docs:** AI engineers understand schemas
- [ ] **Workflow guides:** Complete lifecycle documented
- [ ] **Examples:** Primary example (financial operations assistant) throughout

#### User Experience

- [ ] **Quick start:** <15 minutes to first result
- [ ] **Clear agent selection:** Easy to find right agent for task
- [ ] **Workflow guidance:** Know what comes next at each phase
- [ ] **Platform deployment:** Cursor, Claude, Bedrock instructions

#### AWS Well-Architected

- [ ] **Architecture Agent enforces:** 6 pillars + ML Lens + GenAI Lens
- [ ] **Diagram generation:** Visualizes Well-Architected compliance
- [ ] **Design decisions:** Document Well-Architected alignment

---

### For User AI Systems

**When optimizing user-designed systems, assess:**

#### Performance

- [ ] Prompt efficiency (token usage, clarity)
- [ ] Response times (latency)
- [ ] Throughput (requests/second)
- [ ] Caching opportunities

#### Cost

- [ ] Model selection (right-sized for task complexity)
- [ ] API call optimization (reduce unnecessary calls)
- [ ] Infrastructure right-sizing
- [ ] Multi-agent cost optimization (cheap models for simple tasks)

#### User Experience

- [ ] Onboarding simplicity
- [ ] Workflow clarity
- [ ] Error handling and recovery
- [ ] Documentation completeness

#### Quality

- [ ] Accuracy and consistency
- [ ] Error handling
- [ ] Validation and testing
- [ ] Code quality (if applicable)

#### Structure

- [ ] Modularity (separation of concerns)
- [ ] Reusability (DRY principle)
- [ ] Maintainability (clear, documented)
- [ ] Scalability (can grow with needs)

---

## Example Optimizations

### Example 1: Optimizing User's Financial Assistant

```markdown
# Optimization Report - Financial Operations Assistant

**System:** outputs/prototypes/financial-operations-assistant/  
**Analysis Date:** 2025-10-04

## Discovery Results

**System Type:** Multi-agent (2 agents: Operations, Analytics)  
**Tech Stack:** Python, Claude Sonnet, Streamlit  
**Lines of Code:** ~800  
**Files:** 15

## Assessment

**Strengths:**
✅ Clear agent separation
✅ Working demo scenarios
✅ Complete documentation

**Improvement Opportunities:**

1. **Prompt Token Reduction** (HIGH IMPACT, LOW EFFORT)
   - Current: Agent prompts are 2,000+ tokens each
   - Opportunity: Reduce by 30% through condensing without losing clarity
   - Benefit: 30% faster responses, 30% lower costs
   - Effort: 2 hours

2. **Model Optimization** (HIGH IMPACT, LOW EFFORT)
   - Current: Using Claude Sonnet for all tasks (including simple categorization)
   - Opportunity: Use Claude Haiku for expense categorization
   - Benefit: 60% cost reduction on categorization (10x cheaper model)
   - Effort: 1 hour (change model parameter)

3. **Response Caching** (HIGH IMPACT, MEDIUM EFFORT)
   - Current: Invoice templates regenerated each time
   - Opportunity: Cache common templates and calculations
   - Benefit: 50% faster invoice generation
   - Effort: 4 hours

## Recommended Optimizations (Prioritized)

**Batch 1 (High Priority - 7 hours):**
1. Model optimization (1 hr)
2. Prompt condensing (2 hrs)
3. Response caching (4 hrs)

**Expected Impact:**
- 30-50% faster responses
- 60% lower categorization costs (~$60/month savings)
- Improved user experience

**Shall I proceed with Batch 1?**
```

---

### Example 2: Optimizing AI Architecture Assistant (Meta)

```markdown
# Optimization Report - AI Architecture Assistant

**System:** AI-architecture-assistant repository  
**Analysis Date:** 2025-10-04

## Discovery Results

**System Type:** Multi-agent framework (1 supervisor + 5 specialized agents)  
**Total Files:** 32 (6 agents, 11 user prompts, 3 knowledge base, 12 docs/guides)  
**Architecture:** Supervisor-worker pattern (AWS Bedrock/Strands)

## Assessment

**Strengths:**
✅ Clear separation of concerns (each agent unique domain)
✅ Multi-shot prompting (Architecture Agent orchestrates 6 user prompts)
✅ Knowledge base for shared state (JSON format)
✅ Anthropic best practices (XML tags, tool patterns)
✅ Dual-audience documentation (technical + business)
✅ AWS Well-Architected enforcement
✅ Primary example integrated (financial operations assistant)

**Improvement Opportunities:**

1. **Example Consistency** (HIGH IMPACT, LOW EFFORT)
   - Current: Financial operations example in Requirements and Architecture agents
   - Opportunity: Ensure same example flows through ALL agents for consistency
   - Benefit: Clear end-to-end demonstration, easier learning
   - Effort: 2 hours

2. **User Prompts Index** (MEDIUM IMPACT, LOW EFFORT)
   - Current: User prompts organized in subdirectories, but no quick reference
   - Opportunity: Create user_prompts/INDEX.md with all prompts categorized
   - Benefit: Faster navigation, clearer when to use which prompt
   - Effort: 1 hour

3. **Platform Deployment Guide** (HIGH IMPACT, MEDIUM EFFORT)
   - Current: Platform deployment mentioned but no step-by-step guide
   - Opportunity: Create guides/platform_deployment.md (Cursor, Claude, Bedrock setup)
   - Benefit: Users can actually deploy, not just design
   - Effort: 8-10 hours

4. **Knowledge Base README Enhancement** (MEDIUM IMPACT, LOW EFFORT)
   - Current: Knowledge base has embedded comments, basic README
   - Opportunity: Enhance with more examples, troubleshooting
   - Benefit: AI engineers understand data structures better
   - Effort: 2 hours (COMPLETED in recent refactoring)

## Recommended Optimizations

**Batch 1 (High Priority - 3 hours):**
1. Example consistency across agents (2 hrs)
2. User prompts index (1 hr)

**Batch 2 (Medium Priority - 10 hours):**
3. Platform deployment guide (8-10 hrs)

**Batch 3 (Future - Defer):**
- Additional use case examples
- Video tutorials (describe, don't create)
- Advanced patterns library

**Expected Impact:**
- 30% easier to use (better navigation, consistent examples)
- 50% higher deployment success (platform guides)
- Improved documentation completeness

**Shall I proceed with Batch 1 optimizations?**
```

---

## Refactoring Principles (From Original Refactor)

**When optimizing AI Architecture Assistant, follow these proven principles:**

### Consolidation Strategy

**Identify Redundancy:**
1. **File-level:** Multiple files doing the same thing
2. **Content-level:** Duplicate instructions across files
3. **Capability-level:** Overlapping agent responsibilities

**Consolidation Approach:**
1. **Analyze overlap:** Compare similar files, extract unique capabilities
2. **Design consolidated version:** Preserve all functionality, remove duplication
3. **Migrate references:** Update all cross-references
4. **Validate preservation:** Ensure no capability loss
5. **Delete obsolete:** Remove old files after validation

### Knowledge Base Pattern

**Ensure proper implementation:**
- JSON format (not YAML)
- Clear schemas (system_config, user_requirements, design_decisions)
- Agent access patterns (READ/WRITE/UPDATE per agent)
- Tool-based access (following Anthropic patterns)
- Version control friendly

### Multi-Agent Architecture

**Validate structure:**
- Supervisor orchestrates specialized workers
- Each specialized agent has unique domain
- No capability overlap
- Clear workflow sequencing (requirements → architecture → engineering → deployment)
- Knowledge base enables smooth handoffs

### Dual-Audience Design

**Check every output:**
- Technical depth for builders (specifications, implementation guidance)
- Business clarity for leaders (ROI, risk assessment, recommendations)
- Translation between technical and business concepts
- Both internal projects AND client work considerations

---

## Success Criteria

Optimization is successful when:

✅ **Thorough Discovery**
- Complete file mapping
- Relationship analysis
- Workflow reconstruction

✅ **Evidence-Based Assessment**
- Compliance score against best practices
- Specific issues identified
- Prioritized improvement opportunities

✅ **Safe Implementation**
- No broken functionality
- All critical workflows tested
- Cross-references updated
- Version history preserved (git commits)

✅ **Measured Impact**
- Before/after metrics documented
- Expected improvements validated
- User experience enhanced

✅ **Clear Documentation**
- Optimization report generated
- Changes documented
- Future recommendations provided

✅ **Validation Passed**
- All tests passing
- No regression issues
- System operational

---

## Notes for Optimization Agent

**This is a USER PROMPT for systematic optimization:**

**Your role:**
1. Execute the 4-phase workflow (Discovery → Planning → Implementation → Validation)
2. Use `<thinking>` tags for analysis (show your reasoning)
3. Get user approval before implementing changes
4. Test thoroughly after each change
5. Generate comprehensive optimization report

**Key principles:**
- Discovery-driven (never assume)
- Evidence-based (prove the need)
- Incremental (small, safe changes)
- Validated (test everything)
- Documented (clear change history)

**Special consideration for meta-optimization:**
When optimizing the AI Architecture Assistant itself, you're improving the system you're part of. Treat it like any other system—discover, assess, improve, validate. Your discovery-driven approach prevents the need for explicit self-awareness.

---

## Output Checklist

Before declaring optimization complete:

- [ ] Discovery phase completed (file mapping, assessment)
- [ ] Optimization plan created and approved
- [ ] Changes implemented incrementally
- [ ] Each change validated individually
- [ ] All critical workflows tested
- [ ] Optimization report generated
- [ ] Git commits made with clear messages
- [ ] Future recommendations documented

---

**Version:** 2.0  
**Last Updated:** 2025-10-03  
**Replaces:** optimization/optimize-ai-architecture-system.user.prompt.md  
**Updated For:** New multi-agent architecture, knowledge base pattern, dual-audience design  
**Approach:** Discovery-driven optimization for any AI system
