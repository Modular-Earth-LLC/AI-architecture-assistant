# Email 1: Discovery Call Invitation

**Phase:** Initial Engagement  
**Timing:** Send immediately upon identifying qualified prospect  
**Purpose:** Establish credibility, spark interest, secure discovery call  
**Agent:** email-composer-agent  

---

## Template

**Subject:** AI Agent System for [CLIENT_COMPANY_NAME] - Discovery Call

[CLIENT_FIRST_NAME],

I appreciated learning about [CLIENT_COMPANY_NAME]'s mission to [RESTATE_THEIR_MISSION]. Your background in [KEY_BACKGROUND_ELEMENTS], combined with your [UNIQUE_DIFFERENTIATOR], presents a compelling opportunity for AI augmentation.

I'm Paul Prae, founder of Modular Earth, an open-source AI development company. I specialize in building multi-agent AI systems for [CLIENT_INDUSTRY] professionals like yourself. My background includes over thirteen years designing AI and data solutions for healthcare, life sciences, and financial services at companies including AWS, Microsoft, and Booz Allen Hamilton.

I'm reaching out because I see potential for AI agents to significantly amplify your [consulting practice/operations/service delivery]. Rather than replacing your expertise, these agents would function as specialized interns working under your supervision, each handling constrained tasks within your existing workflows. The key difference from typical AI usage is that these agents augment experts in their craft rather than attempting to replace understanding you don't have.

I'd like to schedule a thirty-minute discovery call to understand your business operations, identify where AI could provide the most value, and determine if we're a good fit to work together. This call is exploratory with no commitment required.

Would you be available for a video call next week? I'm flexible with timing and happy to work around your schedule.

Looking forward to learning more about [CLIENT_COMPANY_NAME].

Paul Prae  
Founder, Modular Earth  
<hireme@paulprae.com>  
<www.paulprae.com>  
LinkedIn: linkedin.com/in/paulprae

---

## Required Inputs

- `CLIENT_FIRST_NAME`: Client's first name
- `CLIENT_COMPANY_NAME`: Company or practice name
- `RESTATE_THEIR_MISSION`: Brief restatement of their stated mission/purpose
- `KEY_BACKGROUND_ELEMENTS`: Relevant professional background (2-3 key points)
- `UNIQUE_DIFFERENTIATOR`: What makes them unique in their field
- `CLIENT_INDUSTRY`: Their primary industry

## Agent Instructions

The email-composer-agent should:

1. Extract required inputs from client research
2. Customize template while maintaining professional tone
3. Ensure message length stays under 300 words
4. Include specific, personalized details (avoid generic language)
5. Validate all hyperlinks and contact information
6. Flag any missing required inputs for human review

## Success Criteria

- Client responds within 5 business days
- Client agrees to discovery call
- Client expresses specific interest in AI augmentation

## Follow-Up Actions

- If no response in 5 days: orchestrator-agent triggers follow-up sequence
- If client declines: sales-strategist-agent analyzes rejection and updates lead scoring
- If client accepts: orchestrator-agent schedules meeting and initiates Phase 1 meeting prep
