# Prototype Development Guide

**Purpose:** Build a working AI agent system from approved requirements and architecture  
**Duration:** 2-4 weeks depending on complexity  
**Output:** Functional prototype ready for stakeholder testing

---

## Overview

The prototype phase is where you transform architecture designs into working code. Your goal is to build a functional system that demonstrates value, not a production-ready product.

**Key principles:**
- **Function over polish** - Working beats beautiful
- **Value demonstration** - Prove the concept works
- **Iterative refinement** - Build, test, improve
- **Pragmatic shortcuts** - Simulated data is OK for prototypes

---

## Development Approach

### Prototype vs. Production

**Prototype priorities:**
- ✅ Demonstrates core functionality
- ✅ Proves technical feasibility
- ✅ Shows clear value to stakeholder
- ✅ Simple, understandable code
- ✅ Works reliably for demo scenarios

**Production priorities (not for prototype):**
- ❌ Perfect error handling
- ❌ Full security hardening
- ❌ Comprehensive test coverage
- ❌ Optimized performance
- ❌ Beautiful UI design

### Agile Build Approach

**Week 1: Foundation**
1. Set up development environment
2. Build highest-priority agent
3. Create simple UI
4. Test core functionality

**Week 2+: Expansion**
5. Add additional agents
6. Implement agent coordination
7. Build/simulate integrations
8. Create demo scenarios
9. Polish and test

---

## Step-by-Step Process

### Step 1: Environment Setup (Day 1)

#### Development Environment

```bash
# Example Python setup
mkdir ai-agent-prototype
cd ai-agent-prototype

# Create virtual environment
python -m venv venv
source venv/bin/activate  # or `venv\Scripts\activate` on Windows

# Install dependencies
pip install anthropic fastapi uvicorn streamlit python-dotenv

# Create project structure
mkdir -p agents integrations ui tests
touch .env README.md
```

#### Project Structure

```
ai-agent-prototype/
├── .env                 # API keys and secrets
├── .gitignore          # Don't commit secrets!
├── requirements.txt    # Python dependencies
├── README.md           # Setup instructions
├── agents/             # Agent implementations
│   ├── agent_1.py
│   ├── agent_2.py
│   └── orchestrator.py
├── integrations/       # External system integrations
│   ├── tool_1.py
│   └── tool_2.py
├── ui/                 # User interface
│   ├── app.py
│   └── components/
└── tests/             # Test scenarios
    └── demo_scenarios.py
```

#### Configuration

```python
# .env file
ANTHROPIC_API_KEY=your_key_here
TOOL_API_KEY=your_tool_key_here
ENVIRONMENT=development
```

**⚠️ Important:** Add `.env` to `.gitignore`!

---

### Step 2: Build First Agent (Days 2-3)

#### Agent Template

```python
# agents/agent_1.py
import anthropic
import os

class Agent1:
    def __init__(self):
        self.stakeholder = anthropic.Anthropic(
            api_key=os.environ.get("ANTHROPIC_API_KEY")
        )
        self.system_prompt = """
        You are a [SPECIALIST_TYPE] agent.
        
        Your purpose: [SPECIFIC_PURPOSE]
        
        Instructions:
        1. [STEP_1]
        2. [STEP_2]
        3. [STEP_3]
        
        Output format:
        [SPECIFIC_FORMAT]
        
        Constraints:
        - [CONSTRAINT_1]
        - [CONSTRAINT_2]
        """
    
    def process(self, user_input: str) -> str:
        """Process user input and return agent response"""
        
        message = self.stakeholder.messages.create(
            model="claude-sonnet-4-20250514",
            max_tokens=1024,
            temperature=0,  # For consistency
            system=self.system_prompt,
            messages=[
                {"role": "user", "content": user_input}
            ]
        )
        
        return message.content[0].text
```

#### Test Your Agent

```python
# tests/test_agent_1.py
from agents.agent_1 import Agent1

def test_agent_1():
    agent = Agent1()
    
    # Test case 1: Normal input
    result = agent.process("Test input here")
    print(f"Result: {result}")
    assert len(result) > 0
    
    # Test case 2: Edge case
    result = agent.process("Edge case input")
    print(f"Edge case result: {result}")
    
    print("✅ Agent 1 tests passed")

if __name__ == "__main__":
    test_agent_1()
```

#### Refine the Prompt

**Iterate on the system prompt until:**
- Agent produces consistent outputs
- Format matches requirements
- Tone matches stakeholder brand voice
- Handles edge cases gracefully

**Common refinements:**
- Add more specific examples
- Tighten output format constraints
- Add error handling instructions
- Specify what to do when uncertain

---

### Step 3: Build Simple Orchestrator (Days 3-4)

#### Simple Router Pattern

```python
# agents/orchestrator.py
from agents.agent_1 import Agent1
from agents.agent_2 import Agent2

class SimpleOrchestrator:
    def __init__(self):
        self.agents = {
            'agent_1': Agent1(),
            'agent_2': Agent2(),
        }
    
    def route(self, user_input: str) -> str:
        """Route input to appropriate agent"""
        
        # Simple keyword routing
        if 'keyword1' in user_input.lower():
            return self.agents['agent_1'].process(user_input)
        elif 'keyword2' in user_input.lower():
            return self.agents['agent_2'].process(user_input)
        else:
            return "I can help with [task1] or [task2]. What would you like?"
```

#### Intent-Based Router (More Sophisticated)

```python
# agents/orchestrator.py
import anthropic
import os

class IntentOrchestrator:
    def __init__(self):
        self.stakeholder = anthropic.Anthropic(
            api_key=os.environ.get("ANTHROPIC_API_KEY")
        )
        self.agents = {
            'agent_1': Agent1(),
            'agent_2': Agent2(),
        }
    
    def classify_intent(self, user_input: str) -> str:
        """Use LLM to determine which agent should handle this"""
        
        message = self.stakeholder.messages.create(
            model="claude-sonnet-4-20250514",
            max_tokens=100,
            temperature=0,
            system="""You are an intent classifier.
            
            Available agents:
            - agent_1: Handles [DESCRIPTION]
            - agent_2: Handles [DESCRIPTION]
            
            Respond with only the agent name that should handle the request.""",
            messages=[
                {"role": "user", "content": user_input}
            ]
        )
        
        return message.content[0].text.strip()
    
    def route(self, user_input: str) -> str:
        """Route to appropriate agent based on intent"""
        
        intent = self.classify_intent(user_input)
        
        if intent in self.agents:
            return self.agents[intent].process(user_input)
        else:
            return f"I'm not sure how to help with that. I can assist with [capabilities]."
```

---

### Step 4: Build User Interface (Days 4-5)

#### Streamlit UI (Fastest)

```python
# ui/app.py
import streamlit as st
from agents.orchestrator import SimpleOrchestrator

st.set_page_config(page_title="AI Agent Demo", layout="wide")

# Initialize orchestrator
if 'orchestrator' not in st.session_state:
    st.session_state.orchestrator = SimpleOrchestrator()

# UI
st.title("🤖 AI Agent System Demo")
st.markdown("This system helps you [MAIN_PURPOSE]")

# Chat interface
user_input = st.text_input("What would you like help with?")

if st.button("Send") and user_input:
    with st.spinner("Processing..."):
        response = st.session_state.orchestrator.route(user_input)
        st.success("Response:")
        st.write(response)

# Sidebar with demo scenarios
with st.sidebar:
    st.header("Demo Scenarios")
    if st.button("Scenario 1: [Description]"):
        st.session_state.demo_input = "[Scenario 1 input]"
    if st.button("Scenario 2: [Description]"):
        st.session_state.demo_input = "[Scenario 2 input]"
```

#### Run the UI

```bash
streamlit run ui/app.py
```

---

### Step 5: Build Integrations (Days 5-7)

#### API Integration Example

```python
# integrations/tool_1.py
import requests
import os

class Tool1Integration:
    def __init__(self):
        self.api_key = os.environ.get("TOOL_API_KEY")
        self.base_url = "https://api.tool.com/v1"
    
    def get_data(self, query: str) -> dict:
        """Fetch data from external tool"""
        
        headers = {
            "Authorization": f"Bearer {self.api_key}",
            "Content-Type": "application/json"
        }
        
        response = requests.get(
            f"{self.base_url}/data",
            headers=headers,
            params={"query": query}
        )
        
        if response.status_code == 200:
            return response.json()
        else:
            # For prototype: return simulated data on error
            return self._get_simulated_data(query)
    
    def _get_simulated_data(self, query: str) -> dict:
        """Simulated data for testing when API unavailable"""
        return {
            "query": query,
            "results": [
                {"id": 1, "value": "Sample result 1"},
                {"id": 2, "value": "Sample result 2"}
            ],
            "note": "This is simulated data for demonstration"
        }
```

#### Use Integration in Agent

```python
# agents/agent_1.py
from integrations.tool_1 import Tool1Integration

class Agent1:
    def __init__(self):
        self.stakeholder = anthropic.Anthropic(...)
        self.tool = Tool1Integration()
    
    def process(self, user_input: str) -> str:
        # Get data from external tool
        data = self.tool.get_data(user_input)
        
        # Use data in LLM prompt
        enhanced_prompt = f"""
        User request: {user_input}
        
        Relevant data from system:
        {data}
        
        Provide a helpful response based on this data.
        """
        
        message = self.stakeholder.messages.create(...)
        return message.content[0].text
```

---

### Step 6: Create Demo Scenarios (Days 7-8)

#### Demo Scenario Template

```python
# tests/demo_scenarios.py

DEMO_SCENARIOS = [
    {
        "name": "Scenario 1: [Description]",
        "input": "[Specific input that demonstrates agent capability]",
        "expected_behavior": "Agent should [expected outcome]",
        "demonstrates": "Core capability of [agent name]"
    },
    {
        "name": "Scenario 2: [Description]",
        "input": "[Input showing agent coordination]",
        "expected_behavior": "Agent 1 should hand off to Agent 2",
        "demonstrates": "Multi-agent coordination"
    },
    {
        "name": "Scenario 3: [Description]",
        "input": "[Input requiring external tool]",
        "expected_behavior": "Agent should fetch data and synthesize response",
        "demonstrates": "Tool integration"
    },
    # Add 5+ scenarios
]

def run_demo_scenario(orchestrator, scenario):
    """Run a single demo scenario"""
    print(f"\n{'='*60}")
    print(f"Scenario: {scenario['name']}")
    print(f"Input: {scenario['input']}")
    print(f"{'='*60}")
    
    result = orchestrator.route(scenario['input'])
    
    print(f"\nAgent Response:")
    print(result)
    print(f"\nDemonstrates: {scenario['demonstrates']}")
    print(f"{'='*60}\n")
    
    return result
```

---

### Step 7: Testing & Refinement (Days 9-12)

#### Create Test Suite

```python
# tests/test_all.py
from agents.orchestrator import IntentOrchestrator
from tests.demo_scenarios import DEMO_SCENARIOS, run_demo_scenario

def test_all_scenarios():
    """Run all demo scenarios"""
    orchestrator = IntentOrchestrator()
    
    results = []
    for scenario in DEMO_SCENARIOS:
        result = run_demo_scenario(orchestrator, scenario)
        results.append({
            'scenario': scenario['name'],
            'passed': len(result) > 0,  # Basic check
            'result': result
        })
    
    # Summary
    passed = sum(1 for r in results if r['passed'])
    print(f"\n✅ {passed}/{len(results)} scenarios passed")
    
    return results

if __name__ == "__main__":
    test_all_scenarios()
```

#### Iterate and Refine

**For each failed or suboptimal result:**
1. Identify the issue (prompt, logic, data)
2. Make targeted fix
3. Retest
4. Document the change

---

## Integration Strategies

### Strategy 1: Real API (Preferred)

```python
# When API is available and reliable
def get_data(self, query: str) -> dict:
    response = requests.get(api_url, params={"q": query})
    return response.json()
```

### Strategy 2: Simulated Data (Acceptable for Prototype)

```python
# When API unavailable or unreliable
def get_data(self, query: str) -> dict:
    # Return realistic sample data
    return {
        "results": [...],
        "note": "Simulated for demonstration"
    }
```

### Strategy 3: Hybrid Approach (Best for Demos)

```python
# Try real API, fallback to simulation
def get_data(self, query: str) -> dict:
    try:
        response = requests.get(api_url, params={"q": query})
        if response.status_code == 200:
            return response.json()
    except Exception as e:
        print(f"API error: {e}, using simulated data")
    
    return self._simulated_data(query)
```

---

## Common Development Patterns

### Pattern 1: Agent with Tool Access

```python
class ResearchAgent:
    def __init__(self):
        self.llm = anthropic.Anthropic(...)
        self.search_tool = SearchIntegration()
    
    def process(self, query: str) -> str:
        # Step 1: Get information
        search_results = self.search_tool.search(query)
        
        # Step 2: Synthesize with LLM
        prompt = f"""
        User question: {query}
        
        Search results:
        {search_results}
        
        Provide a comprehensive answer based on the search results.
        """
        
        return self.llm.generate(prompt)
```

### Pattern 2: Sequential Agent Workflow

```python
class WorkflowOrchestrator:
    def execute_workflow(self, input_data: dict) -> dict:
        # Step 1: Agent 1 processes input
        result_1 = self.agent_1.process(input_data)
        
        # Step 2: Agent 2 uses Agent 1's output
        result_2 = self.agent_2.process(result_1)
        
        # Step 3: Agent 3 finalizes
        final_result = self.agent_3.process(result_2)
        
        return final_result
```

### Pattern 3: Parallel Agent Execution

```python
import asyncio

class ParallelOrchestrator:
    async def process_parallel(self, query: str) -> dict:
        # Execute multiple agents simultaneously
        results = await asyncio.gather(
            self.agent_1.process_async(query),
            self.agent_2.process_async(query),
            self.agent_3.process_async(query)
        )
        
        # Synthesize results
        return self.synthesize(results)
```

---

## Troubleshooting Common Issues

### Issue: Inconsistent Agent Outputs

**Symptoms:** Agent gives different answers to same question

**Solutions:**
- Set `temperature=0` for deterministic outputs
- Add more specific examples in prompt
- Use structured output format (JSON)
- Add validation logic

### Issue: Agent Misunderstands Intent

**Symptoms:** Agent does wrong thing or doesn't understand

**Solutions:**
- Add clarifying examples to prompt
- Implement intent classification layer
- Add conversation context
- Make agent ask clarifying questions

### Issue: Integration Failures

**Symptoms:** External API calls fail or timeout

**Solutions:**
- Add retry logic with exponential backoff
- Implement fallback to cached/simulated data
- Add timeout limits
- Log errors for debugging

### Issue: Slow Response Times

**Symptoms:** Takes too long to respond

**Solutions:**
- Cache frequent queries
- Reduce context window size
- Use parallel processing where possible
- Stream responses for better UX

---

## Pre-Demo Checklist

Two days before stakeholder demo:

- [ ] All demo scenarios tested and working
- [ ] Error handling in place (graceful failures)
- [ ] UI is clear and intuitive
- [ ] No debugging output visible to user
- [ ] All placeholders replaced with real content
- [ ] Agent outputs match stakeholder brand voice
- [ ] Integration fallbacks working
- [ ] Demo environment stable
- [ ] Backup plan prepared (screen recording)
- [ ] Demo script written and practiced

---

## Deployment for Demo

### Local Demo (Simplest)

```bash
# Run on your machine during demo
streamlit run ui/app.py
```

### Quick Cloud Deployment

```bash
# Deploy to Railway (free tier)
railway init
railway up

# Or deploy to Streamlit Cloud
# Just push to GitHub and connect repository
```

### Docker Deployment

```dockerfile
# Dockerfile
FROM python:3.11
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["streamlit", "run", "ui/app.py"]
```

---

## Next Steps After Prototype

After successful demo:

1. **Gather feedback** from stakeholder testing
2. **Prioritize improvements** based on feedback
3. **Plan production development** (if approved)
4. **Document lessons learned**
5. **Archive prototype code** for reference

---

**Remember:** The prototype's job is to prove the concept works and demonstrate value. It doesn't need to be perfect—it needs to be functional and convincing.

Ship working code, gather feedback, iterate.

