# Requirements Extraction Prompt

**Copy this prompt into Cursor or Claude when parsing meeting notes and stakeholder discussions into structured requirements.**

**Optimized for:** Internal project planning | Cross-functional team alignment | Executive proposals

---

## Purpose

Extract structured requirements from unstructured meeting notes, emails, Slack conversations, and other documentation to prepare for technical planning and project proposals.

**When to use:**
- After stakeholder discovery sessions or requirements meetings
- When you have scattered notes that need organization
- Before creating project proposals or technical designs
- When preparing for architecture planning sessions

**Workflow position:**
- **Prerequisite:** Load the Solutions Architect System Prompt first
- **After:** Discovery sessions or requirements gathering
- **Before:** Technical architecture design, project proposals, effort estimation

---

## Instructions

You have collected requirements from stakeholders and stored them as rough notes in meeting documentation. Parse the meeting notes and extract the following information into a structured format. For each category below, identify the relevant information from the notes. If information is missing, note it as "[TO BE DETERMINED]" and list it in the "Missing Information" section at the end.

**DO NOT fabricate information.** Only extract what is explicitly stated or clearly implied in the provided documentation.

---

## Extraction Template

### Project Context

**Project Name:** [Descriptive name if mentioned, or suggest based on use case]

**Business Unit/Team:** [Which team or department is requesting this]

**Primary Stakeholder:** [Key decision maker or project sponsor]

**Project Type:** [New feature | System integration | Data pipeline | ML model | Infrastructure | Other]

---

### Use Case & Problem Statement

**Problem Description:**
[What problem are we solving? What pain point exists?]

**Current State:**
[How is this handled today? What are the limitations?]

**Desired Outcome:**
[What does success look like? What changes?]

**Business Impact:**
[How does this benefit the business? Quantify if possible]
- Revenue impact: [Increase/protect revenue, or N/A]
- Cost impact: [Reduce costs, or N/A]
- Efficiency gain: [Time saved, or N/A]
- User experience: [Improvements to internal/external users]
- Strategic value: [Competitive advantage, new capabilities, etc.]

---

### Functional Requirements

**Core Capabilities:**
[List the main functions/features this system needs to provide]
- [Capability 1]
- [Capability 2]
- [Capability 3]

**User Workflows:**
[High-level workflow steps for key use cases]
1. [Step 1]
2. [Step 2]
3. [Step 3]

**Inputs:**
[What data/information goes into the system?]
- Data sources: [Systems, APIs, files, user input]
- Data types: [Structured, unstructured, real-time, batch]
- Data volume: [Scale expectations if mentioned]

**Outputs:**
[What does the system produce?]
- Output format: [Dashboard, API, reports, notifications, etc.]
- Output frequency: [Real-time, scheduled, on-demand]
- Output consumers: [Who/what uses the outputs]

---

### Technical Context

**Existing Systems & Integrations:**
[Systems that need to be integrated with or replaced]
- [System 1]: [Purpose, integration needs]
- [System 2]: [Purpose, integration needs]

**Technology Preferences:**
[Any mentioned preferences for languages, frameworks, cloud platforms]
- Programming languages: [Mentioned preferences]
- Cloud platforms: [AWS, GCP, Azure, or existing infrastructure]
- Tools/frameworks: [Specific tools requested or currently used]

**Data & Infrastructure:**
[Data architecture and infrastructure considerations]
- Data storage: [Database types, data warehouses mentioned]
- Data quality: [Known issues or requirements]
- Infrastructure: [On-prem, cloud, hybrid]
- Security/compliance: [Mentioned requirements]

---

### Performance & Scale Requirements

**Performance Targets:**
[If specific targets were mentioned]
- Response time: [Target latency]
- Throughput: [Requests per second, records per day, etc.]
- Accuracy: [For ML models, if applicable]
- Availability: [Uptime requirements]

**Scale Expectations:**
[Growth and scale considerations]
- Current volume: [Users, transactions, data size]
- Expected growth: [Growth rate or future targets]
- Peak load: [Known spikes or patterns]

---

### Constraints & Considerations

**Budget Constraints:**
[Financial limitations if mentioned]
- Budget range: [If mentioned, otherwise [TO BE DETERMINED]]
- Budget approval process: [Who needs to approve]

**Timeline Constraints:**
[Deadlines and schedule considerations]
- Target launch: [Desired completion date]
- Key milestones: [Important dates or events]
- Dependencies: [Other projects that must complete first]

**Team & Resources:**
[Available resources and capabilities]
- Team size: [Available engineers/data scientists]
- Skill sets: [Team capabilities and gaps]
- Availability: [Percentage of time allocated]

**Compliance & Security:**
[Regulatory or security requirements]
- Compliance standards: [GDPR, SOC2, HIPAA, etc.]
- Data sensitivity: [PII, financial, health data, etc.]
- Access controls: [Authentication, authorization needs]

---

### Success Criteria

**Technical Success Metrics:**
[How will we measure technical success?]
- [Metric 1]: [Target value or threshold]
- [Metric 2]: [Target value or threshold]

**Business Success Metrics:**
[How will we measure business impact?]
- [Metric 1]: [Target value or threshold]
- [Metric 2]: [Target value or threshold]

**User Acceptance Criteria:**
[What needs to be true for stakeholders to accept delivery?]
- [Criterion 1]
- [Criterion 2]

---

### Risks & Open Questions

**Identified Risks:**
[Concerns or risks mentioned in discussions]
- [Risk 1]: [Impact and likelihood if mentioned]
- [Risk 2]: [Impact and likelihood if mentioned]

**Open Questions:**
[Questions that need answers before proceeding]
- [ ] [Question 1]
- [ ] [Question 2]
- [ ] [Question 3]

**Assumptions:**
[Assumptions we're making in absence of complete information]
- [Assumption 1]
- [Assumption 2]

---

### Missing Information

**Critical Information Needed:**
[Information essential for planning that wasn't provided]
- [ ] [Missing item 1]
- [ ] [Missing item 2]

**Recommended Follow-up:**
[Suggested next steps to gather missing information]
1. [Action 1]
2. [Action 2]

---

## Response Format

Present the extracted requirements in clean, well-structured markdown that can be:
- Easily copied and pasted into documentation tools
- Reviewed by stakeholders for accuracy
- Used as input for architecture design
- Referenced during project planning

**Quality guidelines:**
- Be concise and clear in your extractions
- Use bullet points and numbered lists for readability
- Call out gaps explicitly rather than guessing
- Organize information logically by category
- Flag inconsistencies or ambiguities in the source material

---

## Next Steps

After extracting requirements:

1. **Review with stakeholder** - Validate extracted requirements are accurate
2. **Fill gaps** - Schedule follow-ups to gather missing information
3. **Prioritize** - Work with stakeholders to rank requirements by importance
4. **Design architecture** - Use as input for technical design
5. **Estimate effort** - Use for project planning and LOE estimation
6. **Create proposal** - Use for executive approval and budget requests

---

This extraction process ensures all stakeholders have a shared understanding of project requirements before moving into technical planning and implementation.
