# Complete Engagement Workflow

This document describes the end-to-end workflow for acquiring and serving clients, including all agent interactions and decision points.

---

## Workflow Overview

PROSPECTING → DISCOVERY → REQUIREMENTS → DEVELOPMENT → REVIEW → PARTNERSHIP
↓            ↓            ↓              ↓            ↓           ↓
Research    30-min call   90-min workshop  2-week build  60-min demo  Proposal

---

## Detailed Workflow

### Stage 0: Lead Identification & Research

**Human Actions:**

- Identify potential client (LinkedIn, referral, inbound)
- Initial qualification (industry fit, company size, AI readiness)

**Agent Actions:**

- **Research Assistant** (future): Automatically gather public information
  - LinkedIn profile analysis
  - Company website analysis
  - Industry research
  - Pain point prediction based on industry/role

**Output:** Lead qualification brief

**Decision Point:** Proceed with outreach? (Human decides)

---

### Stage 1: Initial Outreach (Phase 1 Start)

**Trigger:** Human decides to pursue lead

**Agent Actions:**

1. **orchestrator-agent** initiates Phase 1 sequence
2. **email-composer-agent** generates Email 1 (discovery invitation)
   - Inputs: Client research, company info, industry
   - Output: Personalized email draft

**Human Actions:**

- Review and approve email
- Send email

**Success Criteria:** Client responds and agrees to discovery call

**Timeline:** Wait up to 5 days for response

**If No Response:**

- **orchestrator-agent** triggers follow-up sequence
- **sales-strategist-agent** recommends follow-up approach
- Human approves follow-up action

---

### Stage 2: Discovery Call (Phase 1)

**Pre-Meeting:**

**Agent Actions:**

1. **orchestrator-agent** schedules meeting, deploys agents
2. **discovery-call-agent** prepares:
   - Client research summary
   - Industry-specific questions
   - Relevant AI examples
   - Meeting agenda

**Human Actions:**

- Review agent-prepared materials
- Set up video call

**During Meeting:**

**Agent Actions:**

1. **discovery-call-agent** provides real-time guidance:
   - Display agenda and time tracking
   - Suggest follow-up questions
   - Classify pain points as they emerge
   - Assess opportunity strength

2. **notetaker-agent** captures:
   - All pain points mentioned
   - Client's tool stack
   - Budget signals
   - Urgency indicators
   - Exact client language

**Human Actions:**

- Lead conversation
- Follow agent guidance when helpful
- Make judgment calls on conversation flow

**Post-Meeting:**

**Agent Actions:**

1. **notetaker-agent** generates meeting summary (30 minutes)
2. **discovery-call-agent** provides opportunity assessment
3. **orchestrator-agent** determines next action:
   - Strong opportunity → Proceed to Phase 2
   - Moderate opportunity → Schedule follow-up
   - Weak opportunity → Archive lead

**Human Actions:**

- Review meeting summary
- Approve next steps
- Send meeting summary to client (agent-drafted)

**Decision Point:** Proceed to requirements workshop? (Human decides based on agent recommendation)

---

### Stage 3: Requirements Workshop Invitation (Phase 2 Start)

**Trigger:** Human approves proceeding to Phase 2

**Agent Actions:**

1. **orchestrator-agent** initiates Phase 2 sequence
2. **email-composer-agent** generates Email 2 (workshop invitation)
   - Inputs: Discovery call notes, identified pain points
   - Output: Personalized workshop invitation

**Human Actions:**

- Review and approve email
- Send email
- Schedule 90-minute workshop

**Success Criteria:** Client confirms workshop attendance

---

### Stage 4: Requirements Workshop (Phase 2)

**Pre-Workshop:**

**Agent Actions:**

1. **requirements-workshop-agent** prepares:
   - Customized question set based on discovery call
   - Requirement capture framework
   - Time-allocated agenda

**Human Actions:**

- Review agent-prepared materials
- Set up screen sharing and collaborative note-taking

**During Workshop:**

**Agent Actions:**

1. **requirements-workshop-agent** provides real-time guidance:
   - Track section progress and timing
   - Suggest probing questions based on responses
   - Flag gaps or ambiguities
   - Identify AI opportunities in real-time
   - Adapt question depth to client sophistication

2. **notetaker-agent** captures:
   - Complete workflow descriptions
   - Technology stack details
   - Brand voice examples
   - Pain point verbatim descriptions

**Human Actions:**

- Facilitate workshop through all six sections
- Follow agent guidance for coverage completeness
- Make judgment calls on depth vs breadth

**Post-Workshop:**

**Agent Actions:**

1. **notetaker-agent** provides structured notes (30 minutes)
2. **requirements-document-agent** generates comprehensive requirements doc (48 hours)
   - Inputs: Workshop notes, discovery notes
   - Output: 15-25 page requirements document with:
     - Business profile
     - Service workflow diagrams
     - Technology stack
     - AI opportunity analysis
     - Proposed agent architecture

3. **email-composer-agent** drafts Email 3 (requirements delivery)

4. **orchestrator-agent** schedules:
   - Requirements review period (3-5 days)
   - Prototype review meeting (3 weeks out)

**Human Actions:**

- Review requirements document for accuracy
- Approve requirements document
- Send to client for validation

**Success Criteria:** Client confirms requirements document accuracy

**Decision Point:** Are requirements sufficient to build prototype? (Human decides)

---

### Stage 5: Prototype Development (Phase 3)

**Trigger:** Client approves requirements document

**Agent Actions:**

1. **orchestrator-agent** initiates Phase 3 sequence
2. **technical-architect-agent** designs system:
   - Multi-agent architecture
   - Integration approach
   - Technology stack selection
   - Deployment strategy

3. **prototype-builder-agent** develops:
   - Individual agent prompts
   - Agent coordination logic
   - Integration hooks
   - User interface
   - Demo scenarios

4. **orchestrator-agent** at 1-week mark:
   - Deploy **email-composer-agent** for Email 4 (progress update)
   - Send brief update to maintain client engagement

**Human Actions:**

- Review system architecture
- Approve technical approach
- Code and test prototype (augmented by coding agents)
- Review progress update email before sending

**Duration:** 2 weeks

**Output:** Working prototype with 3-5 specialized agents

---

### Stage 6: Prototype Review (Phase 4)

**Pre-Meeting:**

**Agent Actions:**

1. **orchestrator-agent** prepares demo environment
2. **Demo Assistant Agent** (future): Prepares scenarios
3. **orchestrator-agent** sends meeting reminder

**Human Actions:**

- Test prototype thoroughly
- Prepare demonstration plan
- Set up screen sharing

**During Meeting:**

**Agent Actions:**

1. **feedback-capture-agent** captures:
   - Client reactions to each agent
   - Feature requests
   - Concerns or hesitations
   - Usability observations

2. **Meeting-facilitator-agent** tracks:
   - Demo coverage completeness
   - Time management
   - Question patterns

**Human Actions:**

- Demonstrate prototype functionality
- Guide client through hands-on exploration
- Answer questions
- Discuss path to production

**Post-Meeting:**

**Agent Actions:**

1. **feedback-capture-agent** generates feedback summary
2. **sales-strategist-agent** assesses:
   - Client enthusiasm level
   - Concerns to address in proposal
   - Pricing strategy

3. **proposal-generator-agent** creates formal proposal:
   - Custom production system option
   - Partnership/Service-as-Software option
   - Scope, timeline, investment

4. **email-composer-agent** drafts Email 5 (proposal delivery)

**Human Actions:**

- Review feedback summary
- Approve proposal
- Send proposal

**Decision Point:** Did client respond positively to prototype? (Human assesses)

---

### Stage 7: Partnership Discussion (Phase 5)

**Trigger:** Client requests proposal or expresses interest in proceeding

**Agent Actions:**

1. **orchestrator-agent** initiates Phase 5 sequence
2. **sales-strategist-agent** provides:
   - Pricing recommendations
   - Partnership structure options
   - Negotiation guidance

**Human Actions:**

- Discuss proposal with client
- Negotiate terms
- Address concerns
- Close deal or determine next steps

**Outcomes:**

- **Deal Closed:** Begin production development
- **Client Needs Time:** Schedule follow-up
- **Client Declines:** Capture feedback, archive engagement

---

## Agent Interaction Map

orchestrator-agent (central coordinator)
│
├── Phase 1: Discovery
│   ├── email-composer-agent → Email 1
│   ├── discovery-call-agent → Meeting guidance
│   └── notetaker-agent → Capture insights
│
├── Phase 2: Requirements
│   ├── email-composer-agent → Email 2, Email 3
│   ├── requirements-workshop-agent → Workshop guidance
│   ├── notetaker-agent → Capture requirements
│   └── requirements-document-agent → Generate doc
│
├── Phase 3: Development
│   ├── email-composer-agent → Email 4
│   ├── technical-architect-agent → System design
│   └── prototype-builder-agent → Build agents
│
├── Phase 4: Review
│   ├── feedback-capture-agent → Capture reactions
│   └── sales-strategist-agent → Assess opportunity
│
└── Phase 5: Partnership
├── email-composer-agent → Email 5
├── proposal-generator-agent → Create proposal
└── sales-strategist-agent → Pricing & terms
Cross-Cutting Agents:

- notetaker-agent: Used in all meetings
- sales-strategist-agent: Consulted at key decision points
- email-composer-agent: All client communications

---

## Success Metrics

**Phase 1:**

- Discovery call completion rate: >80%
- Conversion to workshop: >60%

**Phase 2:**

- Workshop completion rate: >95%
- Requirements doc accuracy: Client approves with <3 revisions

**Phase 3:**

- Prototype delivery on time: >85%
- Prototype demonstrates all proposed agents: 100%

**Phase 4:**

- Client can use prototype independently: >75%
- Positive feedback on value: >80%

**Phase 5:**

- Proposal presented: 100%
- Deal closure rate: >40%

**Overall:**

- Time from discovery to proposal: <5 weeks
- Client satisfaction: >4.5/5

---

## Timeline Summary

- **Discovery Call to Workshop:** 1 week
- **Workshop to Requirements Doc:** 3-5 days
- **Requirements to Prototype:** 2 weeks
- **Prototype to Review Meeting:** 0-3 days
- **Review to Proposal:** 2-3 days
- **Total: Discovery to Proposal:** 4-5 weeks

---

This workflow is designed to be executed manually at first, with increasing agent automation over time. The human maintains control at all decision points while agents handle routine tasks, provide guidance, and ensure consistency.
