# Email 3: Requirements Document Delivery

**Phase:** Requirements Gathering  
**Timing:** Send within 48 hours of workshop completion  
**Purpose:** Deliver requirements document and confirm accuracy  
**Agent:** email-composer-agent  

---

## Template

**Subject:** [CLIENT_COMPANY_NAME] Requirements Document - Please Review

[CLIENT_FIRST_NAME],

Thank you for the excellent workshop [yesterday/on DATE]. Your detailed insights into how [CLIENT_COMPANY_NAME] operates gave me exactly what I need to build an AI agent system that truly fits your practice.

I've compiled everything we discussed into the attached requirements document. This document will serve as the blueprint for the prototype I'll be building over the next two weeks.

## What's in the Document

The requirements document includes:

1. **Business Profile** - Your market positioning, brand voice, and go-to-market strategy
2. **Service Delivery Analysis** - Detailed workflow diagrams for your [NUMBER] core services
3. **Technology Stack** - Complete inventory of your tools and how they integrate
4. **AI Opportunity Matrix** - The [NUMBER] specific opportunities we identified, prioritized by impact
5. **Proposed Agent Architecture** - The AI agents I recommend building and how they'll work together
6. **Integration Approach** - How the agents will connect with your existing tools
7. **Success Metrics** - How we'll measure whether the agents deliver value

## Please Review Carefully

**Please review this document and let me know if I've misunderstood anything or if there are important details I've missed.** It's much easier to correct the requirements now than to rebuild agents later.

Pay particular attention to:

- **Section 3: Service Delivery Workflows** - Are these step-by-step processes accurate?
- **Section 4: Technology Stack** - Did I capture all your primary tools?
- **Section 6: Proposed Agents** - Do these priorities align with where you'd want to start?

I've also included a preliminary technical architecture showing how the agents would integrate with your existing tools. Don't worry if this section is more technical than you're comfortable with—we'll walk through it together during the prototype review.

## Next Steps

Once you confirm the requirements are accurate (or provide any corrections), I'll begin building the prototype. The development process typically takes two weeks, and I'll keep you updated on progress.

I've tentatively scheduled our prototype review meeting for **[DATE] at [TIME]**. Please confirm this works for your calendar, and I'll send the formal invitation. During that meeting, you'll interact directly with the working agents and see exactly how they handle real scenarios from your business.

If you have questions about anything in the requirements document, we can schedule a brief call to discuss. Otherwise, just reply with any corrections or your confirmation that it looks accurate.

Looking forward to bringing these agents to life for [CLIENT_COMPANY_NAME].

Paul

**Attachment:** [CLIENT_COMPANY_NAME]_AI_Requirements_Document_[DATE].pdf

---

## Required Inputs

- `CLIENT_FIRST_NAME`: Client's first name
- `CLIENT_COMPANY_NAME`: Company or practice name
- `NUMBER` (services): Number of core services documented
- `NUMBER` (opportunities): Number of AI opportunities identified
- `DATE` and `TIME`: Prototype review meeting proposal
- `ATTACHMENT`: Generated requirements document

## Agent Instructions

The email-composer-agent should:

1. Reference specific impressive elements from the workshop
2. Clearly explain what's in the document (don't assume client will read it all)
3. Direct attention to the sections most critical for client validation
4. Set expectation for client action (review and respond)
5. Propose specific prototype review meeting date/time
6. Keep email concise (under 350 words)
7. Maintain balance between thorough and not overwhelming

## Success Criteria

- Client responds within 5 business days
- Client provides feedback (corrections or approval)
- Client confirms prototype review meeting date
- Requirements validated as accurate

## Follow-Up Actions

- If no response in 5 days: orchestrator-agent triggers gentle reminder
- If client requests clarification: Schedule brief call
- If client provides corrections: requirements-document-agent updates document
- If client approves: orchestrator-agent triggers Phase 3 (prototype development)
- If significant gaps identified: May require brief follow-up workshop session
