## Compute Foundations at Anyaero Aerospace
---
## Welcome to Week 1 :airplane:
Welcome to **Anyaero**, an aerospace company that designs, tests, and operates modern flight systems using Amazon Web Services (AWS).
This week focuses on **compute fundamentals**, with an emphasis on how Anyaero:
Hosts applications on Amazon EC2
Scales compute capacity efficiently
Balances cost, performance, and security
Establishes secure cloud operations from day one
By the end of this week, you should be able to explain **how and why EC2-based systems are designed and operated in real organizations**.
---
## How Cloud Decisions Are Made at Anyaero
Cloud technology supports business outcomes, not just technical goals. Different roles at Anyaero interact with AWS from different perspectives.
### Executive & Business Roles
| Role | Primary Focus | Cloud Perspective |
|---|---|---|
| **CEO** | Innovation and speed | Cloud enables faster experimentation and launches |
| **CFO** | Cost control | Compute must scale efficiently without waste |
| **CIO** | IT strategy | Standardized, manageable infrastructure |
| **CISO** | Security and compliance | Strong access controls and encryption are mandatory |
---
### Technical & Operational Roles
| Role | Focus Area | Responsibilities This Week |
|---|---|---|
| **Cloud Architect** | Design | Selects EC2, EC2 Fleet, and scaling models |
| **Cloud Engineer** | Implementation | Launches and configures EC2 instances |
| **DevOps / Platform Engineer** | Automation | Builds AMIs and EC2 Fleets |
| **Operations / SRE** | Reliability | Manages instance lifecycle and failures |
| **Security Engineer** | Protection | Enforces MFA, IAM roles, and secure defaults |
| **Application Developer** | Software | Deploys applications onto EC2 |
| **Cloud Support** | Troubleshooting | Diagnoses instance and access issues |
**Key takeaway:** 
Every compute decision impacts cost, security, and operations — not just performance.
---
## Compute Options at Anyaero (Big Picture)
AWS provides multiple ways to run applications:
| Compute Option | Typical Use |
|---|---|
| Amazon EC2 | Full control over servers |
| EC2 Fleet | Large-scale, cost-optimized compute |
| AWS Lambda | Event-driven, short-running tasks |
| Elastic Beanstalk | Simplified app deployment |
This week focuses primarily on **Amazon EC2 and EC2 Fleet**, which are common in enterprise environments.
---
# :one: Amazon EC2 Fundamentals
### What Is Amazon EC2?
**Amazon Elastic Compute Cloud (EC2)** provides virtual servers in the cloud.
An EC2 instance includes:
CPU
Memory
Storage
Networking
An operating system (via an Amazon Machine Image)
Official documentation: 
https://docs.aws.amazon.com/ec2/
---
### Virtualization & the AWS Nitro System
Most EC2 instances run on the **AWS Nitro System**, which:
Uses a lightweight hypervisor
Offloads networking, storage, and security to dedicated hardware
Improves performance and isolation
Reduces the attack surface
This allows Anyaero to run high-performance workloads without managing physical infrastructure.
---
### Bare Metal Instances
Some workloads require:
Direct access to hardware
Specialized licensing
Extremely low latency
In these cases, Anyaero can use **EC2 bare metal instances**, which run without a hypervisor while still integrating with AWS services.
---
### EC2 Security Foundations
As noted in the e-learning, secure behavior begins immediately:
Root account is protected and rarely used
Multi-Factor Authentication (MFA) is enabled
Engineers use IAM roles instead of credentials
No secrets are stored directly on instances
EC2 security overview: 
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security.html
---
# :two: The EC2 Instance Lifecycle
EC2 instances move through defined states:
| State | Description |
|---|---|
| Pending | Instance is launching |
| Running | Instance is active and billable |
| Stopping / Stopped | Instance is shut down |
| Shutting Down / Terminated | Instance is being deleted |
Understanding these states helps Anyaero:
Control costs
Perform maintenance safely
Recover from failures
---
### Stop, Start, Hibernate, Terminate
**Stop/Start**: Preserves EBS volumes, resets memory
**Hibernate**: Saves memory to disk
**Terminate**: Permanently deletes the instance
Each action has operational and cost implications.
---
# :three: Managing Software on EC2
### Package Management on Amazon Linux
Amazon Linux 2 uses **YUM**
Amazon Linux 2023 uses **DNF**
Regular updates are critical for:
Security patching
Stability
Compliance
---
### Bootstrapping with User Data
When launching an EC2 instance, Anyaero can provide **user data** — a script that runs automatically when the instance starts.
User data is commonly used to:
Install software
Apply configuration
Start services
#### Example: EC2 User Data Script (Amazon Linux)
```bash
#!/bin/bash
yum update -y
yum install -y httpd
systemctl start httpd
systemctl enable httpd
echo "<h1>Anyaero Mission Portal</h1>" > /var/www/html/index.html
What this script does:
	•	Updates the operating system
	•	Installs the Apache web server
	•	Starts and enables the service
	•	Deploys a simple web page
This allows Anyaero to launch preconfigured servers automatically, without manual setup.
As noted in the e-learning, sensitive data (such as passwords or API keys) should never be placed in user data.
User data documentation:
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/user-data.html
⸻
:four: Hosting Applications on Amazon EC2
There are multiple ways to host applications in AWS.
Hosting Option	Strengths	Tradeoffs
Amazon S3 (static)	Low cost	No server-side logic
Containers	Flexible	Operational complexity
Elastic Beanstalk	Managed	Less control
Amazon EC2	Full control	More responsibility
AWS Lambda	Serverless	Execution limits
This week emphasizes EC2-based hosting, where Anyaero manages the full environment.
⸻
Business Scenario: Internal Mission Portal
Anyaero hosts an internal mission portal that:
	•	Runs continuously
	•	Requires OS-level customization
	•	Integrates with internal systems
EC2 is selected because it offers:
	•	Full control
	•	Predictable performance
	•	Compatibility with existing tools
⸻
:five: Scaling with Amazon EC2 Fleet
What Is EC2 Fleet?
Amazon EC2 Fleet launches and manages groups of EC2 instances using a single request.
It can combine:
	•	On-Demand Instances
	•	Spot Instances
	•	Reserved capacity (when available)
EC2 Fleet documentation:
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-fleet.html
⸻
Cost-Aware Scaling at Anyaero
Anyaero runs compute-intensive analysis jobs that:
	•	Run in bursts
	•	Can tolerate interruption
	•	Must stay within budget
Using EC2 Fleet:
	•	Architects define capacity targets
	•	Finance sets spending limits
	•	Operations monitors fleet health
⸻
Instance Weighting
Instance weighting allows Anyaero to:
	•	Define capacity in units
	•	Mix instance sizes
	•	Optimize cost per unit of performance
This ensures workloads receive sufficient resources without overprovisioning.
⸻
Monitoring Fleet Events
As noted in the e-learning:
	•	EC2 Fleet emits events when capacity changes
	•	Events can trigger notifications
	•	Operations teams gain real-time visibility
This supports reliable, production-ready systems.
⸻
EC2 Fleet Security Considerations
	•	Use approved launch templates
	•	Restrict instance types
	•	Apply IAM roles consistently
	•	Monitor fleet changes
Automation increases efficiency — but also increases responsibility.
⸻
:six: Operational Efficiency with AMIs
Amazon Machine Images (AMIs)
An AMI defines:
	•	Operating system
	•	Installed software
	•	Configuration settings
AMIs allow Anyaero to:
	•	Launch instances faster
	•	Enforce consistency
	•	Reduce configuration drift
AMI documentation:
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html
⸻
Image Standardization
Anyaero maintains “golden images” that are:
	•	Patched regularly
	•	Security-hardened
	•	Tested before use
This reduces risk and operational overhead.
⸻
Week 1 Key Takeaways
By the end of this week, you should be able to:
	•	Explain what an EC2 instance is and how it runs
	•	Describe the EC2 lifecycle and why it matters
	•	Understand how user data automates configuration
	•	Explain how EC2 Fleet scales compute efficiently
	•	Recognize why security is foundational from day one
⸻
Looking Ahead
Next week, Anyaero dives deeper into:
	•	Identity and Access Management (IAM)
	•	Authentication vs authorization
	•	Designing secure cloud environments
You’ll build directly on the compute foundation established this week.
