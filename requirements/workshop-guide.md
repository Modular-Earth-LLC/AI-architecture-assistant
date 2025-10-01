# Requirements Workshop Guide

**Purpose:** Comprehensive requirements gathering for AI agent system design  
**Duration:** 90 minutes  
**When to use:** After successful discovery session, before architecture design

---

## Overview

The requirements workshop is a structured deep-dive into the client's operations. Your goal is to capture enough detail to design and build an AI agent system that actually solves their problems.

This workshop produces a requirements document that becomes the blueprint for your architecture and development work.

---

## Pre-Workshop Preparation

### Review and Research (30-60 minutes)

1. **Review discovery notes:**
   - Pain points identified
   - Technology stack mentioned
   - Business context

2. **Research client's industry:**
   - Common workflows
   - Standard tools and integrations
   - Typical AI use cases

3. **Prepare materials:**
   - Customized question set
   - Workflow diagram templates
   - Note-taking framework

4. **Technical setup:**
   - Screen sharing for collaborative note-taking
   - Diagramming tool ready
   - Recording software (with permission)

---

## Workshop Structure

### Opening (5 minutes)

**Set expectations:**

*"[NAME], thanks for this time. Over the next 90 minutes, we're going to map your operations in detail. This will feel thorough—that's intentional. The more I understand how you work, the better I can design AI agents that fit your process rather than fighting it.*

*I'll ask lots of specific questions and take detailed notes. There are no wrong answers—I need your honest operational reality, not an idealized version.*

*We'll cover six areas: market positioning, brand voice, how you go to market, service delivery workflows, business objectives, and technology stack. The bulk of our time will be on service delivery because that's where AI has the most impact."*

---

## Section 1: Industry & Market Positioning (15 minutes)

### Questions

1. "What industry are you in, and what industries do you serve?"
2. "How do you describe your services to potential clients?"
3. "What makes your approach different from competitors?"
4. "Who is your ideal client?"
5. "What problems do clients have when they come to you?"

### What to Capture

- Primary industry vertical
- Target client profile
- Unique value proposition
- Competitive differentiation
- Common client pain points

### Why It Matters

Understanding market context helps you design agents that:
- Use appropriate industry terminology
- Address real market problems
- Position correctly for the client's differentiation

---

## Section 2: Brand Voice & Values (15 minutes)

### Questions

1. "How would you describe your mission and core values?"
2. "How do you communicate with clients? What tone?"
3. "Does your communication style change by audience?"
4. "Are there specific phrases you use or avoid?"
5. "Show me examples of your typical client communication."

### What to Capture

- Mission statement (exact wording)
- Core values
- Communication style by audience
- Tone preferences (formal/casual/technical/accessible)
- Specific terminology to use or avoid
- Brand voice examples

### Why It Matters

**This section determines how AI agents will communicate.** If you build a formal agent for a casual brand, it will feel wrong. Capture exact language patterns.

**Action:** Request client share example emails, proposals, or marketing materials.

---

## Section 3: Go-to-Market Strategy (15 minutes)

### Questions

1. "How do you currently acquire clients?"
2. "Walk through your sales process from first contact to signed contract."
3. "How do you price your services?"
4. "What's your biggest growth opportunity?"
5. "What prevents you from scaling faster?"

### What to Capture

- Client acquisition channels
- Sales process stages and duration
- Pricing model
- Growth constraints
- Scaling bottlenecks

### AI Opportunities to Listen For

- Lead qualification processes
- Proposal generation workflows
- Client onboarding steps
- Sales collateral creation
- Follow-up communication

---

## Section 4: Core Service Delivery (25 minutes)

### ⚠️ MOST CRITICAL SECTION

This section requires the most time and detail. For each major service, walk through the complete workflow.

### Process for Each Service

For client's top 2-3 services, ask:

1. **Service overview:** "Describe [SERVICE] from the client's perspective. What are they getting?"

2. **Workflow walkthrough:** "Walk me through delivering this service step by step, from contract signing to final delivery."

3. **Digital work:** "For each step, what digital work is involved? What gets created on a computer?"

4. **Judgment vs. routine:** "Which parts require your expert judgment? Which parts are more rule-based?"

5. **Bottlenecks:** "Where does this slow down? What takes longer than you'd like?"

6. **Delegation candidates:** "If you had a perfect assistant who followed instructions exactly, what parts could you delegate?"

7. **Tools & templates:** "What tools do you use? Do you have templates or frameworks?"

### Example Deep Dive

**Client:** "I do financial modeling for SaaS companies."

**Follow-up sequence:**
1. "What specific models do you create most often?"
2. "Walk me through creating one model from scratch."
3. "What data sources do you pull from?"
4. "What parts are formulaic? What requires your judgment?"
5. "How long does a typical model take?"
6. "Do you use a template or start fresh?"
7. "What software do you use?"
8. "What would I see you doing in the first hour?"

### What to Capture

For each service:

- Complete workflow diagram (step-by-step)
- Input requirements (data, documents, information)
- Output deliverables (reports, models, presentations)
- Time requirements (per step and total)
- Decision points requiring expertise
- Routine or repetitive tasks
- Bottlenecks and delays
- Tools used (with specific features)
- Templates or frameworks
- Quality control processes

### Time Allocation

- **1 service:** Full 25 minutes deep dive
- **2 services:** 12 minutes each
- **3+ services:** 8 minutes each, focus on top 2-3

### AI Opportunity Signals

Listen for these phrases:

🔴 **HIGH Priority:**
- "This part is tedious but necessary"
- "I do this for every client"
- "Takes me 5+ hours"
- "Follows this formula"
- "I wish I could delegate this"

🟡 **MEDIUM Priority:**
- "Sometimes this varies"
- "Requires some judgment"
- "Depends on the client"

🟢 **LOW Priority:**
- "Requires deep expertise"
- "Every situation is different"
- "This is core to my value"

---

## Section 5: Business Objectives & Challenges (10 minutes)

### Questions

1. "What are your objectives for the next quarter or year?"
2. "What are your biggest operational challenges right now?"
3. "Where do you imagine AI could help most?"
4. "What would success look like six months from now?"
5. "What concerns do you have about implementing AI?"

### What to Capture

- Quarterly/annual objectives (with metrics if available)
- Current operational challenges
- Client's AI opportunity ideas
- Success metrics and vision
- Concerns or hesitations about AI

### Handling Concerns

If client expresses concerns, capture and note mitigation:

- **"Data security"** → Address in technical architecture
- **"Losing personal touch"** → Position as augmentation, not replacement
- **"Cost"** → Show ROI calculation
- **"Complexity"** → Emphasize gradual implementation
- **"Reliability"** → Discuss human oversight and quality control

---

## Section 6: Technology Stack & Tools (10 minutes)

### Questions

1. "What tools do you use for client work?"
2. "What tools do you use for internal operations?"
3. "How do these tools connect? Where do you manually transfer data?"
4. "Where do your current tools frustrate you?"
5. "How comfortable are you adopting new technology? (Scale 1-10)"

### What to Capture

Complete tool inventory with:

- Tool name and version
- Primary use case
- Frequency of use (daily/weekly/monthly)
- Integration points (or lack thereof)
- API availability (research this later if unknown)
- Data export/import capabilities
- Pain points with current tools
- Technology adoption score (1-10)

### Integration Opportunities

🔴 **Flag these:**
- Manual data transfer between tools
- Repetitive data entry across systems
- Tools that don't talk to each other
- Copy-paste workflows

### Technology Adoption Assessment

- **8-10:** Can propose sophisticated integrations and automation
- **5-7:** Moderate complexity appropriate
- **1-4:** Keep initial system simple, focus on usability

---

## Workshop Wrap-Up (10 minutes)

### Summarize Opportunities

*"[NAME], this has been incredibly valuable. Let me summarize what I'm hearing as the highest-priority opportunities:*

*1. A **[AGENT_TYPE]** that handles [SPECIFIC_TASK], reducing your [X]-hour manual process to [Y] hours of review*

*2. A **[AGENT_TYPE]** that [SPECIFIC_TASK], cutting [PROCESS] time in half*

*3. A **[AGENT_TYPE]** that [SPECIFIC_TASK], freeing you from [ROUTINE_WORK]*

*Does that align with your priorities? Am I missing anything?"*

### Explain Next Steps

*"Here's what happens next:*

*1. I'll compile everything into a detailed requirements document within 48 hours*
*2. You'll review it to ensure accuracy*
*3. Once confirmed, I'll design the system architecture*
*4. Then I'll build a working prototype (usually takes 2-3 weeks)*
*5. We'll meet again for you to test the prototype with real work*

*Let's schedule the prototype review meeting for [DATE_3_WEEKS_OUT]. Does that work?"*

### Final Questions

*"Before we wrap—any questions about the process? Anything else I should know that didn't fit into today's structure?"*

---

## Post-Workshop Tasks

### Immediately After (Within 2 hours)

1. **Organize notes:**
   - Structure by six sections
   - Create workflow diagrams
   - Highlight priority opportunities

2. **Preliminary assessment:**
   - List top 5 AI opportunities
   - Note any missing information
   - Identify integration challenges

3. **Share notes:**
   - Send meeting summary to client
   - Ask for any corrections or additions

### Within 48 Hours

1. **Create requirements document:**
   - Use requirements template
   - Include all six sections
   - Add workflow diagrams
   - Propose specific AI agents

2. **Deliver to client:**
   - Send requirements document
   - Request review and feedback
   - Schedule follow-up call if needed

### Within 1 Week

1. **Finalize requirements:**
   - Incorporate client feedback
   - Resolve any ambiguities
   - Get final approval

2. **Begin architecture phase:**
   - Design system architecture
   - Select technology stack
   - Plan development approach

---

## Workshop Quality Indicators

### ✅ Excellent Workshop

- All six sections completed within 90 minutes
- 3+ service workflows documented step-by-step
- Complete technology stack with integration points
- 5+ specific AI opportunities identified
- Client actively engaged with detailed responses
- Client validates priorities
- Prototype review meeting scheduled

### ⚠️ Adequate Workshop

- All six sections covered (might run slightly over)
- 2 service workflows documented
- Most tools captured
- 3-4 AI opportunities identified
- Client engaged, may need follow-up clarification
- Client generally agrees with priorities

### ❌ Poor Workshop (Requires Follow-Up)

- Sections skipped or rushed
- Only high-level service descriptions (no workflows)
- Incomplete technology stack
- Fewer than 3 AI opportunities
- Client distracted or vague answers
- Priorities unclear
- No confirmed next meeting

---

## Common Challenges & Solutions

### Client gives surface-level answers
**Solution:** Use the "tell me about last time" approach  
*"Rather than generally, tell me about the last time you did [TASK]. Walk me through that specific instance."*

### Client jumps between topics
**Solution:** Acknowledge and redirect  
*"That's interesting—let me note that. We'll come back to it after [CURRENT_SECTION]."*

### Client says "it depends" for everything
**Solution:** Focus on the common case  
*"I understand it varies. What are the 2-3 most common scenarios?"*

### Client doesn't know technical details
**Solution:** Focus on use cases  
*"That's fine—just tell me what you use it for day-to-day. I'll research the technical details."*

### Running significantly over time
**Solution:** Prioritize and schedule follow-up  
*"We have 30 minutes left and still need to cover [X] and [Y]. I may need a brief follow-up call. Let's prioritize [MOST_CRITICAL] for the rest of today."*

### Client fixates on AI limitations
**Solution:** Validate and redirect  
*"You're absolutely right that AI can't [X]. That's why we're not proposing to automate that. Your judgment is irreplaceable. We're looking at whether AI can handle the routine parts so you have more time for strategic work."*

---

## Success Metrics

A successful requirements workshop results in:

1. ✅ All six sections completed
2. ✅ 2+ services with detailed workflow documentation
3. ✅ Complete technology stack (80%+ tools captured)
4. ✅ 5+ specific AI opportunities identified
5. ✅ Client validates top 3 priorities
6. ✅ Prototype review meeting confirmed
7. ✅ Requirements document deliverable within 48 hours

---

## Copy-Paste Checklist

Before the workshop:
- [ ] Discovery notes reviewed
- [ ] Industry research completed
- [ ] Customized questions prepared
- [ ] Diagramming tools ready
- [ ] Screen sharing tested

During the workshop:
- [ ] All six sections covered
- [ ] Service workflows documented
- [ ] Technology stack captured
- [ ] AI opportunities identified
- [ ] Client priorities validated
- [ ] Next meeting scheduled

After the workshop:
- [ ] Notes organized within 2 hours
- [ ] Requirements document created within 48 hours
- [ ] Client review scheduled
- [ ] Architecture phase planned

