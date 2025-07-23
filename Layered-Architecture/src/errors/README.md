# ❌ errors/

This folder contains **custom error classes or helpers** to standardize how errors are thrown and handled throughout the application.

Use this folder to define reusable error types and message formatters.

---

## 📁 Recommended structure

```
errors/
├── custom.ts            # Custom error classes (e.g., UnauthorizedError)
├── errorResponse.ts     # Formats error messages into HTTP responses
```

---

## ✅ Best practices

| ✅ Do                                      | ❌ Don't                                 |
|-------------------------------------------|------------------------------------------|
| Create reusable error classes             | Throw raw strings everywhere             |
| Group domain-specific errors (optional)   | Mix HTTP logic with logic errors         |
| Format errors for API responses           | Let Next.js expose default error stack   |
| Use consistent naming and status codes    | Return different formats everywhere      |

---

## ✨ Naming conventions

- `UnauthorizedError` – for 401 errors
- `NotFoundError` – for 404s
- `BadRequestError` – for validation failures
- `formatErrorResponse()` – to structure API errors

---

## 🧠 Example

```ts
// errors/custom.ts

export class UnauthorizedError extends Error {
  status = 401;
  constructor(message = 'Unauthorized') {
    super(message);
    this.name = 'UnauthorizedError';
  }
}
```

```ts
// errors/errorResponse.ts

export function formatErrorResponse(error: unknown) {
  if (error instanceof Error && 'status' in error) {
    return {
      status: (error as any).status,
      message: error.message,
    };
  }

  return {
    status: 500,
    message: 'Internal Server Error',
  };
}
```