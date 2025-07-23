# 🛡️ middlewares/

This folder contains **custom middleware functions** used to intercept, modify, or guard requests before they hit your routes or controllers.

These can include authentication, role checking, rate limiting, logging, etc.

---

## 📁 Recommended structure

```
middlewares/
├── withAuth.ts          # Enforces authentication
├── withRole.ts          # Enforces user role-based access
├── withRateLimit.ts     # Applies rate limiting (optional)
```

---

## ✅ Best practices

| ✅ Do                                       | ❌ Don't                                 |
|--------------------------------------------|------------------------------------------|
| Keep middlewares modular and composable    | Mix them directly inside controllers     |
| Reuse logic across multiple routes         | Hardcode checks inside API handlers      |
| Handle NextRequest and NextResponse cleanly| Perform side effects outside middleware  |
| Name with clear intent (`withX`)           | Use vague names like `check.ts`          |

---

## ✨ Naming conventions

- `withAuth.ts` – protects routes from unauthenticated access
- `withRole.ts` – restricts access based on user roles
- `withLogger.ts` – adds request logging functionality

---

## 🧠 Example

```ts
// middlewares/withAuth.ts

import { NextRequest, NextResponse } from 'next/server';

export function withAuth(handler: (req: NextRequest) => Promise<Response>) {
  return async (req: NextRequest) => {
    const token = req.cookies.get('token');
    if (!token) {
      return NextResponse.json({ message: 'Unauthorized' }, { status: 401 });
    }

    return handler(req);
  };
}
```