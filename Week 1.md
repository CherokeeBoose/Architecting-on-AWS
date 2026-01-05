## Compute Foundations at Anyaero Aerospace
---
## Welcome to Week 1
Welcome to Anyaero, an aerospace company that designs, tests, and operates modern flight systems using Amazon Web Services (AWS).
This week focuses on compute fundamentals and how Anyaero:
Hosts applications on Amazon EC2
Manages and scales compute capacity
Balances cost, performance, and security
Establishes strong cloud foundations from day one
By the end of this week, you should understand how EC2-based systems are designed and operated in real organizations.
---
## How Cloud Decisions Are Made at Anyaero
Cloud technology supports business outcomes, not just technical goals.
### Executive and Business Roles
| Role | Primary Focus | Cloud Perspective |
|---|---|---|
| CEO | Innovation and speed | Faster experimentation and launches |
| CFO | Cost and predictability | Efficient scaling and spending controls |
| CIO | IT strategy | Standardized infrastructure |
| CISO | Security and compliance | Strong access controls and encryption |
---
### Technical and Operational Roles
| Role | Focus | Week 1 Responsibilities |
|---|---|---|
| Cloud Architect | Design | Selecting EC2 and scaling strategies |
| Cloud Engineer | Build | Launching and configuring EC2 |
| DevOps Engineer | Automation | AMIs and EC2 Fleet |
| Operations / SRE | Reliability | Instance lifecycle and recovery |
| Security Engineer | Protection | MFA, IAM roles, secure defaults |
| Application Developer | Software | Deploying applications on EC2 |
| Cloud Support | Troubleshooting | Diagnosing compute issues |
---
## Compute Options at Anyaero
| Compute Option | Typical Use |
|---|---|
| Amazon EC2 | Full control over servers |
| EC2 Fleet | Large-scale, cost-optimized compute |
| AWS Lambda | Event-driven workloads |
| Elastic Beanstalk | Simplified deployments |
This week emphasizes Amazon EC2 and EC2 Fleet.
---
## Amazon EC2 Fundamentals
Amazon Elastic Compute Cloud (EC2) provides virtual servers in the cloud.
An EC2 instance includes:
CPU
Memory
Storage
Networking
Operating system (via an AMI)
Documentation:
https://docs.aws.amazon.com/ec2/
---
## EC2 Security Foundations
As noted in the e-learning:
The root account is locked down
Multi-factor authentication is enabled
IAM roles are used instead of credentials
Secrets are not stored on instances
EC2 security documentation:
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security.html
---
## The EC2 Instance Lifecycle
| State | Description |
|---|---|
| Pending | Instance is launching |
| Running | Instance is active and billable |
| Stopped | Instance is shut down |
| Terminated | Instance is permanently deleted |
Understanding lifecycle states helps control cost and reliability.
---
## Managing Software on EC2
### Package Management on Amazon Linux
Amazon Linux 2 uses YUM
Amazon Linux 2023 uses DNF
Regular updates are critical for:
Security patching
Stability
Compliance
---
## Bootstrapping with User Data
When launching an EC2 instance, Anyaero can provide user data. 
User data is a script that runs automatically when the instance starts.
User data is commonly used to:
Install software
Apply configuration
Start services
### Example: EC2 User Data Script (Amazon Linux)
```bash
#!/bin/bash
yum update -y
yum install -y httpd
systemctl start httpd
systemctl enable httpd
echo "<h1>Anyaero Mission Portal</h1>" > /var/www/html/index.html
```

What this script does:
	•	Updates the operating system
	•	Installs the Apache web server
	•	Starts and enables the service
	•	Deploys a simple web page
This allows Anyaero to launch preconfigured servers automatically.
Sensitive data such as passwords or API keys should never be placed in user data.
User data documentation:
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/user-data.html


Hosting Applications on Amazon EC2
There are multiple ways to host applications in AWS.
Hosting Option	Strengths	Tradeoffs
Amazon S3 (static)	Low cost	No server-side logic
Containers	Flexible	Operational complexity
Elastic Beanstalk	Managed	Less control
Amazon EC2	Full control	More responsibility
AWS Lambda	Serverless	Execution limits
This week emphasizes EC2-based hosting where Anyaero manages the full environment.


Business Scenario: Internal Mission Portal
Anyaero hosts an internal mission portal that:
	•	Runs continuously
	•	Requires OS-level customization
	•	Integrates with internal systems
EC2 is selected because it provides:
	•	Full control
	•	Predictable performance
	•	Compatibility with existing tools


Scaling with Amazon EC2 Fleet
Amazon EC2 Fleet launches and manages groups of EC2 instances using a single request.
It can combine:
	•	On-Demand instances
	•	Spot instances
	•	Reserved capacity when available
Documentation:
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-fleet.html


Cost-Aware Scaling at Anyaero
Anyaero runs compute-intensive analysis jobs that:
	•	Run in bursts
	•	Can tolerate interruption
	•	Must stay within budget
Using EC2 Fleet:
	•	Architects define capacity targets
	•	Finance sets spending limits
	•	Operations monitors fleet health


Instance Weighting
Instance weighting allows Anyaero to:
	•	Define capacity in units
	•	Mix instance sizes
	•	Optimize cost per unit of performance
This prevents overprovisioning while meeting workload requirements.


Monitoring Fleet Events
As noted in the e-learning:
	•	EC2 Fleet emits events when capacity changes
	•	Notifications can be triggered
	•	Operations teams gain real-time visibility
This supports production-ready systems.


EC2 Fleet Security Considerations
	•	Use approved launch templates
	•	Restrict instance types
	•	Apply IAM roles consistently
	•	Monitor fleet changes
Automation increases efficiency and responsibility.


Operational Efficiency with AMIs
Amazon Machine Images (AMIs) define:
	•	Operating system
	•	Installed software
	•	Configuration settings
AMIs allow Anyaero to:
	•	Launch instances faster
	•	Enforce consistency
	•	Reduce configuration drift
AMI documentation:
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html


Week 1 Key Takeaways
By the end of this week, you should be able to:
	•	Explain what an EC2 instance is
	•	Describe the EC2 lifecycle
	•	Understand how user data automates configuration
	•	Explain how EC2 Fleet scales compute
	•	Recognize why security is foundational from day one


Looking Ahead
Next week focuses on:
	•	Identity and Access Management (IAM)
	•	Authentication versus authorization
	•	Designing secure cloud environments
You will build directly on the compute foundation established this week.
