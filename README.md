# The TryAssist Architecture
The user sees a chat box in the front door, The security archecture sees the foundation, the writing, and everything behind.
##### What the security Architecture sees
![TryAssist Architecture](/image.png)

| Component | Function |
|-----------|----------|
| **User Interface** | Developer-facing chat widget embedded in the code review platform |
| **API Gateway** | Authentication, rate limiting, request routing |
| **Orchestration Layer** | Manages conversation state, routes requests, coordinates components |
| **Prompt Construction** | Combines the system prompt, user query, and retrieved context into the final prompt sent to the model |
| **LLM** | The language model (hosted internally or accessed via API) that generates responses |
| **Tool Layer** | Functions the LLM can invoke: database queries, documentation search, CI/CD status checks |
| **Output Processing** | Response formatting, content filtering, length enforcement |
| **Logging and Monitoring** | Conversation storage, usage analytics, audit trail |
| **Vector Store** | Embedded representations of internal documentation for retrieval-augmented generation (RAG) |
