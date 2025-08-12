# 🔌 ports/http/ (clients domain)

This folder contains **HTTP port handlers** for the `clients` domain.  

An HTTP port is an **entry point** that adapts incoming HTTP requests (e.g., API routes, webhooks) into calls to the application layer.  
Its job is to **parse, validate, and forward** the request data to the relevant use case or application service,  
then format the response to send back to the client.

---

## 📁 Example

```
domains/clients/ports/http/
└── create-client.handler.ts
```

---

## ✅ Best practices

- Keep handlers **thin** — they should only handle request parsing, validation, and calling use cases.
- Use **DTOs and validation schemas** to ensure request payload integrity.
- Never implement business logic here — delegate it to the **application layer**.
- Catch and translate domain/application errors into appropriate HTTP responses.
- Follow consistent naming with the `*.handler.ts` suffix.
- Keep them **framework-agnostic** when possible, so they can be reused in different adapters (REST, GraphQL, etc.).

---

## 🧠 Example

```ts
export async function handleCreateClientRequest(client: CreateClientDto) {
  const validatedClient = parseOrThrow(client, CreateClientSchemaDto)

  const clientRepository = new PrismaClientRepository()

  const service = new CreateClientUseCase(clientRepository)

  const result = await service.execute(validatedClient)

  return { message: 'Client created successfully' }
}
```