# AI Architecture Assistant

A world-class Artificial Intelligence (AI) architect and technical project manager. It architects and plans the development of agentic systems, including requirements analysis, tech stack recommendations, project plan generation, team composition creation, and project cost estimation. It can then package it all up as a project proposal.

**How it works**: Load the assistant's System Prompt as a chat mode or custom agent on your preferred agentic generative AI platform.

**Why it's useful**:
> "Artificial intelligence (AI) initiatives often stall because of poor architectural choices, a lack of preparation and the inability to scale. Enterprise architecture and technology innovation leaders can create an AI architect role to help build a robust enterprise-wide architecture for AI.

> Through 2023, Gartner estimates that 50% of IT leaders will struggle to move their AI projects past the proof of concept (POC) stage into production. To increase the chances of success, organizations can hire an AI architect to help define the architectural strategy, create workflows, identify toolsets and scale artificial intelligence operations."
<https://www.gartner.com/en/articles/what-are-ai-architects-and-what-do-they-do>

---

## Quick Start: Use the Prompt Engineering Assistant in Cursor and GitHub Copilot

1. Open `system.prompt.md`.
2. Copy all contents to your clipboard.
3. In Cursor (Custom Mode - Recommended):
   - Enable Custom Modes: Go to `Cursor Settings` → `Chat` → `Custom Modes`
   - Create a new Custom Mode called "AI Architecture Assistant"
   - Set Tools: Select "All tools enabled" or customize as needed
   - Set Instructions: Paste the entire contents of System Prompt
   - Save the Custom Mode
   - Use the mode picker dropdown in Agent to select your new chat mode
   - Reference: [Cursor Custom Modes Documentation](https://docs.cursor.com/en/agent/modes#custom)
4. In GitHub Copilot (Custom Chat Mode - Recommended):
   - Open Command Palette: Press `⇧⌘P` (macOS) or `Ctrl+Shift+P` (Windows/Linux)
   - Type and select `Chat: New Mode File`
   - Choose `.github/chatmodes` in your project directory for workspace-specific modes
   - Name it `Prompt Engineering Assistant.chatmode.md`
   - Add YAML frontmatter at the top:

     ```yaml
     ---
     description: 'Advanced prompt engineering assistant with recursive improvement capabilities'
     tools: ['codebase', 'search', 'fetch', 'websearch']
     ---
     ```

   - Below the frontmatter, paste the entire contents of the System Prompt
   - Save the file, then select the assistant from the chat mode dropdown
   - Reference: [GitHub Copilot Custom Chat Modes Documentation](https://code.visualstudio.com/docs/copilot/customization/custom-chat-modes)
5. Begin prompt engineering. Keep the system prompt pinned to preserve behavior across the session.

---

## How To Use These Prompts Day-to-Day

1. Load `system.prompt.md` into your chat tool (pin it).
2. Describe your task (e.g., “”).
3. Follow the assistant’s checklist to clarify objectives, constraints, and success metrics.
4. Run the built-in validation. Address findings; iterate as needed.

Expected result: 

---

## AI Development Workflow (How These Prompts Work Together)

The workflow combines specialized AI development tasks, creating a comprehensive toolkit for building AI systems. This workflow integrates specialized prompts for complete AI project development:

- **Requirements Analysis** → **Tech Stack Generation** → **Technical Project Planning** → **Team Composition Generation** → **Project Cost Estimation** → **Project Proposal**

Each stage uses the System Prompt as its foundation, ensuring consistent quality and improvement capabilities across the entire development lifecycle.

---

## Repository Files Overview

### Core Prompts

- `system.prompt.md` — The main system prompt (start here).

### AI Development Pipeline Prompts

Complete workflow for developing an open-source AI-driven MVP software product ready for commercialization. Each prompt guides AI engineers through critical decisions, from the initial concept to a market-ready proposal.

#### End-to-End Development Workflow (Works in Progress)

1. **`workflow/requirements_analysis.user.prompt.md`** — Analyze market needs, define product requirements, and validate AI use cases for your MVP concept
2. **`workflow/tech_stack_generation.user.prompt.md`** — Select optimal AI frameworks, cloud platforms, and development tools aligned with your requirements and team capabilities  
3. **`workflow/technical_project_plan_generation.user.prompt.md`** — Create detailed implementation roadmaps, sprint planning, and risk mitigation strategies for AI product development
4. **`workflow/team_composition_generation.user.prompt.md`** — Determine ideal team structure, skill requirements, and hiring priorities for your AI startup or product team
5. **`workflow/project_cost_estimation.user.prompt.md`** — Calculate development costs, infrastructure expenses, and resource allocation for realistic budgeting and investor presentations
6. **`workflow/project_proposal.user.prompt.md`** — Generate compelling commercial proposals, business models, and go-to-market strategies for your AI product

---

## Troubleshooting

- Can’t find a “System Prompt” field in your tool? Paste the system prompt as your first chat message and pin it.
- The assistant “forgets” behavior mid-session: Re-pin the system prompt or start a fresh chat and paste it again.
- Very long prompts/context: Use the file links and summaries instead of pasting entire codebases; ask the assistant to summarize and extract variables.
- Conflicting instructions: Ask the assistant to run its self-check and highlight conflicts before generating outputs.

---

## Contributing

- Propose improvements via pull request.
- Keep changes aligned with the repository’s validation and structure standards.
- Prefer concise, testable edits with clear success criteria.
