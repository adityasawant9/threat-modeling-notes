# What is Threat Modeling
Threat modeling is an effective technique to help secure your systems, applications, networks, and services. It helps you identify potential threats and risk reduction strategies earlier in the development lifecycle. Threat modeling uses a data-flow diagram that graphically shows how the system works. It then applies a framework to help you find and fix security issues.

## Objective of Threat Modeling

## Threat Modeling Phases
Each phase contains important steps to help you create a data-flow diagram and analyze it for potential threats.
1. Design: Capture all requirements for your system and create a data-flow diagram.
2. Break: Apply a threat-modeling framework to the data-flow diagram and find potential security issues.
3. Fix: Decide how to approach each issue with the right combination of security controls.
4. Verify: Verify requirements are met, issues are found, and security controls are implemented.

## Step 1 - Design
Gather as much data as possible about what you're building and what you're using to build it. Ask as many questions as possible about your system. Here are a few questions to consider:
- System description: What does the system do? What are the business processes handled by the service? Are they clearly defined?
- System environment: Will the system be built on the cloud or on-premises? On which operating system is it built? Does it use containers? Is the system an application, service, or something entirely different?
- Scenarios: How will the system be used? How will it not be used?
- Permissions: Does the system have script-execution, data, or hardware-access requirements? If so, what are they?
- Cloud provider: Which cloud provider does the system use? What default security configuration options does the provider offer? How do these options affect the system security requirements?
- Operating system: Which Operating System will the system use? What default security configuration options does the operating system offer? How do these options affect the system security requirements?
- First- and third-party: Which first- and third-party services will the system use? What default security configuration options do they offer? How do these options affect the system security requirements?
- Accounts: What are the account types that the system uses, like users and administrators? Are these accounts be local or cloud-enabled? What access do they need and why?
- Identity & access control: How does the system help secure those accounts? Does it rely on Microsoft Entra ID? Does it use features like Access Control Lists (ACL), multifactor authentication (MFA), and Session control?
- Tokens & sessions: Will the system process requests like SOAP or REST APIs? How does it handle different sessions?
- Bypass: Will the system use or require back doors? If so, how does that bypass work?
- Logging, monitoring and backing up: What are the mechanisms the system uses to log security events, monitor for anomalies, and back up system data? Which event types does capture?
- Network: What are all the intrusion, detection, and protection systems that will be used? How is communication encrypted?
- Data: What type of data will the system create or handle? What will the data classification type be? How does the system trust data sources? How does it parse data? What are the expected input and output behaviors? How is validation handled? How is data encrypted across all states?
- Secrets management: How does the system handle keys, certificates, and credentials?

### Create a data-flow diagram
Use the answers to create a data-flow diagram. Your diagram shows data across each stage in the data lifecycle, and includes changes in trust zones. Examples include:

#### Diagraming tools
- Threat Modeling Tool
- Visio

#### Diagram elements
A data-flow diagram shows the flow of data in a given system. It usually starts with requests from users or data stores and ends with data stores or Analytics Services. The data-flow diagram uses distinct shapes to indicate the elements they represent.
[Example](https://learn.microsoft.com/en-us/training/modules/tm-introduction-to-threat-modeling/2-step-1-design-phase)

#### Diagram layers
To help you understand how much information to include, choose between these four context depth layers:

0. System: Starting point for any system. Data-flow diagram contains major system parts with enough context to help you understand how they work and interact with each other.
1. Process: Focus on data-flow diagrams for each part of the system by using other data-flow diagrams. Use this layer for every system, especially if it handles sensitive data. The context at this layer helps you identify threats and ways to reduce or eliminate risks more efficiently.
2. Subprocess: Focus on data-flow diagrams for each subpart of a system part. Used for systems considered critical. Examples include systems for secured environments, systems that handle highly sensitive data, or systems that contain a high risk rating.
3. Lower-Level: Focus on highly critical and kernel-level systems. Data-flow diagrams describe each subprocess in minute detail.

## Step 2 - Break
The break phase is where you use the data-flow diagram to find potential threats against your system. The process uses a threat-modeling framework to help you find the most common threats and ways to protect against them. The goal is Using the STRIDE framework to identify common threats.

Start by choosing whether you want to find ways to protect your system, or you want to understand all you can about an attacker and their motives. Examples include:

Focus | Example of what you can find
---|---
System | You find an issue with an unencrypted connection between the user and the system.
Attacker| You find out more about means, motivation, and ways to harden the system entry points.
Asset| You identify critical assets based on things like classified data handling, and focus mostly on protecting those assets.

### Select a threat framework
Next, select a framework to help generate potential threats in your system. STRIDE, an acronym for the six main threat categories to provide an extensive—but not exhaustive—list of threats. The framework helps you ask a few important questions about your system:

| Threat | Definition | Question | Threat example |
|--------|------------|----------|----------------|
| Spoofing | Attacker pretends to be someone or something else | Are both sides of the communication authenticated? | Sending an email to users from an account that seems legitimate with malicious links and attachments to capture their credentials, data, and device access |
| Tampering | Attacker changes data without authorization | How do I know someone can't change data in transit, in use, or at rest? | Modifying memory through weak API call handling to cause crashes and disclosure of sensitive error messages |
| Repudiation | Attacker claims to not have done something | Can every action be tied to an identity? | Claiming to not have deleted database records |
| Information Disclosure | Attacker sees data they aren't supposed to see | How do I know someone can't see data in transit, in use, or at rest? | Accessing unauthorized documents and folders with weak security controls |
| Denial of Service | Attacker brings your system down | Are there areas in the system where resource is limited? | Flooding the network with requests |
| Elevation of Privilege | Attacker has unauthorized access to data | How do I know someone is allowed to take this action? | Extracting data by exploiting weaknesses in input-handling logic or memory |

## Step 3 - Fix
### Goals
1. Measure each threat against a prioritization framework or security bug bar
2. Track each threat as a task or work item in a bug-management service
3. Generate security control recommendations that are mapped to STRIDE threats
4. Select one or more security control types and functions to address each threat
5. Resolve tasks

### Prioritize threats
Start by measuring each threat against a prioritization framework or security bug bar. This process helps you arrange resources to fix issues deemed most important to your organization.

| Variable | Description |
|----------|-------------|
| Impact   | Uses STRIDE categories to assign impact |
| Severity | Uses internal bug bar or prioritization framework to assign severity using worst-case scenarios |
| Risk     | Uses a calculation of security control effectiveness and implementation cost |

### Create tasks
Next, add each threat in a bug-management solution

### Rate security control effectiveness and cost
Visit each security control recommendation mapped to STRIDE threats. Write down the ones that are most effective and least expensive to implement.

| Threat | Security Control | Security Control Example |
|--------|------------------|-------------------------|
| Spoofing | Authentication | Send and receive messages signed with digital signatures to authenticate origin and ensure message integrity |
| Tampering | Integrity | Validate input to prevent the processing of malicious payloads and mishandling of unexpected behavior |
| Repudiation | Nonrepudiation | Create and protect security logs that contain user actions and timestamps |
| Information disclosure | Confidentiality | Apply access control lists to ensure the right users can access to the right data |
| Denial of service | Availability | Use elastic resources to manage growing or shrinking usage |
| Elevation of privilege | Authorization | Run the service using the least possible amount of access |

### Security control types and functions
Security controls have different types and functions. When combined, they help secure your system and create multiple layers of security, also known as defense-in-depth.

You can choose one or more security control types:
- Physical, like cameras
- Technical, like encryption
- Administrative, like policies

These types have one or more security control functions:
- Preventive : Reduces the probability or impact of a threat, like firewalls
- Detective : Identifies attacks as they happen, like surveillance
- Corrective : Controls how the system responds to an ongoing attack, like system patches
- Recovery : Recovers system from an attack, like backups
- Deterrent : Keeps attackers away from the system, like least privilege

### Add security control details to each issue
Add the details to each issue in the bug management solution/ dashboard/ tracker, then resolve each issue with one of the following resolutions.

- Reduce : Use bug fixes or redesign to reduce or eliminate threat impact and severity.
- Transfer : Assign issue to another system or team.
- Avoid : The part of the system that contains the issue will be cut.
- Accept: Risk is accepted without a resolution. This resolution requires approval of an authorized risk decision maker. The decision might be based on threat severity. Critical severity threats might require approval from senior leadership, while a defense-in-depth risk might require approval by a senior engineer.

## Step 4 - Verify
The verify phase is the last step of the threat-modeling process, which often happens before the system is deployed. It involves ensuring requirements are met, assumptions are validated, and security controls are in place.

### Goals
- Confirm that the system satisfies all previous and new security requirements
- Configure cloud provider, operating system, and components to meet security requirements
- Ensure that all issues are addressed with the right security controls
- Take the system through manual and automated verification before deployment

### Verify requirements and set defaults
Start by verifying that all requirements created in the first phase are met.

Examples:
- Network security plans
- Secrets-management solution implementation
- Logging and monitoring systems
- Identity and access controls
Then make sure to change all the default configuration settings from the cloud provider, operating system, and components to meet all security requirements.

Examples:
- Enable Azure SQL Database transparent data encryption to protect data on disk
- Use Role Based Access Control (RBAC) to assign permissions to users, groups, and applications
- Enable Windows Firewall across all profiles

### Run verification
The last part involves running both manual and automated verification. The process might include automated scanners, code reviews, and penetration tests. The process can be enforced before each deployment or across time intervals, like every 6-12 months.
