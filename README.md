<!-- ========================================================= -->
<!--                        HERO                               -->
<!-- ========================================================= -->

<p align="center">
  <img
    src="https://capsule-render.vercel.app/api?type=waving&color=0:050505,45:0f2027,75:203a43,100:2c5364&height=240&section=header&text=Bhavesh%20Gupta&fontSize=58&fontColor=ffffff&animation=fadeIn&fontAlignY=38"
    width="100%"
  />
</p>

<p align="center">
  <img
    src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&size=25&duration=2800&pause=700&color=00F7FF&center=true&vCenter=true&width=850&lines=Software+Development+Engineer;Java+%7C+Spring+Boot+%7C+React;Full+Stack+Developer;Microservices+%26+REST+APIs;Agentic+AI+%26+Automation;600%2B+LeetCode+Problems+Solved"
  />
</p>

<p align="center">
  <a href="https://github.com/bhaveshgupta1811">
    <img src="https://komarev.com/ghpvc/?username=bhaveshgupta1811&label=Profile%20Views&color=0e75b6&style=flat" />
  </a>
  <a href="https://github.com/bhaveshgupta1811?tab=followers">
    <img src="https://img.shields.io/github/followers/bhaveshgupta1811?label=Followers&style=flat&logo=github" />
  </a>
  <a href="https://github.com/bhaveshgupta1811?tab=repositories">
    <img src="https://img.shields.io/badge/Repositories-Explore-203a43?style=flat&logo=github" />
  </a>
</p>

---

# `whoami`

```java
public class Engineer {

    String name       = "Bhavesh Gupta";
    String role       = "Software Development Engineer";
    String company    = "Verzat Technology Private Limited";
    String philosophy = "Secure it, then scale it.";

    String[] focus = {
        "Spring Boot Microservices",
        "REST API Design",
        "Security, RBAC & Authorization",
        "React + TypeScript",
        "Agentic AI Workflows"
    };
}
```

> I build backend systems where **who can do what** is as carefully designed as **what the system does**.

Full Stack Java Developer working on enterprise file management and collaboration
platforms — secure storage, sharing, permissions, approval workflows and audit
trails — backed by Spring Boot, PostgreSQL and AWS S3.

### Current interests

```text
┌────────────────────────────────────────────────────────────┐
│                                                            │
│  ☕ Java              Spring Boot / JPA                    │
│  🔐 Security          RBAC / JWT / AuthZ                   │
│  🧩 Microservices     REST API Design                      │
│  🗄️  Databases         PostgreSQL / MySQL                   │
│  ⚛️  Frontend          React / TypeScript                   │
│  🤖 AI Automation     n8n / vLLM / LLM APIs                │
│                                                            │
└────────────────────────────────────────────────────────────┘
```

---

# ⚙️ Engineering Philosophy

<details>
<summary><b>🔐 Security First</b></summary>

Authorization is not a filter you bolt on at the end — it is a layer that every request passes
through, and it has to be correct at each level.

```text
Request
    ↓
JWT Authentication
    ↓
Role / Permission Resolution
    ↓
Module-Level Access
    ↓
Resource Ownership Check
    ↓
Action
```

Things I actively design against:

* Privilege escalation through overlooked endpoints
* Cross-tenant data access
* Trusting client-supplied IDs without an ownership check
* Permissions granted implicitly by sharing or approval flows

</details>

<details>
<summary><b>⚡ Performance</b></summary>

I care about what the database actually does, not just what the code looks like:

* N+1 query problems (solved in Airgo with `JOIN FETCH`)
* Fetch strategies — lazy vs eager
* Index usage and query plans
* Payload size and serialization overhead
* Connection pooling
* Caching boundaries

</details>

<details>
<summary><b>🧩 Architecture</b></summary>

Layers that are understandable, testable and replaceable on their own.

```text
   React SPA
       │
       ▼
┌──────────────┐
│  Controller  │   REST endpoints, validation
└──────┬───────┘
       ▼
┌──────────────┐
│   Security   │   JWT filter, roles, permissions
└──────┬───────┘
       ▼
┌──────────────┐
│   Service    │   Business logic, transactions
└──────┬───────┘
       ▼
┌──────────────┐
│  Repository  │   Spring Data JPA / Hibernate
└──────┬───────┘
       ▼
┌──────────────┐
│  PostgreSQL  │
└──────────────┘
```

</details>

---

# 🚀 Flagship Projects

## ✈️ Airgo

**Full-stack airline management system.**
[`github.com/Sunbeam-Bhavesh/Airgo`](https://github.com/Sunbeam-Bhavesh/Airgo)

```text
  React SPA + React Router
            │
            ▼
┌───────────────────────┐
│    Spring Security    │   role-based access
└───────────┬───────────┘
            ▼
┌───────────────────────┐
│    REST Controllers   │
└───────────┬───────────┘
            ▼
┌───────────────────────┐
│  Booking / Scheduling │
└───────────┬───────────┘
            ▼
┌───────────────────────┐
│   Hibernate (JPA)     │
└───────────┬───────────┘
            ▼
┌───────────────────────┐
│        MySQL          │
└───────────────────────┘
```

### Core concepts

* 🛫 Flight scheduling and seat booking
* 🔑 Role-based access via Spring Security + JWT
* 🧭 Single-page app with React Router
* 🐢 **N+1 query problem** found in booking retrieval
* 🚀 Fixed with `JOIN FETCH` in Hibernate — fewer round trips, faster responses
* 🧑‍💼 Separate admin operations surface

<details>
<summary><b>🧪 What the N+1 fix looked like</b></summary>

```text
Before                          After
──────                          ─────
SELECT bookings                 SELECT bookings
  → SELECT flight  (per row)      JOIN FETCH flight
  → SELECT user    (per row)      JOIN FETCH user
  → SELECT seat    (per row)      JOIN FETCH seat

1 + 3N queries                  1 query
```

</details>

**Stack:** Java • Spring Boot • Spring Security • JWT • React.js • MySQL • Tailwind CSS • Hibernate

---

## 🗂️ Enterprise File Management Platform

**Secure file storage, sharing and document lifecycle management.**

> Built at Verzat Technology — where most of my authorization work lives.

### Architecture

```text
      React + TypeScript
              │
              ▼
┌─────────────────────────┐
│   Auth  ·  JWT Filter   │
└────────────┬────────────┘
             ▼
┌─────────────────────────┐
│  Permission Resolution  │  roles · overrides · modules
└────────────┬────────────┘
             ▼
┌─────────────────────────┐
│   File / Folder Logic   │  share · approve · own
└──────┬───────────┬──────┘
       ▼           ▼
┌────────────┐ ┌────────────┐
│ PostgreSQL │ │   AWS S3   │
│  metadata  │ │   objects  │
└────────────┘ └────────────┘
```

### Core features

* 📁 Secure storage, sharing and version control
* 👁️ Document previews and lifecycle management
* 🎭 Role templates with user-specific permission overrides
* 🧱 Module-level access and ownership controls
* 🔍 Comprehensive audit logging and notifications
* ✅ Approval workflows for controlled access
* 🛡️ Privilege-escalation and cross-tenant issues identified and closed

**Stack:** Java • Spring Boot • Spring Security • JWT • JPA/Hibernate • React.js • TypeScript • PostgreSQL • AWS S3

---

## 🤖 Agentic AI & Migration Systems

**Automation pipelines and multi-platform data movement.**

```text
   n8n Orchestration
          │
    ┌─────┴─────┐
    ▼           ▼
LLM APIs    Self-hosted
Groq        vLLM + CUDA
OpenAI      (Ubuntu)
Google
    │           │
    └─────┬─────┘
          ▼
  Stable Diffusion
  Image Pipeline
```

* 🧠 Agentic AI workflows designed in **n8n**
* 🖼️ Automated image generation via **Stable Diffusion API**
* ⚙️ Local model serving with **vLLM on Ubuntu, CUDA-accelerated**
* 🔄 **15+ platform connectors** — AEM, AWS, Cloudinary, WordPress, Dropbox, Contentful, GCS
* 🔐 Credential-based authentication for full automated migrations

**Stack:** TypeScript • Python • n8n • vLLM • CUDA • Groq API • OpenAI API • REST APIs

---

# 🧠 What I Focus On

<details>
<summary><b>☕ Backend & APIs</b></summary>

* Spring Boot
* Microservice boundaries
* REST API design
* Spring Data JPA / Hibernate
* Transaction management
* Exception handling
* DTO / entity separation
* JUnit + Mockito testing

</details>

<details>
<summary><b>🔐 Security & Authorization</b></summary>

* Spring Security filter chains
* JWT issuance and validation
* Role-based access control
* Granular permission models
* Role templates and per-user overrides
* Ownership and tenancy checks
* Approval and sharing workflows
* Audit logging

</details>

<details>
<summary><b>🗄️ Data & Persistence</b></summary>

* PostgreSQL / MySQL / MongoDB
* Schema and relationship design
* JPA mappings and fetch strategies
* Query optimization
* N+1 detection and elimination
* Indexing
* Migrations
* Object storage with AWS S3

</details>

<details>
<summary><b>⚛️ Frontend & Automation</b></summary>

* React.js + TypeScript
* Redux state management
* React Router
* Tailwind CSS / Material-UI
* REST API integration
* n8n workflow automation
* LLM API integration
* Local model deployment

</details>

---

# 🛠️ Technology Stack

## 🚨 Languages

<p>
  <img src="https://skillicons.dev/icons?i=java" height="48"/>
  <img src="https://skillicons.dev/icons?i=ts" height="48"/>
  <img src="https://skillicons.dev/icons?i=js" height="48"/>
  <img src="https://skillicons.dev/icons?i=python" height="48"/>
</p>

## ⚙️ Backend & Frameworks

<p>
  <img src="https://skillicons.dev/icons?i=spring" height="48"/>
  <img src="https://skillicons.dev/icons?i=hibernate" height="48"/>
  <img src="https://skillicons.dev/icons?i=maven" height="48"/>
  <img src="https://skillicons.dev/icons?i=nodejs" height="48"/>
</p>

## 🎨 Frontend

<p>
  <img src="https://skillicons.dev/icons?i=react" height="48"/>
  <img src="https://skillicons.dev/icons?i=redux" height="48"/>
  <img src="https://skillicons.dev/icons?i=tailwind" height="48"/>
  <img src="https://skillicons.dev/icons?i=materialui" height="48"/>
</p>

## 🗄️ Databases & Storage

<p>
  <img src="https://skillicons.dev/icons?i=postgres" height="48"/>
  <img src="https://skillicons.dev/icons?i=mysql" height="48"/>
  <img src="https://skillicons.dev/icons?i=mongodb" height="48"/>
</p>

## 🧰 Infrastructure

<p>
  <img src="https://skillicons.dev/icons?i=aws" height="48"/>
  <img src="https://skillicons.dev/icons?i=docker" height="48"/>
  <img src="https://skillicons.dev/icons?i=linux" height="48"/>
  <img src="https://skillicons.dev/icons?i=githubactions" height="48"/>
  <img src="https://skillicons.dev/icons?i=git" height="48"/>
</p>

---

# 💼 Experience

```text
┌──────────────────────────────────────────────────────────────┐
│  Software Developer                       Jul 2026 – Present │
│  Verzat Technology Private Limited            Pune, MH       │
│  → Enterprise file management & collaboration platform       │
│  → RBAC, granular permissions, secure sharing workflows      │
│  → Audit logging, notifications, approval workflows          │
├──────────────────────────────────────────────────────────────┤
│  SDE                                     Dec 2025 – Jun 2026 │
│  NdSoftTech Solution                          Pune, MH       │
│  → Agentic AI workflows with n8n + vLLM on CUDA              │
│  → Multi-platform asset migration app, 15+ connectors        │
├──────────────────────────────────────────────────────────────┤
│  Software Developer Intern                May 2024 – Oct 2024│
│  B.N. Consultant                          Gwalior, MP        │
│  → React.js + Material-UI interfaces                         │
│  → REST API integration with Node.js services                │
└──────────────────────────────────────────────────────────────┘
```

---

# 🎓 Education & Certifications

**B.Tech, Computer Science** — Lakshmi Narain College of Technology, Bhopal
`2021 – 2024` · CGPA **8.6**

<details>
<summary><b>📜 Certifications & Achievements</b></summary>

<br>

| | |
|---|---|
| 🎯 | **CDAC** (2025) — hands-on training in Java Full Stack Development |
| 🤖 | **Elements of AI** and **Agentic AI** — MinnaLearn Academy (2026) |
| ☕ | **Certified Java Developer** — HackerRank (2025) |
| 👕 | **600+ LeetCode problems** solved — earned the LeetCode T-shirt (2025) |

</details>

---

# 📊 GitHub Analytics

<p align="center">
  <img
    src="https://github-readme-stats.vercel.app/api?username=bhaveshgupta1811&show_icons=true&theme=tokyonight&hide_border=true&rank_icon=github"
    height="180"
  />
  <img
    src="https://github-readme-stats.vercel.app/api/top-langs/?username=bhaveshgupta1811&layout=compact&theme=tokyonight&hide_border=true"
    height="180"
  />
</p>

<p align="center">
  <img
    src="https://streak-stats.demolab.com/?user=bhaveshgupta1811&theme=tokyonight&hide_border=true"
    width="70%"
  />
</p>

---

# 🐍 Contribution Activity

<p align="center">
  <picture>
    <source
      media="(prefers-color-scheme: dark)"
      srcset="https://raw.githubusercontent.com/bhaveshgupta1811/bhaveshgupta1811/output/github-contribution-grid-snake-dark.svg"
    />
    <img
      src="https://raw.githubusercontent.com/bhaveshgupta1811/bhaveshgupta1811/output/github-contribution-grid-snake.svg"
      alt="GitHub contribution snake"
    />
  </picture>
</p>

---

# 📈 GitHub Activity

<details>
<summary><b>📅 Contribution Graph</b></summary>

<br>

<p align="center">
  <img
    src="https://github-readme-activity-graph.vercel.app/graph?username=bhaveshgupta1811&theme=tokyo-night&hide_border=true"
    width="100%"
  />
</p>

</details>

---

# 🧪 Currently Building

```text
┌───────────────────────────────────────────────────────┐
│                   CURRENT LAB                         │
├───────────────────────────────────────────────────────┤
│                                                       │
│  ☕ Spring Boot Microservices                         │
│  🔐 Authorization & RBAC Design                       │
│  🗄️  PostgreSQL Query Optimization                     │
│  ☁️  AWS S3 & Cloud Deployment                         │
│  🤖 Agentic AI Workflows                              │
│  🧩 System Design                                     │
│                                                       │
└───────────────────────────────────────────────────────┘
```

---

# 🧰 Developer Environment

```bash
$ neofetch

OS          → Windows 11
Shell       → PowerShell / WSL Ubuntu
Editor      → IntelliJ IDEA / VS Code
Primary     → Java
Backend     → Spring Boot
Frontend    → React + TypeScript
Database    → PostgreSQL / MySQL
Container   → Docker
Cloud       → AWS (EC2, S3)
```

---

# 🎯 Learning Goals

> Where I'm putting my time — direction, not a scoreboard.

```text
[████████████████████] Backend & Spring Boot

[██████████████████░░] API Security & RBAC

[████████████████░░░░] Full Stack (React + TS)

[██████████████░░░░░░] System Design

[████████████░░░░░░░░] Cloud & DevOps
```

> Build it. Break it. Secure it. Improve it.

---

# 🔗 Connect With Me

<p align="center">

  <a href="https://github.com/bhaveshgupta1811">
    <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white"/>
  </a>

  <a href="https://www.linkedin.com/in/bhaveshgupta1811">
    <img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white"/>
  </a>

  <a href="mailto:bhaveshgupta13524@gmail.com">
    <img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white"/>
  </a>

  <a href="https://leetcode.com/u/bhaveshgupta1811">
    <img src="https://img.shields.io/badge/LeetCode-FFA116?style=for-the-badge&logo=leetcode&logoColor=black"/>
  </a>

</p>

---

<p align="center">

### `mvn spring-boot:run`

**Building backend systems that are secure by design.**

<br>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:2c5364,50:203a43,100:0f2027&height=120&section=footer"/>

</p>
