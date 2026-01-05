## Building Cloud Foundations at Anyaero Aerospace
---
## Welcome to Anyaero :airplane:
**Anyaero** is a forward-thinking aerospace company designing, testing, and operating next-generation aircraft and flight systems. Like most modern engineering organizations, Anyaero relies heavily on cloud computing to:
Process flight telemetry
Run simulations and analytics
Host internal and external applications
Secure sensitive mission and business data
Scale systems on demand while controlling costs
This week, you’ll step into Anyaero’s cloud environment and begin learning how AWS services support real business and technical decisions.
---
## How Cloud Work Happens at Anyaero: Roles & Responsibilities
Cloud systems are never built by one person alone. At Anyaero, **business leaders and technical teams work together**, each with different priorities.
### Executive & Business Leadership Roles
| Role | What They Care About | Cloud Perspective |
|---|---|---|
| **CEO** | Business growth, speed, competitiveness | Cloud enables faster launches and innovation |
| **CFO** | Cost control, budgeting, ROI | Wants predictable spend and cost optimization |
| **CIO** | IT strategy, reliability, modernization | Oversees cloud adoption and architecture standards |
| **CISO** | Security, compliance, risk management | Requires encryption, access controls, and secure design |
---
### Technical & Operational Roles
| Role | Primary Focus | AWS Involvement |
|---|---|---|
| **Cloud Architect** | System design | Chooses between EC2, Lambda, RDS, networking models |
| **Cloud Engineer** | Implementation | Builds EC2 instances, fleets, and Lambda functions |
| **DevOps / Platform Engineer** | Automation & scaling | Uses EC2 Fleet, launch templates, monitoring |
| **Security Engineer** | Protection & compliance | Enforces IAM, encryption, network security |
| **Network Engineer** | Connectivity | Designs VPCs, subnets, VPNs |
| **Operations / SRE** | Reliability & monitoring | Manages EC2 lifecycle, scaling, alerts |
| **Application Developer** | Code & features | Builds apps that run on EC2 or Lambda |
| **Cloud Support / Ops Associate** | Troubleshooting | Diagnoses instance, networking, and access issues |
**Key takeaway:** 
Cloud services exist to support *both* business outcomes and technical execution.
---
## The Big Picture: Core Cloud Building Blocks
Every AWS architecture at Anyaero is built from the same foundational layers:
┌─────────────────────────┐
│        Compute          │  → Run code (EC2, Lambda)
├─────────────────────────┤
│          Data           │  → Store information (RDS)
├─────────────────────────┤
│       Networking        │  → Connect systems (VPC, VPN)
├─────────────────────────┤
│        Security         │  → Protect everything (IAM, TLS)
└─────────────────────────┘
This week introduces you to each of these pillars.
---
# :one: Compute Foundations: Amazon EC2
### What Is Amazon EC2?
**Amazon Elastic Compute Cloud (EC2)** provides virtual servers in the cloud. These servers behave much like on-premises machines, but with far greater flexibility and scalability.
Official documentation: 
https://docs.aws.amazon.com/ec2/
---
### Why Anyaero Uses EC2
EC2 is used when Anyaero needs:
Full control over operating systems
Custom software installations
Long-running applications
Predictable performance
Typical use cases include:
Mission planning portals
Internal engineering tools
Data processing workloads
---
### Understanding the EC2 Lifecycle
An EC2 instance moves through states such as:
**Pending**
**Running**
**Stopping**
**Stopped**
**Terminated**
Operations teams rely on this lifecycle knowledge to:
Control costs
Recover from failures
Perform maintenance safely
---
### EC2 Security Considerations
Security is never optional at Anyaero:
Use **IAM roles** instead of static credentials 
Restrict access using **security groups**
Patch operating systems regularly
Never expose sensitive services publicly unless required
EC2 security overview: 
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security.html
---
# :two: Scaling Compute: Amazon EC2 Fleet
### What Is EC2 Fleet?
**EC2 Fleet** allows Anyaero to launch and manage **groups of EC2 instances** using a single request. It can mix:
On-Demand Instances
Spot Instances
Reserved Instances
Official documentation: 
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-fleet.html
---
### Business Scenario: Cost-Aware Scaling at Anyaero
Anyaero runs compute-heavy flight simulations that:
Run in bursts
Can tolerate interruptions
Must stay within budget
To meet these needs:
Architects design an EC2 Fleet
Finance approves Spot usage for cost savings
Operations monitors fleet health
As you may have seen in the e-learning, EC2 Fleet enables:
Instance weighting
Allocation strategies
Automatic capacity maintenance
---
### EC2 Fleet Best Practices
Mix instance types and Availability Zones
Use **instance weighting** for performance-based scaling
Set **maximum price limits** to control spend
Monitor fleet events automatically
---
### EC2 Fleet Security Considerations
Fleets use **launch templates** with approved settings
Security groups enforce least privilege
Fleet events can trigger alerts for operations teams
---
# :three: Serverless Compute: AWS Lambda
### What Does “Serverless” Mean?
Serverless means **you don’t manage servers** — AWS does.
With **AWS Lambda**, Anyaero runs code:
Only when needed
Automatically scaled
Billed per execution
Official documentation: 
https://docs.aws.amazon.com/lambda/latest/dg/welcome.html
---
### When Anyaero Uses Lambda
Lambda is ideal for:
Event-driven processing
Short-running tasks
Automation and integration
Examples:
Processing telemetry events
Responding to system changes
Backend APIs
---
### Lambda Best Practices
https://docs.aws.amazon.com/lambda/latest/dg/best-practices.html
Keep functions small and focused
Tune memory and timeout settings
Use environment variables
Design for retries
---
### Lambda Security Considerations
Enforce least-privilege IAM roles
Never embed secrets in code
Encrypt all data in transit
Lambda security overview: 
https://docs.aws.amazon.com/lambda/latest/dg/security.html
---
# :four: Data Foundations: Relational Databases with Amazon RDS
### What Is Amazon RDS?
**Amazon Relational Database Service (RDS)** is a managed service for relational databases such as:
MySQL
PostgreSQL
MariaDB
SQL Server
Oracle
Official documentation: 
https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html
---
### Why Anyaero Uses RDS
Relational databases are used when data must be:
Structured
Consistent
Queryable with SQL
Examples include:
Mission metadata
Flight summaries
Operational records
---
### RDS Best Practices
https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_BestPractices.html
Enable automated backups
Use Multi-AZ for production
Keep databases in private subnets
---
### RDS Security Considerations
Encrypt data at rest and in transit
Restrict access via security groups
Store credentials securely
RDS security documentation: 
https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.Security.html
---
# :five: Networking & Connectivity
### Amazon VPC Basics
All AWS resources live inside a **Virtual Private Cloud (VPC)**.
Official documentation: 
https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html
---
### Connectivity Options at Anyaero
| Option | Use Case |
|---|---|
| Internet Gateway | Public access |
| Site-to-Site VPN | Secure on-premises connection |
| Client VPN | Remote user access |
| Direct Connect | Dedicated private connectivity |
---
### Networking Security Considerations
Use private subnets for sensitive systems
Limit inbound traffic
Monitor traffic with logs
VPC security best practices: 
https://docs.aws.amazon.com/vpc/latest/userguide/vpc-security-best-practices.html
---
# :six: Encryption in Transit: A Non-Negotiable Standard
### What Is Encryption in Transit?
Encryption in transit protects data **while it is moving** between systems using TLS.
Official overview: 
https://docs.aws.amazon.com/security/latest/userguide/encryption.html
---
### Where Anyaero Enforces Encryption
User → AWS Console (HTTPS)
Application → Database (TLS)
On-premises → AWS (VPN/IPSec)
Service → Service communication
---
## Week 1 Key Takeaways
By the end of this week, you should be able to:
Explain how business and technical roles influence cloud decisions
Describe when to use EC2, EC2 Fleet, Lambda, and RDS
Understand how AWS networking connects systems securely
Explain why security and encryption are foundational, not optional
---
## Looking Ahead
Next week, you’ll go deeper into:
Identity and Access Management (IAM)
Authentication vs authorization
Designing for least privilege
Secure cloud governance
