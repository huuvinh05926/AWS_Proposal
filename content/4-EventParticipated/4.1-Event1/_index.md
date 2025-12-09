---
title: "Event 1"
date: "2025-11-11"
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# 03/10/2025

# AWS GenAI Builder

**Speaker:** Toàn Huỳnh - Senior Specialist Solutions Architect

## AI-Driven Development Lifecycle (AI-DLC)

### Introduction to AI-DLC

- AI-DLC is not just a simple tool
- Evolution of AI in software development:
  - **2023:** Helping developers write code faster
  - **2024:** Generating larger pieces of code and answering faster
  - **2025:** Completing development tasks end-to-end with human in the loop
- AI should be used in a pair-programming model rather than working alone
- Developers are still the ones who review, validate, and own the code

### AI Disruption to Development

**Challenges when using AI:**

- Need to understand why AI is needed
- AI is becoming an indispensable tool in software development
- Software quality is still checked and ensured by developers
- When using AI to scale large projects, many issues can arise:
  - Generating lots of code but unable to control quality
  - May have to start over if not well controlled
  - Difficult to track what AI is doing
- Should not "single-shot" for all cases
- When viewing AI as a companion to solve problems together, most problems will be solved better

### Working with AI-DLC

**Important Principles:**

- Developers must make the final decisions, not let AI decide on its own
- Developers need to synthesize information, generate ideas, and communicate with AI
- AI will help define tasks, avoiding loss of control
- Must provide sufficient information and ideas to AI
- Development based on analyzing and understanding problems with AI support

**Workflow:**

![How does AI-DLC work?](/images/4-EventParticipated/BC23F17A-C590-4D04-9560-B9CBF09A0B87.jpeg)

![AI-Driven Development Lifecycle](/images/4-EventParticipated/0B608674-73F3-4495-A0F4-4DD70F17C3B8.jpeg)

**Implementation Steps:**

1. Put the problem into AI to generate user stories
2. Scope down and ask questions about the app you want to build
3. Ask AI to group important units for end users
4. Implement each unit, breaking them into small projects

### Mob Elaboration & Construction

**Mob Elaboration:** Multiple people working together on one computer and sharing output with each other

![Construction: Mob Construction](/images/4-EventParticipated/C96E172C-D36A-451B-A402-8EB2DF5B8486.jpeg)

**Note:** Starting from a simple requirement through each unit to reach the final result. If Backend and Frontend want to work together according to this model, they need at least one common track to interact with each other.

### Workflow with AI

**Standard Development Workflow:**

![AI-DLC Standard Development Workflow](/images/4-EventParticipated/67A368F8-5389-4E7E-AFE1-329DEE2B1255.jpeg)

- Currently we use AI to compile code
- This model cannot be broken down, so for large projects, Amazon Q should be used

**Prompt Template:**

![Prompt Template](/images/4-EventParticipated/96F29C72-912C-4427-9774-F1381D6A8FA4.jpeg)

**How to write effective prompts:**

- Must clearly specify what AI does, what Product Manager does
- Must indicate the role to solve the problem
- When wanting to do a project, ask AI to plan first
- Can divide into multiple options and do gradually to avoid overload

**Best Practices:**

- Store results in Markdown files and use them for subsequent tasks
- Must compile multiple times, upload to MD and define clearly
- Put MD files into the project so AI can read and add ideas
- Have checkmarks in the plan file to note what has been done

![Each Stage](/images/4-EventParticipated/C651E529-5F58-47C4-8FF8-1A068DAAB023.jpeg)

![Key Workflow Features](/images/4-EventParticipated/A432E852-C014-4130-B437-9BEE50B1296C.jpeg)

![Steps in AI-DLC](/images/4-EventParticipated/4A1C23B0-123E-47AB-A5AE-A71CBE94A764.jpeg)

### Important Principles

**Never Single-shot a Multi-step Problem:**

![Never Single-shot](/images/4-EventParticipated/2B3CD950-C4EF-4601-B9C7-3B69F28F104E.jpeg)

- Leverage AI for standardized work
- Do thinking work yourself
- Must review regularly, don't delegate tasks completely to AI

**Maximize Semantics per Token:**

![Maximize Semantics per Token](/images/4-EventParticipated/6CAE446D-4245-4D9D-9807-D12D4FDD74F9.jpeg)

- Code is easy to over-context, so must build into Markdown files to avoid going wrong

![Code Ownership](/images/4-EventParticipated/BA4CF1EE-98AA-466F-B3F7-C8E87EF7E32C.jpeg)

**Conclusion:** You are still responsible for the final code.

---

## Kiro - The AI IDE for Prototype to Production

**Speaker:** My Nguyễn - Senior Prototyping Architect

### Introduction to Kiro

Kiro is an AI IDE specifically designed to quickly and efficiently convert from prototype to production.

**Differences between Kiro and VSCode:**

![Kiro vs VSCode](/images/4-EventParticipated/48757C46-B986-4A99-9CC1-B4048BB2E690.jpeg)

### Key Features

**Power, Flexibility, and Security:**

Kiro provides a powerful combination of:

- **Power:** Strong processing capability with AI support
- **Flexibility:** Flexible in developing from prototype to production
- **Security:** Ensuring safety and security during the development process

#### Identifying the drawbacks of legacy application architecture

- Long product release cycles → Lost revenue/missed opportunities
- Inefficient operations → Reduced productivity, higher costs
- Non-compliance with security regulations → Security breaches, loss of reputation

#### Transitioning to modern application architecture – Microservices

Migrating to a modular system — each function is an **independent service** communicating via **events**, built on three core pillars:

- **Queue Management**: Handle asynchronous tasks
- **Caching Strategy**: Optimize performance
- **Message Handling**: Flexible inter-service communication

#### Domain-Driven Design (DDD)

- **Four-step method**: Identify domain events → arrange timeline → identify actors → define bounded contexts
- **Bookstore case study**: Demonstrates real-world DDD application
- **Context mapping**: 7 patterns for integrating bounded contexts

#### Event-Driven Architecture

- **3 integration patterns**: Publish/Subscribe, Point-to-point, Streaming
- **Benefits**: Loose coupling, scalability, resilience
- **Sync vs async comparison**: Understanding the trade-offs

#### Compute Evolution

- **Shared Responsibility Model**: EC2 → ECS → Fargate → Lambda
- **Serverless benefits**: No server management, auto-scaling, pay-for-value
- **Functions vs Containers**: Criteria for appropriate choice

#### Amazon Q Developer

- **SDLC automation**: From planning to maintenance
- **Code transformation**: Java upgrade, .NET modernization
- **AWS Transform agents**: VMware, Mainframe, .NET migration

### Key Takeaways

#### Design Mindset

- **Business-first approach**: Always start from the business domain, not the technology
- **Ubiquitous language**: Importance of a shared vocabulary between business and tech teams
- **Bounded contexts**: Identifying and managing complexity in large systems

#### Technical Architecture

- **Event storming technique**: Practical method for modeling business processes
- Use **event-driven communication** instead of synchronous calls
- **Integration patterns**: When to use sync, async, pub/sub, streaming
- **Compute spectrum**: Criteria for choosing between VM, containers, and serverless

#### Modernization Strategy

- **Phased approach**: No rushing — follow a clear roadmap
- **7Rs framework**: Multiple modernization paths depending on the application
- **ROI measurement**: Cost reduction + business agility

### Applying to Work

- **Apply DDD** to current projects: Event storming sessions with business teams
- **Refactor microservices**: Use bounded contexts to define service boundaries
- **Implement event-driven patterns**: Replace some sync calls with async messaging
- **Adopt serverless**: Pilot AWS Lambda for suitable use cases
- **Try Amazon Q Developer**: Integrate into the dev workflow to boost productivity

### Event Experience

Attending the **“GenAI-powered App-DB Modernization”** workshop was extremely valuable, giving me a comprehensive view of modernizing applications and databases using advanced methods and tools. Key experiences included:

#### Learning from highly skilled speakers

- Experts from AWS and major tech organizations shared **best practices** in modern application design.
- Through real-world case studies, I gained a deeper understanding of applying **DDD** and **Event-Driven Architecture** to large projects.

#### Hands-on technical exposure

- Participating in **event storming** sessions helped me visualize how to **model business processes** into domain events.
- Learned how to **split microservices** and define **bounded contexts** to manage large-system complexity.
- Understood trade-offs between **synchronous and asynchronous communication** and integration patterns like **pub/sub, point-to-point, streaming**.

#### Leveraging modern tools

- Explored **Amazon Q Developer**, an AI tool for SDLC support from planning to maintenance.
- Learned to **automate code transformation** and pilot serverless with **AWS Lambda** to improve productivity.

#### Networking and discussions

- The workshop offered opportunities to exchange ideas with experts, peers, and business teams, enhancing the **ubiquitous language** between business and tech.
- Real-world examples reinforced the importance of the **business-first approach** rather than focusing solely on technology.

#### Lessons learned

- Applying DDD and event-driven patterns reduces **coupling** while improving **scalability** and **resilience**.
- Modernization requires a **phased approach** with **ROI measurement**; rushing the process can be risky.
- AI tools like Amazon Q Developer can significantly **boost productivity** when integrated into the current workflow.

#### Some event photos

_Add your event photos here_

> Overall, the event not only provided technical knowledge but also helped me reshape my thinking about application design, system modernization, and cross-team collaboration.
