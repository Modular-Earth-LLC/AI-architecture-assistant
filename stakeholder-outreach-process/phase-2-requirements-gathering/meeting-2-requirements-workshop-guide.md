# Meeting 2: Requirements Workshop Guide

**Phase:** Requirements Gathering  
**Duration:** 90 minutes  
**Timing:** Within 1 week of Email 2  
**Purpose:** Comprehensive business understanding, AI opportunity identification  
**Agents:** requirements-workshop-agent, notetaker-agent  

---

## Pre-Workshop Preparation

### Human Tasks

- Review discovery call notes thoroughly
- Study any materials client provided
- Research industry-specific workflows and pain points
- Prepare screen sharing for collaborative note-taking
- Set up video conferencing

### Agent Tasks (requirements-workshop-agent)

- Generate customized question set based on discovery insights
- Create requirement capture framework
- Prepare workflow diagram templates
- Build time-tracking dashboard for workshop
- Brief human facilitator on key focus areas

---

## Workshop Opening (5 minutes)

**Script:**

"[CLIENT_FIRST_NAME], thanks for making this time. Over the next ninety minutes, we're going to map out [CLIENT_COMPANY_NAME]'s operations in detail. This will feel quite thorough—that's intentional. The more I understand about how you work, the better I can build AI agents that fit seamlessly into your process rather than fighting against it.

I'll be taking notes throughout and asking lots of specific questions. There are no wrong answers—I need your honest operational reality, not an idealized version. If something is messy or inconsistent, that's fine. Most businesses have some of that.

We'll cover six areas: your market positioning, your brand, how you go to market, how you deliver services, your business objectives, and your technology stack. The bulk of our time will be on service delivery because that's where AI agents have the most impact.

Any questions before we dive in?"

**Agent Support:**

- requirements-workshop-agent displays agenda on screen share
- notetaker-agent begins capturing conversation
- requirements-workshop-agent sets 90-minute countdown timer

---

## Section 1: Industry and Market Positioning (15 minutes)

### Questions

**Q1: Industry Definition**
"Let's start broad. How do you describe what industry you're in, and what industries do you primarily serve?"

**Q2: Service Description**
"When someone asks what [CLIENT_COMPANY_NAME] does, what do you tell them?"

**Q3: Competitive Differentiation**
"What makes your approach different from other [INDUSTRY] consultants or service providers? What do you do that others don't?"

**Q4: Ideal Client Profile**
"Describe your ideal client. What do they look like in terms of size, industry, maturity, challenges?"

**Q5: Client Problems**
"What problems do clients typically have when they first come to you? What are they struggling with?"

### Section 1 What to Capture

- Primary industry vertical(s)
- Target client demographics
- Unique value proposition
- Competitive advantages
- Common client pain points at intake

### Agent Guidance

#### Section 1: Industry & Market (15 min)

- Progress: [X/5 questions]
- Key captures:
  - ✓ Industry: [VALUE]
  - ✓ Target clients: [VALUE]
  - ✓ Differentiation: [VALUE]
- ⚠️ Watch for:
  - Generic descriptions → Probe for specifics
  - "We do everything" → Help client narrow focus
  - Unclear value prop → Ask for client testimonial language
- Time check: [X] minutes remaining in section

---

## Section 2: Brand Voice and Values (15 minutes)

### Section 2 Questions

**Q1: Mission and Values**
"How would you describe [CLIENT_COMPANY_NAME]'s mission? What are your core values?"

**Q2: Communication Style**
"How do you communicate with clients? What's your tone—formal, casual, technical, accessible?"

**Q3: Stakeholder Differentiation**
"Does your communication style change when you're talking to clients versus contractors or partners? How?"

**Q4: Language Preferences**
"Are there specific phrases or terms you use consistently? Any words or approaches you specifically avoid?"

**Q5: Integration of Unique Elements**
"I noticed [UNIQUE_ELEMENT_FROM_RESEARCH]. How does that integrate into your daily operations and client interactions?"

### Section 2 What to Capture

- Mission statement (exact wording)
- Core values (client's language)
- Communication style guidelines
- Tone preferences by audience
- Specific terminology to use/avoid
- Brand voice examples from actual communications

### Critical Importance

This section determines how AI agents will communicate on behalf of the business. Capture exact phrases and language patterns.

### Section 2 Agent Guidance

#### Section 2: Brand Voice (15 min)

- 🔴 CRITICAL: Capture exact language patterns
- Current captures:
  - ✓ Mission: "[EXACT_QUOTE]"
  - ✓ Values: [LIST]
  - ✓ Client tone: [DESCRIPTION]
- ⚠️ Need examples:
  - How does client open emails to clients?
  - How does client close proposals?
  - What phrases appear in their marketing?
- Action: Request client share example email/proposal if available

---

## Section 3: Go-to-Market Strategy (15 minutes)

### Section 3 Questions

**Q1: Client Acquisition**
"How do you currently find and acquire clients? What channels work best?"

**Q2: Sales Process**
"Walk me through your sales process from first contact to signed contract. What are the stages?"

**Q3: Pricing Model**
"How do you price your services? Hourly, project-based, retainer? Why that model?"

**Q4: Differentiation in Practice**
"When a client chooses you over a competitor, what do they cite as the reason?"

**Q5: Growth and Scaling**
"Where do you see the biggest opportunity for growth? What's preventing you from scaling faster?"

### Section 3 What to Capture

- Client acquisition channels (with success rates if available)
- Sales process stages and typical duration
- Pricing model and rationale
- Win factors in competitive situations
- Growth opportunities
- Scaling bottlenecks

### Section 3 Agent Guidance

#### Section 3: Go-to-Market (15 min)

- Current captures:
  - ✓ Acquisition: [CHANNELS]
  - ✓ Sales cycle: [DURATION]
  - ✓ Pricing: [MODEL]
- 🔴 AI OPPORTUNITIES:
  - If "proposal creation takes too long" → Proposal generation agent
  - If "lead qualification manual" → Lead scoring agent
  - If "follow-up inconsistent" → Client communication agent
- Time check: 45 minutes elapsed, on schedule

---

## Section 4: Core Service Delivery (25 minutes)

### Critical Section Note

This is the most critical section—allocate full 25 minutes

### Process for Each Service

For client's top 2-3 services, work through this sequence:

**Step 1: Service Overview**
"Describe [SERVICE_NAME] from the client's perspective. What are they getting?"

**Step 2: Workflow Walkthrough**
"Walk me through delivering this service step by step. Start from when a client signs the contract."

**Step 3: Digital Work Identification**
"For each step, what digital work is involved? What gets created on a computer?"

**Step 4: Judgment vs. Routine**
"Which parts require your expert judgment? Which parts are more routine or rule-based?"

**Step 5: Bottleneck Identification**
"Where does this process typically slow down? What takes longer than you'd like?"

**Step 6: Delegation Opportunities**
"If you had a junior analyst who followed instructions perfectly, what parts of this could you delegate?"

**Step 7: Tools and Templates**
"What tools do you use for this? Do you have templates or frameworks?"

### Example Deep Dive

**Client:** "I do financial modeling for SaaS companies."

**Follow-up sequence:**

1. "What specific models do you create most often?"
2. "Walk me through creating one of these models from scratch."
3. "What data sources do you pull from?"
4. "What parts of the model are formulaic? What parts require your judgment?"
5. "How long does a typical model take you?"
6. "Do you use a template or start fresh each time?"
7. "What software do you use?"
8. "If I watched you create a model, what would I see you doing for the first hour?"

### Section 4 What to Capture

For each service:

- Complete workflow diagram (step-by-step with decision points)
- Input requirements (data, documents, client information)
- Output deliverables (reports, models, presentations, recommendations)
- Time requirements (per step and total)
- Decision points requiring expertise
- Routine or repetitive tasks
- Bottlenecks and delays
- Tools used (with specific features)
- Templates or frameworks employed
- Quality control processes

### Agent Intensive Guidance

SECTION 4: Service Delivery (25 min) - MOST CRITICAL
Current service: [SERVICE_NAME]
Workflow steps captured: [COUNT]
CAPTURE CHECKLIST FOR THIS SERVICE:
✓ Service description
✓ Trigger/start point
✓ Step-by-step workflow
✓ Decision points mapped
✓ Digital artifacts identified
✓ Time estimates per step
✓ Bottlenecks flagged
✓ Tools documented
⚠️ Still need: Templates/frameworks
🔴 AI OPPORTUNITY SIGNALS:

"This part is tedious" → HIGH priority
"I do this for every client" → HIGH priority (scalable)
"Takes me 5+ hours" → HIGH priority (time savings)
"Follows this formula" → HIGH priority (automatable)
"Requires deep expertise" → LOW priority (keep human)

PROBING QUESTIONS READY:

"What's the first thing you do?"
"Then what happens?"
"What do you create at this step?"
"How do you decide [X]?"
"What takes the most time here?"

TIME: [X] minutes remaining - pace appropriately
If 3 services: 8 min each
If 2 services: 12 min each
If 1 service: Full 25 min deep dive

---

## Section 5: Business Objectives and Challenges (10 minutes)

### Section 5 Questions

**Q1: Near-Term Objectives**
"What are your main objectives for the next quarter or year?"

**Q2: Operational Challenges**
"What are your biggest operational challenges right now? What keeps you up at night?"

**Q3: AI Vision**
"Where do you imagine AI could help your business most?"

**Q4: Success Definition**
"If we successfully implement AI agents, what would success look like six months from now? What would be different?"

**Q5: Concerns**
"What concerns or hesitations do you have about implementing AI in your practice?"

### Section 5 What to Capture

- Specific quarterly/annual objectives (with metrics if available)
- Current operational challenges (prioritized)
- Client's own AI opportunity ideas
- Success metrics and vision
- Concerns, fears, or hesitations about AI

### Section 5 Agent Guidance

#### Section 5: Objectives & Challenges (10 min)

Linking analysis:
Objective: [STATED_GOAL]
↓
Related pain point: [FROM_DISCOVERY]
↓
Service workflow: [FROM_SECTION_4]
↓
Proposed AI solution: [AGENT_TYPE] to [SPECIFIC_ACTION]
CONCERN HANDLING:
If client expresses concern, capture and note mitigation:

"Data security" → Address in technical architecture
"Losing personal touch" → Position as augmentation
"Cost" → Show ROI calculation
"Complexity" → Emphasize gradual implementation
"Reliability" → Discuss supervision and quality control

Time check: 75 minutes elapsed, 15 minutes remaining

---

## Section 6: Technology Stack and Tools (10 minutes)

### Section 6 Questions

**Q1: Client-Facing Tools**
"What tools do you use for client work? Walk me through your primary tools."

**Q2: Internal Operations Tools**
"What tools do you use for internal operations—CRM, project management, documentation?"

**Q3: Integration Status**
"How do these tools connect to each other? Where do you manually transfer data between systems?"

**Q4: Pain Points**
"Where do your current tools frustrate you? What do you wish worked better?"

**Q5: Technology Comfort**
"On a scale of 1-10, how comfortable are you adopting new technology? What's your typical process for learning a new tool?"

### Section 6 What to Capture

Complete tool inventory with:

- Tool name and version
- Primary use case
- Frequency of use (daily/weekly/monthly)
- Integration points (or lack thereof)
- API availability status
- Data export/import capabilities
- User pain points
- Technology adoption willingness score

### Section 6 Agent Guidance

#### Section 6: Technology Stack (10 min)

TOOL INVENTORY:
Client-Facing:

[TOOL_NAME]: [USE_CASE] - API: [Y/N]
[TOOL_NAME]: [USE_CASE] - API: [Y/N]

Internal Operations:

[TOOL_NAME]: [USE_CASE] - API: [Y/N]
[TOOL_NAME]: [USE_CASE] - API: [Y/N]

🔴 INTEGRATION OPPORTUNITIES:
Where manual data transfer happens:

[SOURCE_TOOL] → [DESTINATION_TOOL]: Manual [PROCESS]
This is automation opportunity

API AVAILABILITY:
✓ Robust API: High integration potential - Priority 1
⚠️ Limited API: Some integration possible - Priority 2
❌ No API: Workarounds needed - Priority 3
ADOPTION LEVEL: [SCORE]/10

8-10: Can propose sophisticated integrations
5-7: Moderate complexity appropriate
1-4: Keep initial system simple, focus on usability

Time: 85 minutes elapsed - wrap up in 5 minutes

---

## Workshop Wrap-Up (10 minutes)

### Summary and Validation

**Script:**

"[CLIENT_FIRST_NAME], this has been incredibly valuable. Let me summarize what I'm hearing as the highest-priority opportunities:

**[Summarize top 3-5 opportunities with specific agent types]**

For example:

1. A **report automation agent** that pulls data from [TOOL] and generates your standard financial reports, reducing your 8-hour manual process to 1 hour of review
2. A **research assistant agent** that gathers industry data and competitive intelligence for your client proposals, cutting proposal prep time in half
3. A **client communication agent** that drafts follow-up emails and status updates in your voice, freeing you from routine correspondence

Does that align with your priorities? Is there anything I'm missing or misunderstanding?"

### Next Steps Communication

**Script:**

"Here's what happens next:

1. I'll compile everything we discussed today into a detailed requirements document within 48 hours
2. You'll review that document to ensure I captured everything accurately
3. Once you confirm the requirements, I'll spend about two weeks building a working prototype
4. We'll meet again in about three weeks for you to interact with the actual AI agents

The prototype won't be a slideshow or a demo video—it will be a functional system you can actually use with your real work to see if it delivers value.

I've scheduled our prototype review meeting for [DATE/TIME]. Does that work for your calendar?"

### Final Questions

**Script:**

"Before we wrap up—any questions about the process? Anything else about your operations I should know that didn't fit into today's structure?"

### Agent Guidance for Wrap-Up

WRAP-UP CHECKLIST (10 min):
✓ Summarize top 3-5 AI opportunities
✓ Get client validation on priorities
✓ Explain next steps clearly
✓ Confirm prototype review meeting date
✓ Address final questions
PRIORITY VALIDATION TEMPLATE:
"Based on today's workshop, the highest-value opportunities are:

[AGENT_TYPE] for [TASK]

Addresses: [PAIN_POINT]
Saves: [TIME_ESTIMATE]/week
Current process: [MANUAL_METHOD]
Proposed process: [AI_AUGMENTED_METHOD]

[Repeat for 2-3 more agents]

Do these align with where you'd want to start?"
MEETING SCHEDULING:
Do not leave workshop without confirmed prototype review date.
If client uncertain: "Let's tentatively hold [DATE]. I'll send confirmation once the prototype is closer to ready."
COMPLETENESS CHECK:
All six sections covered: ✓
Service workflows documented: [COUNT] ✓
Technology stack captured: ✓
AI opportunities identified: [COUNT] ✓
Next meeting scheduled: ✓
Workshop complete at: [TIME] ([OVER/UNDER] schedule by [X] min)

---

## Post-Workshop Tasks

### Immediate (Within 2 Hours)

**Agent Tasks:**

1. notetaker-agent generates structured notes
2. requirements-workshop-agent creates preliminary opportunity assessment
3. orchestrator-agent validates completeness of capture

**Human Tasks:**

1. Review agent-generated notes while workshop is fresh in memory
2. Clarify any ambiguous points
3. Approve initiation of requirements document generation

### Within 48 Hours

**Agent Tasks:**

1. requirements-document-agent generates comprehensive document
2. email-composer-agent drafts Email 3 (requirements delivery)
3. orchestrator-agent schedules review period

**Human Tasks:**

1. Review requirements document thoroughly
2. Validate accuracy of workflow diagrams
3. Approve sending to client

### Within 1 Week

**Client Tasks:**

1. Review requirements document
2. Provide corrections or clarifications
3. Approve requirements as accurate

**Agent Tasks:**

1. Incorporate client feedback if needed
2. Finalize requirements document
3. Trigger Phase 3 (prototype development)

---

## Workshop Quality Indicators

### Excellent Workshop

- All six sections completed within 90 minutes
- At least 3 service workflows documented in step-by-step detail
- Complete technology stack with integration points mapped
- 5+ specific AI opportunities identified
- Client actively engaged with detailed responses
- Client validates priorities enthusiastically
- Prototype review meeting scheduled

### Adequate Workshop

- All six sections covered (might run slightly over time)
- 2 service workflows documented
- Most tools captured
- 3-4 AI opportunities identified
- Client engaged but may need follow-up clarification
- Client generally agrees with priorities
- Prototype review meeting scheduled

### Poor Workshop (Requires Follow-Up)

- Sections skipped or rushed
- Only high-level service descriptions (no workflows)
- Incomplete technology stack
- Fewer than 3 AI opportunities
- Client distracted or provides vague answers
- Priorities unclear
- No confirmed next meeting

---

## Common Workshop Challenges and Solutions

**Challenge:** Client provides only surface-level answers

**Solution:**

- Use the "tell me about last time" approach
- "Rather than generally, tell me about the last time you did [TASK]. Walk me through that specific instance."
- Real examples force specificity

**Challenge:** Client jumps between topics and goes off on tangents

**Solution:**

- "That's really interesting and I want to capture it. Let me make a note and we'll come back to it after we finish [CURRENT_SECTION]."
- Keep visible list of "parking lot" topics to return to

**Challenge:** Client says "it depends" for every workflow question

**Solution:**

- "I understand it varies. What are the 2-3 most common scenarios?"
- Capture variations as workflow branches
- Focus on the 80% case, note exceptions

**Challenge:** Client doesn't know technical details of their tools

**Solution:**

- "That's fine—we'll figure out the technical details. Just tell me what you use it for day-to-day."
- Make note to research tools independently
- Focus on use cases rather than technical specs

**Challenge:** Running significantly over time

**Solution:**

- At 60-minute mark: "We have 30 minutes left and still need to cover [X] and [Y]. I may need to schedule a brief 30-minute follow-up call to capture the remaining details. Let's prioritize [MOST_CRITICAL_SECTION] for the rest of today."
- Better to schedule follow-up than rush

**Challenge:** Client fixates on what AI can't do

**Solution:**

- Validate their concern: "You're absolutely right that AI can't [X]. That's exactly why we're not proposing to automate that."
- Redirect: "Your judgment on [X] is irreplaceable. What we're looking at is whether AI can handle the [routine/repetitive/time-consuming] parts so you have more time for [strategic/high-value] work."

**Challenge:** Client provides contradictory information

**Solution:**

- Flag immediately: "Help me understand—earlier you mentioned [A], but just now you said [B]. Can you clarify the difference?"
- Often reveals important nuances about when different processes apply

**Challenge:** Client is clearly overwhelmed by the depth of questions

**Solution:**

- Reassure: "I know this feels very thorough. That thoroughness is what allows me to build something that actually works for how you operate, not a generic tool that creates more work."
- Offer break: "Would a 5-minute break be helpful?"

---

## Success Metrics

A successful requirements workshop results in:

1. ✅ All six sections completed
2. ✅ Minimum 2 services with detailed workflow documentation
3. ✅ Complete technology stack inventory with 80%+ tools captured
4. ✅ At least 5 specific AI opportunities identified
5. ✅ Client validates top 3 priorities
6. ✅ Prototype review meeting confirmed on calendar
7. ✅ Requirements document deliverable within 48 hours
8. ✅ Client satisfaction: "That was valuable time spent"

---

This guide ensures consistent, comprehensive requirements gathering that provides everything needed to build a valuable AI agent prototype.
