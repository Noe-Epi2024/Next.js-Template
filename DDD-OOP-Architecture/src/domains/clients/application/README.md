# 🧠 application/ (clients domain)

This folder defines the **application layer** of the `clients` domain.  
It contains **use cases** and **application services** that orchestrate domain models, repositories, and other services to fulfill specific business processes.

The application layer coordinates the **flow of data** between the domain layer and external layers (e.g., API controllers, UI, infrastructure),  
but it does **not** contain UI logic or direct infrastructure code.

---

## ✅ Best practices

- Implement **use cases** that represent application-level operations (e.g., `createClient`, `updateClientEmail`).
- Keep business rules in the **domain layer**, not here.
- Use **dependency injection** to work with repository interfaces and services.
- Avoid direct calls to databases, APIs, or frameworks — delegate to the infrastructure layer.
- Keep methods simple, **orchestrating** actions rather than performing complex calculations.

---
