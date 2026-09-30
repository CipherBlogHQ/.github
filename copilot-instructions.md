# CipherBlog — GitHub Copilot Engineering Instructions

## 1. Product Identity

CipherBlog is a lightweight, open-source, developer-first, modular, API-first
content platform built with modern .NET.

It is designed to support:

- Blogs
- Websites
- Content publishing
- Headless applications
- Mobile applications through APIs
- Custom digital experiences
- Extensible modules
- Configurable workflows
- Event-driven capabilities
- Real-time experiences
- Integrations

CipherBlog is NOT intended to be a WordPress clone.

Core product principle:

> Keep the core lightweight. Make capabilities modular, composable, extensible,
> configurable, and easy for developers to integrate.

---

# 2. Source of Truth

Before implementing functionality, inspect these documents when they exist:

- `/docs/product/PRODUCT-VISION.md`
- `/docs/product/PRD.md`
- `/docs/product/MVP-SCOPE.md`
- `/docs/architecture/ARCHITECTURE.md`
- `/docs/architecture/APPLICATION-FLOW.md`
- `/docs/architecture/MODULES.md`
- `/docs/decisions/DECISIONS.md`
- `/docs/roadmap/ROADMAP.md`

Repository code is also a source of truth.

If documentation and implementation disagree:

1. Do not silently choose one.
2. Identify the conflict.
3. Explain the impact.
4. Ask for a decision or create a clearly marked TODO.

Never invent product behavior.

---

# 3. Current Product Stage

CipherBlog is being developed incrementally.

Do not assume that future capabilities are already implemented.

Clearly distinguish:

- Implemented
- Planned
- Experimental
- TODO
- Future

Do not describe planned functionality as completed functionality.

---

# 4. MVP Philosophy

The MVP must remain lightweight.

Prefer:

- Modular monolith
- Simple deployment
- PostgreSQL
- ASP.NET Core
- REST APIs
- In-process events
- Background services where necessary
- SignalR only where real-time behavior provides clear value
- Local/file storage abstraction with future cloud providers
- Simple configuration
- Docker-based development

Do NOT introduce infrastructure such as:

- Microservices
- Kafka
- RabbitMQ
- Redis
- Elasticsearch
- Kubernetes
- Service mesh

unless explicitly approved by the product/architecture decision records.

Avoid solving future scale problems before they exist.

---

# 5. Technology Baseline

Use the repository's pinned versions as the authoritative versions.

Target stack:

- .NET 10
- C#
- ASP.NET Core
- Entity Framework Core
- PostgreSQL
- ASP.NET Core Identity
- Blazor / Razor Components where applicable
- SignalR where applicable
- OpenAPI
- Docker
- GitHub Actions
- xUnit for testing

Do not add third-party dependencies when the .NET platform already provides
a suitable capability.

Before adding a package:

1. Explain why it is required.
2. Check whether the existing stack already solves the problem.
3. Consider security, maintenance, licensing, size, and transitive dependencies.

---

# 6. Architecture

Use a modular monolith as the initial architecture.

Preferred logical boundaries:

```text
Presentation
    |
API / Web
    |
Application
    |
Domain
    |
Infrastructure
