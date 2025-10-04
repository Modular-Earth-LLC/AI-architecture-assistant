# Platform Deployment Guide

**Purpose:** Step-by-step instructions for deploying AI Architecture Assistant agents to different platforms  
**Platforms:** Cursor | Claude Projects | AWS Bedrock | Self-Hosted

---

## Deployment Overview

The AI Architecture Assistant supports multiple deployment patterns:

1. **Cursor Custom Chat Modes** - Local development, file context aware
2. **Claude Projects** - Deep reasoning, large context window
3. **AWS Bedrock Multi-Agent** - Enterprise production deployment
4. **Self-Hosted** (Ollama + Open WebUI) - Maximum privacy

---

## Option 1: Cursor Custom Chat Modes (Recommended for Development)

### Method A: Deploy Supervisor Agent Only

**Best for:** Integrated experience, automatic agent switching

**Setup (5 minutes):**

1. Open Cursor → Settings (Ctrl/Cmd + ,)
2. Search for "Custom Chat"
3. Click "Add Custom Chat Mode"
4. **Name:** "AI Architecture Assistant"
5. **Copy** contents of `supervisor_agent.system.prompt.md`
6. **Paste** into Custom Instructions field
7. Click "Save"

**Usage:**
```
You: "I want to build an AI system for financial operations"
Supervisor: [Routes you to Requirements Agent, guides through workflow]
```

**Pros:** Seamless agent switching, guided workflow  
**Cons:** Single chat mode, may hit context limits on very long sessions

---

### Method B: Deploy Each Specialized Agent Separately

**Best for:** Direct access to specific agents, no supervisor overhead

**Setup (25 minutes):**

Create 5 separate custom chat modes:

1. **Requirements Agent**
   - Name: "Requirements Discovery"
   - Prompt: `ai_agents/requirements_agent.system.prompt.md`

2. **Architecture Agent**
   - Name: "AI Architecture Design"
   - Prompt: `ai_agents/architecture_agent.system.prompt.md`

3. **Engineering Agent**
   - Name: "Prototype Builder"
   - Prompt: `ai_agents/engineering_agent.system.prompt.md`

4. **Deployment Agent**
   - Name: "System Deployment"
   - Prompt: `ai_agents/deployment_agent.system.prompt.md`

5. **Optimization Agent**
   - Name: "System Optimizer"
   - Prompt: `ai_agents/optimization_agent.system.prompt.md`

**Usage:**
```
Manually switch between chat modes based on workflow phase:
- Starting project → Requirements Discovery
- Have requirements → AI Architecture Design
- Have architecture → Prototype Builder
- Have prototype → System Deployment
- Want improvements → System Optimizer
```

**Pros:** Direct agent access, clear separation  
**Cons:** Manual switching, user maintains context

---

### Knowledge Base Access in Cursor

**Cursor automatically accesses files in your workspace:**

```
knowledge_base/system_config.json       # Agents read this
knowledge_base/user_requirements.json   # Requirements Agent writes, others read
knowledge_base/design_decisions.json    # Architecture Agent writes, others read
```

**No special configuration needed** - Cursor's file context handles this automatically.

---

## Option 2: Claude Projects

### Setup (10 minutes)

**For Supervisor Agent:**

1. Go to https://claude.ai
2. Click "Projects" → "Create Project"
3. **Name:** "AI Architecture Assistant"
4. **Custom Instructions:** Copy `supervisor_agent.system.prompt.md`
5. **Project Knowledge:** Upload entire `knowledge_base/` folder
6. Click "Create"

**For Specialized Agents** (if deploying separately):

Create 5 projects, one for each specialized agent, following same process.

---

### Knowledge Base in Claude Projects

**Upload to Project Knowledge:**
```
knowledge_base/system_config.json
knowledge_base/user_requirements.json
knowledge_base/design_decisions.json
docs/agent_design_patterns.md
```

**Claude will:**
- Search project knowledge when needed
- Reference schema structures
- Maintain context across conversations

---

### Usage

```
You: "Help me design a financial operations AI system"
Supervisor: [Guides you through requirements → architecture → engineering]

[After requirements complete]
Supervisor: "Requirements saved to user_requirements.json in project knowledge."

[After architecture complete]
Supervisor: "Architecture saved to design_decisions.json. Ready for proposal assembly?"
```

**Pros:** Large context window (200K tokens), excellent reasoning  
**Cons:** Requires Claude Pro subscription, knowledge base upload

---

## Option 3: AWS Bedrock Multi-Agent (Enterprise Production)

### Architecture

```
Bedrock Orchestrator Agent (Supervisor)
    ├─ Bedrock Sub-Agent: Requirements
    ├─ Bedrock Sub-Agent: Architecture
    ├─ Bedrock Sub-Agent: Engineering
    ├─ Bedrock Sub-Agent: Deployment
    └─ Bedrock Sub-Agent: Optimization

Bedrock Knowledge Base (for knowledge_base/*.json)
Bedrock Prompt Management (for user_prompts/*.md)
```

### Setup (2-4 hours with AWS experience)

**Prerequisites:**
- AWS Account with Bedrock access
- IAM permissions for Bedrock, S3, Lambda
- AWS CLI configured

**Step 1: Create Bedrock Knowledge Base**

```bash
# Create S3 bucket for knowledge base
aws s3 mb s3://ai-architecture-kb-[your-suffix]

# Upload knowledge base files
aws s3 cp knowledge_base/ s3://ai-architecture-kb-[your-suffix]/knowledge_base/ --recursive

# Create Bedrock Knowledge Base
aws bedrock-agent create-knowledge-base \
  --name "AI-Architecture-Knowledge-Base" \
  --role-arn [YOUR_IAM_ROLE_ARN] \
  --storage-configuration s3Configuration={bucketArn=arn:aws:s3:::ai-architecture-kb-[your-suffix]}
```

**Step 2: Create Bedrock Agents**

```bash
# Create Supervisor Agent
aws bedrock-agent create-agent \
  --agent-name "AI-Architecture-Supervisor" \
  --foundation-model "anthropic.claude-3-sonnet-20240229-v1:0" \
  --instruction file://supervisor_agent.system.prompt.md \
  --knowledge-bases knowledgeBaseId=[KB_ID]

# Create Sub-Agents (repeat for each specialized agent)
aws bedrock-agent create-agent \
  --agent-name "Requirements-Agent" \
  --foundation-model "anthropic.claude-3-sonnet-20240229-v1:0" \
  --instruction file://ai_agents/requirements_agent.system.prompt.md \
  --knowledge-bases knowledgeBaseId=[KB_ID]

[Repeat for Architecture, Engineering, Deployment, Optimization agents]
```

**Step 3: Upload User Prompts to Prompt Management**

```bash
# Upload each user prompt
aws bedrock-agent create-prompt \
  --name "quick-discovery" \
  --variants file://user_prompts/requirements/quick_discovery.user.prompt.md

[Repeat for all 15 user prompts]
```

**Step 4: Configure Agent Collaboration**

```bash
# Link supervisor to sub-agents
aws bedrock-agent update-agent \
  --agent-id [SUPERVISOR_AGENT_ID] \
  --sub-agents [
{
      "agentId": "[REQUIREMENTS_AGENT_ID]"
    },
    {
      "agentId": "[ARCHITECTURE_AGENT_ID]"
    },
    {
      "agentId": "[ENGINEERING_AGENT_ID]"
    },
    {
      "agentId": "[DEPLOYMENT_AGENT_ID]"
    },
    {
      "agentId": "[OPTIMIZATION_AGENT_ID]"
    }
  ]
```

**Reference:** [AWS Multi-Agent Orchestration Guide](https://aws.amazon.com/solutions/guidance/multi-agent-orchestration-on-aws/)

---

### Production Deployment Considerations

**Monitoring:**
- CloudWatch Logs for agent interactions
- X-Ray tracing for performance
- Custom metrics for usage tracking

**Security:**
- IAM roles with least privilege
- VPC endpoints for private access
- Encryption at rest and in transit
- Knowledge base access controls

**Cost Management:**
- Set usage quotas
- Monitor token consumption
- Alert on cost thresholds

---

## Option 4: Self-Hosted (Ollama + Open WebUI)

### Setup (30 minutes)

**Prerequisites:**
- Docker Desktop installed
- 16GB+ RAM recommended
- 50GB+ disk space

**Step 1: Install Ollama**

```bash
# macOS/Linux
curl https://ollama.ai/install.sh | sh

# Windows: Download from https://ollama.ai

# Download model (choose size based on your hardware)
ollama pull llama3.1:8b     # 8GB RAM minimum
ollama pull llama3.1:70b    # 32GB+ RAM for better quality
```

**Step 2: Install Open WebUI**

```bash
docker run -d -p 3000:8080 \
  --add-host=host.docker.internal:host-gateway \
  -v open-webui:/app/backend/data \
  --name open-webui \
  ghcr.io/open-webui/open-webui:main
```

**Step 3: Create Custom Models in Open WebUI**

1. Open http://localhost:3000
2. Click Settings → Models → "+" (Add Model)
3. **Name:** "AI Architecture Supervisor"
4. **Base Model:** llama3.1:8b (or 70b)
5. **System Prompt:** Paste `supervisor_agent.system.prompt.md`
6. Click "Save"

**Repeat for each specialized agent** (5 more custom models)

**Step 4: Upload Knowledge Base**

1. In Open WebUI → Settings → Documents
2. Upload all files from `knowledge_base/`
3. Agents can reference these in conversations

---

### Usage

```
Select "AI Architecture Supervisor" model
You: "Help me build a financial operations assistant"
[Workflow proceeds locally, completely private]
```

**Pros:** Maximum privacy, no data leaves your computer, no API costs  
**Cons:** Requires powerful hardware, open-source models less capable than Claude/GPT-4

---

## Comparison Matrix

| Feature | Cursor | Claude Projects | AWS Bedrock | Self-Hosted |
|---------|--------|----------------|-------------|-------------|
| **Setup Time** | 5 min | 10 min | 2-4 hrs | 30 min |
| **Cost** | Cursor subscription | Claude Pro ($20/mo) | Pay per use | Free (hardware) |
| **Privacy** | Local files | Cloud (Anthropic) | Cloud (AWS) | Fully local |
| **Context Size** | Large | 200K tokens | Large | Model dependent |
| **Multi-Agent** | Manual/Supervisor | Manual | Native support | Manual |
| **File Access** | Excellent | Via upload | Via S3/KB | Via upload |
| **Best For** | Development | Design/Analysis | Production | Privacy-critical |

---

## Recommended Setup

**For Learning/Development:**
→ **Cursor** (Method A: Supervisor Agent only)

**For Deep Analysis/Design:**
→ **Claude Projects** (Best reasoning quality)

**For Enterprise Production:**
→ **AWS Bedrock** (Scalable, secure, monitored)

**For Maximum Privacy:**
→ **Self-Hosted** (No data leaves your infrastructure)

---

**Version:** 1.0  
**Last Updated:** 2025-10-03  
**Platforms:** Cursor, Claude Projects, AWS Bedrock, Self-Hosted Ollama
