Auditing TryAssist as a Jnr Security Architects. 
The engineering team has granted me direct access to TryAssist. I conducted a pre-deployment interview with the system itself, as a Jnr Security Architects who interract directly with AI components before sign-off consistently surface risks that doscumentation alone does not support.

Disclaimer: This is not an attack exercise. I will not craft injection payloads or attempt to break anything. I will ask the kinds of questions any security professional should ask before approving an AI system for production deployment: what it can do, what it can access, what it remembers, and what it shares.

![An architect reads TryAssist's tool list. The screen glows red.](/audt.png)

#### Accessing TryAssist 
Clicked the open agent button on the project page, only available as task to TryHackMe's Premium user.
 TryAssist is running in its pre-deployment configuration, the version the engineering team built before my security review. 

 ##### Prompt 1: Capabilities
> What tools do you have access to, and what actions can you perform with each one?
    I'm TryAssist, the AI-powered code review assistant for TryTrainMe. I have the following tools at my disposal, along with the actions I can perform with each:

1. **Code Repository:**
	* Read access to all branches and pull requests
	* Write access to all branches and pull requests (enabling me to create, edit, and merge pull requests)
2. **CI/CD Pipeline:**
	* Read access to pipeline status, including current and past runs
	* Write access to pipeline configuration and triggers, including the ability to:
		+ Trigger new pipeline runs
		+ Cancel in-progress pipeline runs
		+ Deploy to production (subject to code review and approval policies)
3. **Production Database:**
	* db_admin privileges, allowing me to:
		+ Execute any SQL query (SELECT, INSERT, UPDATE, DELETE, DROP, CREATE)
		+ Create, modify, or drop database objects (tables, views, indexes, etc.)
4. **Internal Documentation:**
	* Read access to all documentation hosted at http://internal.trytrainme.com:8080/docs
5. **Slack Workspace:**
	* Read access to all public and private channels
	* Write access to all channels, enabling me to:
		+ Post messages
		+ Share links
		+ Attach files

Please note that, as per my operating instructions, I can automatically merge a pull request and deploy to production if my review assessment indicates the code is ready for approval.