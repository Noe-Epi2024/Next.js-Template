# 🏗️ infrastructure/ (clients domain)

This folder contains the **technical implementations** that support the `clients` domain.
It provides concrete classes for repositories, mappers, and external service integrations, based on interfaces defined in the domain or application layers.

Infrastructure code is responsible for **connecting the domain to real-world technologies** like databases, APIs, storage, and queues.

---

## ✅ Best practices

- Implement only what is defined in the domain/application layer interfaces
- Keep third-party dependencies isolated here
- Do **not** place business logic in infrastructure
- Use mappers to transform between domain models and persistence/DTO formats

---
