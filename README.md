# AI Architecture Assistant

A comprehensive multi-agent system for AI solution architecture and sales process automation.

## Overview

This repository contains a complete framework for Modular Earth's sales and solution architecture process, from initial client prospecting through prototype delivery and partnership negotiation. The system is designed to be executed manually at first, with progressive automation through specialized AI agents.

## Philosophy

Rather than replacing human expertise, this system augments AI solution architects with specialized agents that handle routine tasks, provide real-time guidance, ensure process consistency, and capture critical information. The human architect maintains control at all decision points while agents accelerate execution.

## Repository Structure

AI-architecture-assistant/
├── sales-process/          # Five-phase client engagement process
│   ├── phase-1-initial-engagement/
│   ├── phase-2-requirements-gathering/
│   ├── phase-3-prototype-development/
│   ├── phase-4-prototype-review/
│   └── phase-5-partnership-discussion/
├── templates/              # Reusable document templates
├── agents/                 # AI agent prompts and instructions
└── workflows/              # Process workflows and interaction maps

## The Five-Phase Process

### Phase 1: Initial Engagement

- Discovery call to understand client needs
- Pain point identification
- Opportunity qualification
- **Duration:** 1 week
- **Key Agents:** discovery-call-agent, notetaker-agent

### Phase 2: Requirements Gathering

- 90-minute structured workshop
- Comprehensive business understanding
- AI opportunity mapping
- **Duration:** 1-2 weeks
- **Key Agents:** requirements-workshop-agent, requirements-document-agent

### Phase 3: Prototype Development

- System architecture design
- Working AI agent system build
- Integration development
- **Duration:** 2 weeks
- **Key Agents:** technical-architect-agent, prototype-builder-agent

### Phase 4: Prototype Review

- Live demonstration
- Hands-on client exploration
- Feedback capture
- **Duration:** 1 week
- **Key Agents:** feedback-capture-agent

### Phase 5: Partnership Discussion

- Formal proposal presentation
- Pricing and terms negotiation
- Deal closure or next steps
- **Duration:** 1-2 weeks
- **Key Agents:** proposal-generator-agent, sales-strategist-agent

## AI Agents

This system includes seven specialized agents coordinated by a central orchestrator:

### Core Agents

1. **orchestrator-agent** - Central coordinator managing entire engagement workflow
2. **email-composer-agent** - Drafts all client communications
3. **meeting-facilitator-agent** - Provides real-time guidance during client meetings
4. **notetaker-agent** - Captures and structures meeting insights

### Specialized Agents

5. **requirements-analyst-agent** - Analyzes requirements and identifies AI opportunities
6. **technical-architect-agent** - Designs multi-agent system architectures
7. **sales-strategist-agent** - Provides pricing guidance and negotiation support

See `/agents/` directory for complete agent prompts and instructions.

## Getting Started

### Manual Execution (Current State)

1. Review `/workflows/complete-engagement-workflow.md` for end-to-end process
2. For each client engagement:
   - Start with Phase 1 materials in `/sales-process/phase-1-initial-engagement/`
   - Follow meeting guides and email templates
   - Progress through phases sequentially
3. Customize templates based on client industry and needs

### AI-Augmented Execution (Intermediate State)

1. Deploy agents in Anthropic Claude workspace
2. Use agents as real-time copilots during meetings
3. Have agents draft communications for your review
4. Let agents generate requirements documents and proposals
5. Human reviews and approves all outputs before client delivery

### Autonomous Execution (Future State)

1. Orchestrator-agent manages entire engagement
2. Agents compose and send client communications automatically
3. Meeting facilitator agents lead workshops with human supervision
4. Prototype builder agents develop systems autonomously
5. Human involvement at decision points only

## Key Features

- **Process Consistency:** Ensures every client engagement follows proven methodology
- **Time Savings:** Agents handle routine tasks (email drafting, note-taking, document generation)
- **Quality Assurance:** Built-in checklists and validation at each phase transition
- **Adaptability:** Templates and agents adjust to client industry, sophistication, and complexity
- **Knowledge Capture:** Every engagement generates structured data for continuous improvement

## Usage Guidelines

### For New Client Engagements

1. Create engagement folder: `/engagements/[CLIENT_NAME]-[DATE]/`
2. Copy relevant templates from `/templates/`
3. Follow phase-by-phase process from `/sales-process/`
4. Document learnings and update templates

### For Agent Deployment

1. Read agent prompt file in `/agents/`
2. Deploy to Anthropic Claude workspace with appropriate context
3. Test agent with example scenarios before live client use
4. Review all agent outputs before sending to clients

### For Process Customization

- **Industry Adaptation:** Modify questions and examples in meeting guides
- **Timeline Adjustment:** Compress or extend phases based on client needs
- **Scope Variation:** Focus on subset of agents for smaller engagements

## Dependencies

- Anthropic Claude (Sonnet 4.5 or better) for AI agents
- Video conferencing tool for client meetings
- Note-taking tool compatible with agent access
- Document generation tools (Google Docs, Microsoft Word, etc.)
- Calendar management system

## Roadmap

### Current (Manual)

- ✅ Complete process documentation
- ✅ Email templates
- ✅ Meeting guides
- ✅ Document templates

### Near-Term (AI-Augmented)

- ⏳ Deploy agents in Claude workspace
- ⏳ Real-time meeting facilitation
- ⏳ Automated document generation
- ⏳ Client communication drafting

### Long-Term (Autonomous)

- ⬜ Automated lead research
- ⬜ Self-scheduling calendar integrations
- ⬜ Autonomous email sending with approval
- ⬜ Prototype auto-generation from requirements
- ⬜ Full engagement orchestration

## Contributing

This system is designed for Modular Earth's internal use but follows patterns that can be adapted to other consulting and solution architecture practices.

To contribute:

1. Document learnings from client engagements
2. Refine agent prompts based on actual usage
3. Update templates with improved language
4. Share successful customizations

## License

[Your License]

## Contact

Paul Prae  
<hireme@paulprae.com>  
linkedin.com/in/paulprae  
github.com/praeducer

## Acknowledgments

Built on principles from:

- Service-as-Software (Foundation Capital)
- AI agent orchestration patterns (LangChain, AutoGen)
- Enterprise solution architecture methodologies
- Consulting engagement best practices

---

**Version:** 1.0  
**Last Updated:** October 2025  
**Status:** Production-ready for manual execution, agents in development
