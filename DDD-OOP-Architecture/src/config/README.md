# ⚙️ config/

This folder contains **application-wide configuration** that is **environment-agnostic** and **centralized**, such as:

- API endpoints
- Feature flags
- Global constants
- Third-party service settings (without secrets)
- App metadata (e.g., app name, version, locale defaults)

It acts as the **single source of truth** for all non-secret configuration values.  
Secrets like database passwords or API keys **must** go into `.env` files, not here.

---

## 📁 Recommended structure

```
config/
├── app.config.ts       # Global app settings (name, version, default locale)
├── api.config.ts       # API endpoints and related constants
├── feature-flags.ts    # Enable/disable experimental features
├── theme.config.ts     # Theme tokens or layout constants
├── index.ts            # Barrel file for exporting configs
```

---

## ✅ Best practices

| ✅ Do                                                              | ❌ Don't                                      |
|-------------------------------------------------------------------|-----------------------------------------------|
| Centralize non-sensitive config in this folder                    | Spread config values randomly across the app  |
| Keep secrets in `.env` and load them via env parsing library      | Hardcode sensitive credentials here           |
| Export typed config objects for better DX                         | Use untyped `any` objects for config          |
| Document what each config file is responsible for                 | Leave ambiguous or unused config files        |
| Group related config into separate files (e.g., `api.config.ts`)  | Dump all settings into a single large file    |

---

## ✨ Naming conventions

- `*.config.ts` → Configuration files (`app.config.ts`, `api.config.ts`, `theme.config.ts`)
- `feature-flags.ts` → Toggleable features (boolean flags)
- `index.ts` → Barrel export of all configs