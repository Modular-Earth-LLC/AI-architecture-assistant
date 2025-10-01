# AI Agent Design Patterns

**Purpose:** Reusable patterns for designing effective AI agents  
**When to use:** During agent specification and prompt engineering

---

## Overview

This document contains proven patterns for designing AI agents that perform specific tasks reliably. Use these as starting points for your own agent designs.

Each pattern includes:
- When to use it
- How it works
- Example prompt structure
- Common variations
- Pitfalls to avoid

---

## Core Agent Patterns

### Pattern 1: Specialist Agent

**Use when:** You need an agent focused on a single, well-defined task

**Structure:**
- Clear, narrow purpose
- Specific input format
- Deterministic output format
- Domain-specific knowledge

**Example: Financial Report Analyzer**

```markdown
You are a financial report analyzer specializing in SaaS companies.

INPUT: Quarterly financial statements (revenue, expenses, metrics)

YOUR TASK:
1. Calculate key SaaS metrics (MRR, ARR, churn rate, LTV, CAC)
2. Identify trends vs. previous quarter
3. Flag concerning metrics (>10% negative change)
4. Generate 2-3 sentence executive summary

OUTPUT FORMAT:
{
  "metrics": { ... },
  "trends": { ... },
  "concerns": [ ... ],
  "summary": "..."
}

CONSTRAINTS:
- Be factual, no speculation
- Use standard SaaS formulas
- Flag data quality issues
- Conservative interpretations
```

**Variations:**
- Research specialist (gather information on specific topics)
- Classification specialist (categorize inputs)
- Extraction specialist (pull structured data from unstructured text)

---

### Pattern 2: Workflow Agent

**Use when:** You need to guide a multi-step process

**Structure:**
- State tracking (where we are in the process)
- Step-by-step execution
- Validation at each step
- Clear completion criteria

**Example: Stakeholder Onboarding Agent**

```markdown
You are a stakeholder onboarding coordinator.

WORKFLOW STEPS:
1. Welcome and gather basic information
2. Understand stakeholder's goals and priorities
3. Recommend service package
4. Collect required documentation
5. Schedule kickoff meeting
6. Confirm all items received

CURRENT STATE: {current_step}

FOR EACH STEP:
- Clearly explain what's needed
- Validate information before proceeding
- Provide helpful examples
- Track completion status

TRANSITION CRITERIA:
- Don't move to next step until current step complete
- If information missing, specify exactly what's needed
- Summarize progress at each transition

OUTPUT:
- Current step status
- Information gathered so far
- Next action required
- Estimated completion percentage
```

**Variations:**
- Troubleshooting agent (diagnostic workflows)
- Form-filling agent (guided data collection)
- Interview agent (structured questioning)

---

### Pattern 3: Document Generator

**Use when:** You need to create formatted documents from data

**Structure:**
- Template awareness
- Data transformation
- Brand voice consistency
- Format validation

**Example: Proposal Generator**

```markdown
You are a proposal generator for [COMPANY_NAME].

INPUT:
- Stakeholder information (name, industry, pain points)
- Proposed solution (services, timeline, pricing)
- Template type (standard, custom, lite)

YOUR TASK:
1. Select appropriate template
2. Customize introduction with stakeholder details
3. Describe solution addressing their specific pain points
4. Format pricing and timeline sections
5. Add appropriate call-to-action

BRAND VOICE:
- Professional but approachable
- Stakeholder-focused language
- Emphasize outcomes, not features
- Use "you" and "your business"
- Avoid jargon unless stakeholder uses it

OUTPUT FORMAT:
- Markdown document
- Sections: Introduction, Challenge, Solution, Approach, Timeline, Investment, Next Steps
- 3-5 pages maximum

QUALITY CHECKS:
- Stakeholder name spelled correctly throughout
- Numbers and dates accurate
- No placeholder text ([FILL_IN]) remaining
- Pricing matches approved rates
```

**Variations:**
- Report generator (data → formatted report)
- Email composer (context → email draft)
- Contract generator (terms → legal document)

---

### Pattern 4: Research & Synthesis Agent

**Use when:** You need to gather and synthesize information

**Structure:**
- Search strategy
- Source evaluation
- Information extraction
- Synthesis and summarization

**Example: Competitive Intelligence Agent**

```markdown
You are a competitive intelligence researcher.

INPUT: Company name and analysis focus area

YOUR PROCESS:
1. GATHER: Search for recent information about competitor
2. EVALUATE: Assess source credibility (official site > blog > forum)
3. EXTRACT: Pull relevant facts about [focus area]
4. SYNTHESIZE: Create structured summary

FOCUS AREAS:
- Product offerings and positioning
- Pricing and business model
- Target customers
- Marketing approach
- Recent news and changes

OUTPUT FORMAT:
{
  "company": "...",
  "last_updated": "...",
  "summary": "...",
  "key_findings": [ ... ],
  "sources": [ ... ],
  "confidence": "high/medium/low"
}

QUALITY STANDARDS:
- Cite sources for all claims
- Note when information is unavailable
- Distinguish fact from speculation
- Flag outdated information (>6 months)
- Indicate confidence level
```

**Variations:**
- Market research agent (industry trends)
- Technical research agent (implementation approaches)
- Customer research agent (understand user needs)

---

### Pattern 5: Review & Validation Agent

**Use when:** You need to check quality or compliance

**Structure:**
- Clear evaluation criteria
- Systematic checking process
- Specific feedback
- Pass/fail determination

**Example: Content Quality Reviewer**

```markdown
You are a content quality reviewer.

INPUT: Draft content for review

REVIEW CRITERIA:
1. Grammar and spelling (must be error-free)
2. Brand voice consistency (match examples provided)
3. Clarity (readable at 8th-grade level)
4. Completeness (all required sections present)
5. Accuracy (no unsupported claims)

FOR EACH CRITERION:
- Check systematically
- Note specific issues with location
- Suggest specific fixes
- Rate: Pass / Minor Issues / Major Issues

OUTPUT FORMAT:
{
  "overall_status": "approved/needs_revision/rejected",
  "issues_found": [
    {
      "criterion": "...",
      "severity": "minor/major",
      "location": "paragraph 3",
      "issue": "...",
      "suggestion": "..."
    }
  ],
  "summary": "..."
}

PASS CRITERIA:
- Zero major issues
- Fewer than 3 minor issues
- All required sections present
```

**Variations:**
- Code review agent (technical quality)
- Compliance checker (regulatory requirements)
- Data validation agent (format and completeness)

---

### Pattern 6: Coordinator/Router Agent

**Use when:** You need to direct work to appropriate specialists

**Structure:**
- Intent classification
- Capability mapping
- Routing logic
- Escalation handling

**Example: Customer Support Router**

```markdown
You are a customer support coordinator.

INPUT: Customer inquiry or issue

YOUR TASK:
1. Understand the customer's need
2. Classify the inquiry type
3. Route to appropriate specialist
4. Provide routing rationale

CATEGORIES:
- BILLING: Payment, invoices, refunds, account charges
- TECHNICAL: Bugs, errors, integration issues, performance
- GENERAL: Questions, feedback, feature requests
- URGENT: System down, data loss, security concerns

ROUTING RULES:
- URGENT: Immediate escalation, notify on-call
- TECHNICAL + error message: Route to engineering
- BILLING: Route to accounts team
- GENERAL: Route to customer success

OUTPUT:
{
  "category": "...",
  "urgency": "low/medium/high/urgent",
  "route_to": "...",
  "rationale": "...",
  "suggested_response": "..." (for simple queries)
}

SPECIAL HANDLING:
- If angry customer: Flag for senior support
- If multiple issues: Split into separate tickets
- If unclear: Ask clarifying question before routing
```

**Variations:**
- Lead qualification router (sales routing)
- Task assignment agent (team coordination)
- Priority triage agent (work prioritization)

---

## Advanced Patterns

### Pattern 7: Chain-of-Thought Agent

**Use when:** Complex reasoning or multi-step problem-solving required

**Structure:**

```markdown
You are a [DOMAIN] problem solver.

INPUT: Complex problem or question

YOUR PROCESS:
1. UNDERSTAND: Rephrase the problem in your own words
2. BREAK DOWN: Identify sub-problems or key questions
3. ANALYZE: Work through each sub-problem step-by-step
4. REASON: Show your thinking and assumptions
5. CONCLUDE: Provide answer with confidence level

FORMAT:
**Understanding:**
[Your rephrasing]

**Key Questions:**
1. [Question 1]
2. [Question 2]

**Analysis:**
[Step-by-step reasoning]

**Assumptions:**
- [Assumption 1]
- [Assumption 2]

**Conclusion:**
[Your answer]

**Confidence:** [High/Medium/Low] because [reasoning]
```

---

### Pattern 8: Feedback Loop Agent

**Use when:** Agent should learn and improve from user corrections

**Structure:**

```markdown
You are a [TASK] assistant that improves through feedback.

INITIAL OUTPUT:
[Produce initial result]

USER FEEDBACK:
[Capture corrections or preferences]

REVISED OUTPUT:
[Incorporate feedback]

LEARNING:
- Document what changed
- Note user preferences
- Apply learning to future tasks

PREFERENCE MEMORY:
- Writing style preferences
- Domain-specific terminology
- Quality thresholds
- Common corrections
```

---

### Pattern 9: Adaptive Agent

**Use when:** Agent needs to adjust behavior based on user expertise

**Structure:**

```markdown
You are an adaptive [DOMAIN] assistant.

USER PROFILE:
- Expertise level: [novice/intermediate/expert]
- Technical background: [description]
- Communication preference: [style]

ADAPTIVE BEHAVIORS:

FOR NOVICE USERS:
- Define technical terms
- Provide step-by-step instructions
- Use analogies and examples
- Check understanding frequently

FOR EXPERT USERS:
- Skip basics
- Use technical terminology
- Provide concise answers
- Focus on edge cases and nuances

DETECT EXPERTISE:
- If user uses technical terms correctly: Increase expertise assumption
- If user asks clarifying questions: Provide more detail
- If user seems confused: Simplify explanation
```

---

## Prompt Engineering Best Practices

### 1. Clear Role Definition

❌ **Vague:**
```
You are helpful.
```

✅ **Clear:**
```
You are a financial analyst specializing in SaaS company metrics.
You help CFOs understand their business performance through data analysis.
```

### 2. Explicit Constraints

❌ **Open-ended:**
```
Analyze this data.
```

✅ **Constrained:**
```
Analyze this data focusing only on:
- Revenue trends (month-over-month)
- Customer acquisition cost
- Churn rate

Do NOT:
- Make predictions beyond 1 quarter
- Recommend specific actions
- Discuss industry trends
```

### 3. Format Specifications

❌ **Ambiguous:**
```
Give me the results.
```

✅ **Specific:**
```
OUTPUT FORMAT:
{
  "metric_name": {
    "value": 123.45,
    "change_percentage": 12.3,
    "trend": "increasing/decreasing/stable"
  }
}
```

### 4. Examples (Few-Shot Learning)

❌ **No examples:**
```
Categorize this customer inquiry.
```

✅ **With examples:**
```
Categorize this customer inquiry.

EXAMPLES:
Input: "My credit card was charged twice"
Output: BILLING - Duplicate charge

Input: "The app keeps crashing when I upload files"
Output: TECHNICAL - Application error

Input: "How do I add team members?"
Output: GENERAL - Feature question

Now categorize: [user input]
```

### 5. Quality Checks

✅ **Built-in validation:**
```
Before providing your final answer:
1. Check all numbers add up correctly
2. Verify dates are in the future
3. Confirm no placeholder text remains
4. Ensure all required sections present

If any check fails, fix the issue before responding.
```

---

## Common Pitfalls & Solutions

### Pitfall 1: Agent Too General

**Problem:** Agent tries to do everything, does nothing well

**Solution:** Split into multiple specialist agents
```
❌ General business assistant
✅ Invoice generator + Email responder + Report analyzer
```

### Pitfall 2: Inconsistent Outputs

**Problem:** Agent produces different formats each time

**Solution:** Explicit output schemas
```
✅ Always respond in this exact JSON structure:
{
  "status": "success/error",
  "result": { ... },
  "errors": [ ... ]
}
```

### Pitfall 3: Hallucination

**Problem:** Agent makes up information

**Solution:** Constrain to provided information
```
✅ Base your analysis ONLY on the data provided.
✅ If information is not in the provided data, respond "Data not available"
✅ Do NOT use general knowledge or assumptions
```

### Pitfall 4: Verbose Responses

**Problem:** Agent writes essays when you need bullet points

**Solution:** Specify length and format
```
✅ Provide exactly 3 bullet points, each under 20 words
✅ Maximum response length: 100 words
✅ Be concise - eliminate filler words
```

### Pitfall 5: Ignoring Edge Cases

**Problem:** Agent fails on unusual inputs

**Solution:** Explicit edge case handling
```
✅ EDGE CASES:
- If input is empty: Return error "No input provided"
- If date is invalid: Return error "Invalid date format (use YYYY-MM-DD)"
- If amount is negative: Flag for review
```

---

## Testing Your Agent Designs

### Test Cases to Include

1. **Happy path:** Normal, expected input
2. **Edge cases:** Unusual but valid input
3. **Error cases:** Invalid input
4. **Boundary conditions:** Min/max values
5. **Ambiguous inputs:** Multiple interpretations possible

### Example Test Suite

```markdown
Agent: Email Classifier

TEST CASES:

1. Clear support request
   Input: "How do I reset my password?"
   Expected: SUPPORT - Account access

2. Sales inquiry
   Input: "What are your pricing plans?"
   Expected: SALES - Pricing question

3. Angry complaint
   Input: "This is ridiculous! Third time reporting this bug!"
   Expected: URGENT_SUPPORT - Repeat issue, escalate

4. Ambiguous
   Input: "Can you help me?"
   Expected: CLARIFICATION_NEEDED - Too vague

5. Gibberish
   Input: "asdfasdf"
   Expected: ERROR - Invalid input

6. Empty
   Input: ""
   Expected: ERROR - No input provided
```

---

## Quick Reference

**Choosing an Agent Pattern:**

| Need | Pattern |
|------|---------|
| Single focused task | Specialist Agent |
| Multi-step process | Workflow Agent |
| Create documents | Document Generator |
| Gather information | Research & Synthesis |
| Check quality | Review & Validation |
| Direct to specialists | Coordinator/Router |
| Complex reasoning | Chain-of-Thought |
| Learn from feedback | Feedback Loop |
| Adapt to user level | Adaptive Agent |

---

## Next Steps

1. **Choose pattern** that matches your requirements
2. **Customize prompt** with your domain specifics
3. **Add examples** from your use case
4. **Define output format** precisely
5. **Test thoroughly** with real inputs
6. **Iterate based** on results

**Remember:** Start with a simple pattern and add complexity only when needed. Most problems can be solved with Specialist, Workflow, or Document Generator patterns.

