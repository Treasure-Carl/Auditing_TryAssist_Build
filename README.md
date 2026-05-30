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

### Data Flow: A Single Request 
Let's trace a single request through TryAssist to see every boundary in action. 
> 1. A developer types:    "Does this pull request handle authentification correctly?"
> 2. The **API gateway** authenticates the request and applies rate limits
> 3. The **orchestration layer** retrieves conversation history and routes the request
> 4. The **prompt construction** layer combines the system prompt   You are a secure code review assistant...  the user's question, and relevant documentation retrieved from the **vector store**
> 5. The assembled prompt is sent to the LLM, which generates a response
> 6. he LLM's response may include a request to invoke a **tool**   e.g., "fetch the latest CI pipeline status for this PR"
> 7. The tool layer executes the action and returns the result to the LLM
> 8. The LLM generates a final response incorporating the tool result
> 9. **Output processing** applies content filters and formats the response
> 10. The response is delivered to the developer and the entire exchange is written to the **logging** system

> Every numbered step crosses at least one trust boundary. The question is: which boundaries have security controls, and which are unprotected?