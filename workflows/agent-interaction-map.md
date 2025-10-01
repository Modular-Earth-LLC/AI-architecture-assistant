# Agent Interaction Map

This document describes how all agents in the system interact throughout the complete client engagement workflow.

---

## Agent Hierarchy
orchestrator-agent (Central Coordinator)
│
├── Phase 1: Discovery
│   ├── email-composer-agent
│   ├── discovery-call-agent
│   └── notetaker-agent
│
├── Phase 2: Requirements
│   ├── email-composer-agent
│   ├── requirements-workshop-agent
│   ├── notetaker-agent
│   └── requirements-document-agent
│
├── Phase 3: Development
│   ├── email-composer-agent
│   ├── technical-architect-agent
│   └── prototype-builder-agent
│
├── Phase 4: Review
│   ├── feedback-capture-agent
│   └── notetaker-agent
│
└── Phase 5: Partnership
├── email-composer-agent
└── proposal-generator-agent

---

## Agent Communication Patterns

### Pattern 1: Sequential Handoff

**Scenario:** Requirements workshop → Requirements document
User initiates → orchestrator-agent
↓
requirements-workshop-agent
(facilitates workshop)
↓
notetaker-agent
(captures notes)
↓
requirements-document-agent
(generates document)
↓
email-composer-agent
(drafts delivery email)
↓
Human reviews and approves

---

### Pattern 2: Parallel Execution

**Scenario:** Prototype development
Human architect decides to build prototype
↓
orchestrator-agent initiates
↓
┌───────────┴───────────┐
↓                       ↓
technical-architect-agent   prototype-builder-agent
(designs system)            (generates code)
↓                       ↓
└───────────┬───────────┘
↓
Results combined
↓
Human validates

---

### Pattern 3: Supervisory Monitoring

**Scenario:** Throughout entire engagement
Any phase activity
↓
orchestrator-agent (always monitoring)
↓
Maintains state
Tracks progress
Triggers next actions
Reports to human

---

## Data Flow Between Agents

### Discovery Call → Requirements Workshop
discovery-call-agent outputs:
├── Pain points identified
├── Client business model
├── Technology stack mentioned
├── Budget signals
└── Timeline expectations
↓
requirements-workshop-agent inputs:
├── Uses pain points to focus deep-dive questions
├── Validates business model understanding
├── Expands technology stack inventory
└── Confirms budget and timeline

---

### Requirements Workshop → Prototype Development
requirements-document-agent outputs:
├── Service workflows
├── Technology integrations needed
├── Agent specifications
└── Success criteria
↓
technical-architect-agent inputs:
├── Designs architecture from workflows
├── Plans integrations
├── Defines agent boundaries
└── Sets performance targets
↓
prototype-builder-agent inputs:
├── Generates agent prompts from specs
├── Builds integrations per architecture
├── Implements workflows
└── Creates test scenarios from success criteria

---

### Prototype Review → Proposal
feedback-capture-agent outputs:
├── Feature enthusiasm scores
├── Concerns raised
├── Feature requests
├── Value perception
└── Adoption likelihood
↓
proposal-generator-agent inputs:
├── Emphasizes most-loved features
├── Addresses concerns directly
├── Includes requested features in roadmap
├── Prices based on perceived value
└── Structures options for likelihood tier

---

## Agent Dependencies

### Critical Dependencies (Must Have)

**orchestrator-agent depends on:**
- All other agents (it coordinates everything)
- Must function for system to work

**notetaker-agent depends on:**
- Meeting audio/transcript access
- Used in multiple phases

**email-composer-agent depends on:**
- Context from other agents
- Client information
- Used in all phases

### Optional Dependencies (Enhance Capability)

**requirements-workshop-agent enhances:**
- requirements-document-agent (provides better inputs)
- But requirements-document could work with raw notes

**feedback-capture-agent enhances:**
- proposal-generator-agent (provides better insights)
- But proposal could be generated from basic feedback

---

## State Management

### What the Orchestrator Tracks
```yaml
engagement_state:
  client_id: "UUID"
  client_name: "Company Name"
  current_phase: "discovery | requirements | development | review | partnership"
  phase_status: "not_started | in_progress | complete"
  
  discovery:
    call_completed: true
    pain_points: [list]
    opportunity_score: 45
    next_action: "schedule_workshop"
  
  requirements:
    workshop_completed: false
    document_delivered: false
    next_action: "send_workshop_invitation"
  
  development:
    prototype_started: false
    completion_percentage: 0
    next_action: "pending_requirements_approval"
  
  review:
    demo_completed: false
    feedback_captured: false
    next_action: "pending_prototype_completion"
  
  partnership:
    proposal_sent: false
    decision_received: false
    next_action: "pending_demo_completion"

Error Handling and Fallbacks
Agent Failure Scenarios
If email-composer-agent fails:

Fallback: Use template email
Human: Reviews and customizes manually
Impact: Minimal (just slower)

If requirements-workshop-agent fails:

Fallback: Human facilitates without agent guidance
Use standard question list
Impact: Moderate (may miss some details)

If prototype-builder-agent fails:

Fallback: Human codes entirely manually
No automation assistance
Impact: High (significantly slower development)

If orchestrator-agent fails:

Fallback: Human manages workflow manually
Agents can still function independently
Impact: High (coordination breaks down)


Agent Optimization Opportunities
Current State (Manual Triggers)

Human initiates each phase
Agents provide assistance when requested
Human approves all outputs

Near-Term (Semi-Autonomous)

Orchestrator auto-triggers routine actions
Agents draft communications automatically
Human approves before sending

Future State (Highly Autonomous)

Orchestrator manages full workflow
Agents execute end-to-end with checkpoints
Human oversight at decision points only


This map ensures all agents work together cohesively throughout the engagement lifecycle.
