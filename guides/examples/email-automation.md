# Example: Email Response Automation Agent

**Time to complete:** 15 minutes  
**Difficulty:** ⭐ Beginner-friendly  
**Pattern:** Specialist Agent

---

## The Problem

**Scenario:** A small business owner receives 20-30 customer emails daily asking about pricing, availability, and shipping. 60% of these are repetitive questions that could be answered from a FAQ.

**Current state:** Manually reading and responding to each email takes 2-3 hours/day.

**Goal:** Automate responses to common questions while flagging complex inquiries for human review.

---

## Step 1: Identify the Pattern (2 minutes)

**What we're building:**
- **Input:** Customer email text
- **Processing:** Classify inquiry type, generate appropriate response
- **Output:** Draft email response

**Pattern match:** **Specialist Agent** (single focused task)

Why? This is a classification + generation task with clear rules—perfect for a specialist agent.

---

## Step 2: Design the Agent Prompt (5 minutes)

```markdown
You are a customer service email assistant for [COMPANY NAME].

Your purpose: Generate professional email responses to customer inquiries based on our FAQ and policies.

INPUTS:
- Customer email text
- Email subject line (optional)

YOUR PROCESS:
1. Classify the inquiry type (pricing, availability, shipping, returns, other)
2. If it's a common question (pricing, availability, shipping), generate a response using our FAQ
3. If it's complex or requires human judgment, flag it for review

OUTPUT FORMAT:
{
  "classification": "[inquiry type]",
  "confidence": "[high/medium/low]",
  "response": "[draft email response]",
  "requires_human": true/false,
  "reason": "[why flagged or auto-responded]"
}

EXAMPLE:
Input: "Hi, do you ship to Canada? How much does shipping cost?"
Output: {
  "classification": "shipping",
  "confidence": "high",
  "response": "Hi [Customer Name],\n\nThank you for your interest! Yes, we ship to Canada. Shipping costs are:\n- Standard (7-10 days): $15 USD\n- Express (3-5 days): $35 USD\n\nFree shipping on orders over $100 USD.\n\nLet me know if you have any other questions!\n\nBest regards,\n[Company Name] Team",
  "requires_human": false,
  "reason": "Standard shipping inquiry covered by FAQ"
}

CONSTRAINTS:
- Always be professional and friendly
- Use our company voice: approachable, helpful, concise
- If customer seems upset or mentions a complaint, flag for human review
- Never make up information—only use provided FAQ data
- If unsure (confidence = low), flag for human review

FAQ DATA:
[Paste your actual FAQ here - pricing, shipping, returns, etc.]

ERROR HANDLING:
- If email is empty or gibberish: Flag for human review
- If multiple questions in one email: Address all or flag for human
- If question not in FAQ: Flag for human review with reason
```

---

## Step 3: Implement the Code (5 minutes)

```python
# email_agent.py
import anthropic
import os

class EmailResponseAgent:
    def __init__(self):
        self.client = anthropic.Anthropic(
            api_key=os.environ.get("ANTHROPIC_API_KEY")
        )
        self.system_prompt = """
        [Paste the agent prompt from Step 2 above]
        """
    
    def process_email(self, email_text: str, subject: str = "") -> dict:
        """Process customer email and generate response"""
        
        user_message = f"Subject: {subject}\n\n{email_text}" if subject else email_text
        
        message = self.client.messages.create(
            model="claude-sonnet-4-20250514",
            max_tokens=1024,
            temperature=0,  # Deterministic for consistency
            system=self.system_prompt,
            messages=[
                {"role": "user", "content": user_message}
            ]
        )
        
        # Parse JSON response
        import json
        response_text = message.content[0].text
        
        try:
            result = json.loads(response_text)
            return result
        except json.JSONDecodeError:
            # Fallback if JSON parsing fails
            return {
                "classification": "error",
                "confidence": "low",
                "response": "",
                "requires_human": True,
                "reason": "Could not parse agent response"
            }

# Usage example
if __name__ == "__main__":
    agent = EmailResponseAgent()
    
    # Test with sample email
    sample_email = "Hi, do you ship to Canada? How much does shipping cost?"
    
    result = agent.process_email(sample_email)
    
    print("Classification:", result['classification'])
    print("Confidence:", result['confidence'])
    print("\nDraft Response:")
    print(result['response'])
    print("\nRequires Human Review:", result['requires_human'])
```

---

## Step 4: Create Simple UI (3 minutes)

```python
# email_ui.py
import streamlit as st
from email_agent import EmailResponseAgent

st.set_page_config(page_title="Email Response Assistant", layout="wide")

# Initialize agent
if 'agent' not in st.session_state:
    st.session_state.agent = EmailResponseAgent()

st.title("📧 Customer Email Response Assistant")

# Input section
st.subheader("Incoming Email")
email_subject = st.text_input("Subject Line")
email_body = st.text_area("Email Body", height=200)

if st.button("Generate Response", type="primary"):
    if email_body:
        with st.spinner("Processing..."):
            result = st.session_state.agent.process_email(email_body, email_subject)
        
        # Display results
        col1, col2 = st.columns(2)
        
        with col1:
            st.subheader("Analysis")
            st.write(f"**Type:** {result['classification']}")
            st.write(f"**Confidence:** {result['confidence']}")
            
            if result['requires_human']:
                st.warning(f"⚠️ Requires Human Review: {result['reason']}")
            else:
                st.success("✅ Auto-response ready")
        
        with col2:
            st.subheader("Draft Response")
            st.text_area("", value=result['response'], height=300)
            
            if not result['requires_human']:
                if st.button("✉️ Send Response"):
                    st.success("Response sent! (In real implementation)")
    else:
        st.warning("Please enter an email body")

# Sidebar with stats
with st.sidebar:
    st.header("Statistics")
    st.metric("Emails Processed Today", "47")
    st.metric("Auto-responded", "38 (81%)")
    st.metric("Flagged for Human", "9 (19%)")
```

**Run it:**
```bash
streamlit run email_ui.py
```

---

## Step 5: Test & Iterate (5 minutes)

**Test scenarios:**

1. **Common question (should auto-respond):**
   ```
   "What are your business hours?"
   ```
   Expected: Auto-response with hours from FAQ

2. **Complaint (should flag):**
   ```
   "I'm very unhappy with my order. It arrived damaged."
   ```
   Expected: Flag for human review

3. **Complex multi-part question:**
   ```
   "Do you ship to Canada? Also, can I return items if they don't fit? What's your return policy?"
   ```
   Expected: Either comprehensive response or flag (depending on FAQ completeness)

4. **Edge case (empty email):**
   ```
   ""
   ```
   Expected: Flag for human review

**Iterate:** Refine the prompt based on test results. Common improvements:
- Add more FAQ examples
- Adjust confidence thresholds
- Improve response templates

---

## Results

**Before AI:**
- 20-30 emails/day
- 2-3 hours manual work
- Delayed responses

**After AI (15 minutes of work):**
- 70-80% auto-responded instantly
- 20-30% flagged for human (complex cases)
- 30-45 minutes of human work (reviewing flagged emails)
- **Time saved:** ~2 hours/day = 10 hours/week

**Cost:** ~$20-30/month (Claude API for 600 emails/month)

**ROI:** If your time is worth $50/hour → $500/week saved for $30/month cost = 16x ROI

---

## Next Steps

**To make this production-ready:**

1. **Add email integration:**
   - Connect to Gmail/Outlook API
   - Auto-fetch new emails
   - Send responses directly

2. **Improve FAQ handling:**
   - Store FAQ in vector database for semantic search
   - Update FAQ without changing code

3. **Add analytics:**
   - Track classification accuracy
   - Measure response times
   - Monitor customer satisfaction

4. **Expand capabilities:**
   - Handle attachments
   - Multi-language support
   - Personalization (customer history)

**Time to production:** 1-2 additional weeks

---

## Key Takeaways

✅ **Speed:** Working agent in 15 minutes  
✅ **Simple pattern:** Specialist Agent is perfect for focused tasks  
✅ **Real value:** 2 hours/day saved immediately  
✅ **Iterative:** Start simple, improve based on real usage  
✅ **Pragmatic:** 80% automation is better than 0% while waiting for 100%

**Ready to build your own?** Use this as a template:
1. Identify your repetitive task
2. Choose the pattern (see [Agent Design Patterns](../architecture/agent-design-patterns.md))
3. Write the prompt (30-60 minutes)
4. Implement the code (30-60 minutes)
5. Test and iterate (30 minutes)

**Total time:** 2-3 hours to a working agent.

---

**Questions?** Refer to:
- [Prototype Guide](../development/prototype-guide.md) - Full development process
- [Agent Design Patterns](../architecture/agent-design-patterns.md) - All 9 patterns
- [Discovery Guide](../requirements/discovery-guide.md) - How to identify opportunities

