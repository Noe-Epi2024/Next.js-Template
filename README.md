# 🧱 Next.js Architecture Templates

Welcome to this repository of **Next.js architecture templates**, designed for real-world full-stack applications.  
Each template follows a structured and scalable approach, depending on your project’s complexity, goals, and team needs.

---

## 📦 Available Templates

### 1. **FSD Architecture** (Feature-Sliced Design)

A modular, function-based architecture suitable for most full-stack web apps.

- ✅ Feature-driven structure
- ✅ No OOP — purely functional
- ✅ Lightweight, easy to scale
- ✅ Good for dashboards, SaaS, admin panels

📁 Folder: `FSD-Architecture/`

---

### 2. **DDD + OOP Architecture**

Strictly organized using **Domain-Driven Design** and **Object-Oriented Programming**, perfect for complex business logic and high modularity.

- ✅ Domain isolation
- ✅ Uses classes, services, entities, ports
- ✅ Ideal for enterprise-scale or B2B apps
- ✅ Aligned with clean architecture principles

📁 Folder: `DDD-OOP-Architecture/`

---

### 3. **Layered Architecture**

A simple, clean, and functional architecture structured by **technical layers**: UI, controller, service, and data access.  
Ideal for small to medium projects or teams not requiring full DDD/OOP overhead.

- ✅ Functional and minimal
- ✅ No class-based OOP
- ✅ Clear technical separation
- ✅ Easy to onboard and extend

📁 Folder: `Layered-Architecture/`

---

## ⚙️ Stack Used

- [x] **Next.js App Router**
- [x] **TypeScript**
- [x] **Tailwind CSS**
- [x] **Zod** for validation
- [x] **Prisma** for database
- [x] **React Query** (FSD)

---

## ✨ How to Use

1. Clone this repo:
```bash
git clone https://github.com/Noe-Epi2024/Next.js-Template.git
```

2. Pick your desired template folder:
```bash
cd FSD-Architecture
# or
cd DDD-OOP-Architecture
# or
cd Layered-Architecture
```

3. Install dependencies and start the dev server:
```bash
npm install
npm run dev
```

---

## 🤝 Contribute

Feel free to fork, clone, and contribute your own improvements or variants!

---

## 📄 License

This repository is available under the MIT License.
