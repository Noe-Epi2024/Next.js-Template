# 🔌 ports/ (clients domain)

This folder defines the **entry and exit points** for the `clients` domain.  
Ports specify **how the domain interacts with the outside world**, such as HTTP handlers, CLI commands, or messaging subscribers.

Ports only define **contracts and request/response handling** — the actual logic is delegated to the application layer.

---

## ✅ Best practices

- Keep ports **thin** — only parse/validate requests and call use cases
- Do **not** implement business logic here
- Keep ports **framework-agnostic** when possible
- Follow clear naming conventions (e.g., `*.handler.ts` for HTTP)

---
