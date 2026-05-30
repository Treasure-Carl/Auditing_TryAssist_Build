# The TryAssist Architecture
The user sees a chat box in the front door, The security archecture sees the foundation, the writing, and everything behind.
##### What the security Architecture sees
![TryAssist Architecture](/arch.png)

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

### Trust Boundaries 
 TryAssist has five different attack boundries gotten from the securiy anatomy above - The trust boundary is where data moves from one security context to another, and everyone is a potential attack surface.  
| Boundary | Data Crossing|
|-----------|----------|
| **User-to-system** | Untrusted natural language enters the system |
| **System-to-LLM** | Constructed prompt (system instructions + user input + context) sent to the model |
| **LLM-to-tools** | Model output triggers database queries, API calls, or file operationsl |
|**System-to-external-data** | Retrieved documents from vector store or external sources enter the prompt |
| **System-to-user** | Generated response delivered to the user |