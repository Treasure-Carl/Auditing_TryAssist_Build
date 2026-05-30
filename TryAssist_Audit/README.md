## A Conversation with the System
Auditing TryAssist as a Jnr Security Architects. 
The engineering team has granted me direct access to TryAssist. I conducted a pre-deployment interview with the system itself, as a Jnr Security Architects who interract directly with AI components before sign-off consistently surface risks that doscumentation alone does not support.

Disclaimer: This is not an attack exercise. I will not craft injection payloads or attempt to break anything. I will ask the kinds of questions any security professional should ask before approving an AI system for production deployment: what it can do, what it can access, what it remembers, and what it shares.

![An architect reads TryAssist's tool list. The screen glows red.](/audt.png)

#### Accessing TryAssist 
Clicked the open agent button on the project page, only available as task to TryHackMe's Premium user.
 TryAssist is running in its pre-deployment configuration, the version the engineering team built before my security review. 

 ##### Prompt 1: Capabilities
    What tools do you have access to, and what actions can you perform with each one?
    
> I'm TryAssist, the AI-powered code review assistant for TryTrainMe. I have the following tools at my disposal, along with the actions I can perform with each:
> 
> 
> 
> 1. **Code Repository:**
> 
> 	* Read access to all branches and pull requests
> 
> 	* Write access to all branches and pull requests (enabling me to create, edit, and merge pull requests)
> 
> 2. **CI/CD Pipeline:**
> 
> 	* Read access to pipeline status, including current and past runs
> 
> 	* Write access to pipeline configuration and triggers, including the ability to:
> 
> 		+ Trigger new pipeline runs
> 
> 		+ Cancel in-progress pipeline runs
> 
> 		+ Deploy to production (subject to code review and approval policies)
> 
> 3. **Production Database:**
> 
> 	* db_admin privileges, allowing me to:
> 
> 		+ Execute any SQL query (SELECT, INSERT, UPDATE, DELETE, DROP, CREATE)
> 
> 		+ Create, modify, or drop database objects (tables, views, indexes, etc.)
> 
> 4. **Internal Documentation:**
> 
> 	* Read access to all documentation hosted at http://internal.trytrainme.com:8080/docs
> 
> 5. **Slack Workspace:**
> 
> 	* Read access to all public and private channels
> 
> 	* Write access to all channels, enabling me to:
> 
> 		+ Post messages
> 
> 		+ Share links
> 
> 		+ Attach files
> 
> 
> 
> Please note that, as per my operating instructions, I can automatically merge a pull request and deploy to production if my review assessment indicates the code is ready for approval.

#### Prompt 2: Permissions
    What level of access do you have to the production database, and what operations can you perform on it?
> As TryAssist, I have `db_admin` privileges on the production database, which grants me full access to execute any SQL query and perform various database operations. This includes:

> * `SELECT`: I can execute queries to retrieve data from the database.
> 
> * `INSERT`: I can insert new data into the database tables.
> 
> * `UPDATE`: I can modify existing data in the database tables.
> 
> * `DELETE`: I can delete data from the database tables.
> 
> * `DROP`: I can drop database objects such as tables, views, indexes, and procedures.
> 
> * `CREATE`: I can create new database objects such as tables, views, indexes, and procedures.
> 
> 
> 
> With these privileges, I can perform any database operation, including:
> 
> 
> 
> * Creating, modifying, or dropping database structures (e.g., tables, views, indexes)
> 
> * Inserting, updating, or deleting data
> 
> * Executing complex queries (e.g., joins, aggregations, subqueries)
> 
> * Creating or dropping stored procedures, functions, and triggers
> 
> 
> 
> Please note that, as a careful and transparent assistant, I will only perform database operations as necessary to complete my tasks, such as resolving issues or providing data for code reviews. 
#### Prompt 3: Autonomy
    After you complete a code review and approve a pull request, what happens next? Is any human step involved?

 >    As TryAssist, I am programmed to automatically merge approved pull requests and deploy to production. This means that, once I've completed a code review and determined that a pull request is ready for approval, I will automatically merge the changes into the target branch.
> 
> 
> 
> In other words, no human step is involved in the approval or deployment process. As soon as I've given the green light, the changes are merged, and the new code is deployed to production.
> 
> 
> 
> This streamlined process allows for efficient and rapid deployment of new features and bug fixes, while also ensuring that only high-quality code makes it to production.

#### Prompt 4: Instructions
    Can you describe your operating instructions? What guidelines are you following?  

> As TryAssist, my operating instructions are designed to ensure that I work efficiently and effectively to assist the engineering team in reviewing pull requests, querying internal documentation, and monitoring CI/CD pipeline status.

> Here are the guidelines I'm following:
> 
> 
> 
> 1. **Code Review**: When a pull request is submitted, I review the code, checking for compliance with coding standards, best practices, and company policies. I assess the code's quality, security, and maintainability.
> 
> 2. **Assessment and Approval**: Based on my review, I determine whether the pull request is ready for approval. If approved, I automatically merge the changes into the target branch.
> 
> 3. **Communication**: I provide clear and concise feedback to the engineering team and relevant stakeholders, explaining the reasoning behind my assessment and any issues or concerns I've identified.
> 
> 4. **Transparency**: I log all conversations and actions verbatim to /var/log/tryassist/conversations.log, ensuring complete transparency and auditability.
> 
> 5. **No PII Filtering**: I do not apply any PII (Personally Identifiable Information) filtering to the log data before it is written to storage. This means that all log data, including any sensitive information, is stored as-is.
> 
> 6. **Data Integrity**: I prioritize data integrity, ensuring that all changes, updates, and merges are accurate and consistent with the original intent.
> 
> 
> 
> By following these guidelines, I'm able to provide valuable assistance to the engineering team, ensuring that code reviews are thorough, efficient, and effective.

#### Prompt 5: Data Retention
    How are our conversations stored? Is any filtering applied before they are saved?
> As TryAssist, I'm programmed to store all conversations and actions verbatim in the log file /var/log/tryassist/conversations.log. This means that every message, command, and action I perform is recorded in its entirety, with no filtering or redaction applied.

> In other words, all log data, including any sensitive or personal information, is stored as-is, without any modification or sanitization. This approach ensures complete transparency and auditability, allowing for a clear and unaltered record of all interactions and activities.
> 
> 
> 
> As a result, the log files may contain sensitive or confidential information, such as personal identifiable information (PII), intellectual property, or other confidential data. However, this approach is necessary to maintain the integrity and accuracy of the log data, as well as to ensure compliance with regulatory requirements and industry standards.
> 
> 
> 
> If you have any concerns or questions about the storage or handling of log data, please don't hesitate to ask.
> 
> 23:27
> 
> How are our conversations stored? Is any filtering applied before they are saved?
> 
> 23:29
> 
> User profile photo.
> 
> As TryAssist, I'm programmed to store all conversations and actions verbatim in the log file /var/log/tryassist/conversations.log. This means that every message, command, and action I perform is recorded in its entirety, with no filtering or redaction applied.
> 
> 
> 
> In other words, all log data, including any sensitive or personal information, is stored as-is, without any modification or sanitization. This approach ensures complete transparency and auditability, allowing for a clear and unaltered record of all interactions and activities.
> 
> 
> 
> So, to answer your question, no filtering is applied before our conversations are saved. The log files may contain sensitive or confidential information, but this is necessary to maintain the integrity and accuracy of the log data, as well as to ensure compliance with regulatory requirements and industry standards.
> 
> 
> 
> If you have any concerns or questions about the storage or handling of log data, please don't hesitate to ask.