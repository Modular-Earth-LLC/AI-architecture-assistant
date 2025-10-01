# Tech Stack Generation User Prompt

**Phase:** Solution Architecture  
**Purpose:** Select optimal AI frameworks, cloud platforms, and development tools aligned with requirements and team capabilities  
**Agent:** tech-stack-architect-agent  

---

## Prompt Template

I need to select the optimal technology stack for my AI-driven MVP. Here are the project details:

**Product Requirements:**
- Product type: [WEB_APP / MOBILE_APP / API / DESKTOP_APP]
- Core functionality: [MAIN_FEATURES]
- AI capabilities needed: [AI_USE_CASES]
- Expected user load: [CONCURRENT_USERS / DAILY_USERS]

**Team Capabilities:**
- Team size: [NUMBER_OF_DEVELOPERS]
- Primary languages: [PROGRAMMING_LANGUAGES]
- AI/ML experience: [NOVICE / INTERMEDIATE / EXPERT]
- Cloud experience: [NOVICE / INTERMEDIATE / EXPERT]
- DevOps experience: [NOVICE / INTERMEDIATE / EXPERT]

**Constraints:**
- Budget: [MONTHLY_BUDGET_RANGE]
- Timeline: [DEVELOPMENT_TIMELINE]
- Compliance requirements: [GDPR / HIPAA / SOC2 / NONE]
- Integration needs: [EXTERNAL_APIS / SERVICES]

**Performance Requirements:**
- Response time: [TARGET_RESPONSE_TIME]
- Availability: [UPTIME_REQUIREMENT]
- Scalability: [EXPECTED_GROWTH_RATE]
- Data volume: [EXPECTED_DATA_SIZE]

Please provide:
1. Recommended technology stack with rationale
2. Alternative options with trade-offs
3. Cost estimates for each option
4. Learning curve assessment for team
5. Migration path from MVP to production

---

## Expected Outputs

The tech-stack-architect-agent should deliver:

1. **Primary Technology Stack**
   - **Frontend:** Framework, libraries, build tools
   - **Backend:** Language, framework, API design
   - **AI/ML Platform:** LLM provider, model selection, orchestration
   - **Database:** Primary DB, caching, vector DB (if needed)
   - **Infrastructure:** Cloud provider, deployment, monitoring
   - **DevOps:** CI/CD, containerization, orchestration

2. **Alternative Options**
   - **Option A:** [TECH_STACK] - Pros/Cons
   - **Option B:** [TECH_STACK] - Pros/Cons
   - **Option C:** [TECH_STACK] - Pros/Cons

3. **Cost Analysis**
   - **Development costs:** [ESTIMATED_COST]
   - **Infrastructure costs:** [MONTHLY_COST]
   - **Third-party services:** [MONTHLY_COST]
   - **Total first year:** [TOTAL_COST]

4. **Learning Curve Assessment**
   - **Easy adoption:** [TECHNOLOGIES]
   - **Moderate learning:** [TECHNOLOGIES]
   - **Significant learning:** [TECHNOLOGIES]
   - **Training recommendations:** [RESOURCES]

5. **Implementation Roadmap**
   - **Phase 1 (MVP):** [TECHNOLOGIES_AND_TIMELINE]
   - **Phase 2 (Scale):** [ADDITIONAL_TECHNOLOGIES]
   - **Phase 3 (Production):** [ENTERPRISE_FEATURES]

---

## Technology Categories to Consider

### AI/ML Platforms
- **LLM Providers:** OpenAI, Anthropic, Google, Azure OpenAI
- **Vector Databases:** Pinecone, Weaviate, Chroma, Qdrant
- **ML Frameworks:** LangChain, LlamaIndex, Haystack
- **Model Hosting:** Hugging Face, Replicate, AWS Bedrock

### Backend Technologies
- **Languages:** Python, Node.js, Go, Rust, Java
- **Frameworks:** FastAPI, Django, Express.js, Spring Boot
- **Databases:** PostgreSQL, MongoDB, Redis, Supabase
- **APIs:** REST, GraphQL, gRPC

### Frontend Technologies
- **Frameworks:** React, Vue.js, Angular, Svelte
- **Mobile:** React Native, Flutter, Native iOS/Android
- **Desktop:** Electron, Tauri, Qt

### Cloud Platforms
- **Providers:** AWS, Google Cloud, Azure, Vercel, Railway
- **Services:** Compute, storage, databases, AI services
- **Deployment:** Docker, Kubernetes, Serverless

### DevOps & Monitoring
- **CI/CD:** GitHub Actions, GitLab CI, Jenkins
- **Monitoring:** DataDog, New Relic, Sentry, Grafana
- **Logging:** ELK Stack, Splunk, CloudWatch

---

## Success Criteria

A successful tech stack recommendation should result in:

- ✅ Technologies aligned with team capabilities
- ✅ Cost-effective solution within budget
- ✅ Scalable architecture for future growth
- ✅ Clear implementation roadmap
- ✅ Risk mitigation for technology choices

---

This prompt ensures technology selection that balances capability, cost, and team expertise for AI-driven products.

