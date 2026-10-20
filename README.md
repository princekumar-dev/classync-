<div align="center">

# ClassSync

### College timetables, staff workload & campus insights — in one dashboard

[![React](https://img.shields.io/badge/React-18-61DAFB?style=flat-square&logo=react&logoColor=black)](https://react.dev)
[![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)](https://www.typescriptlang.org)
[![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white)](https://vitejs.dev)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=flat-square&logo=tailwindcss&logoColor=white)](https://tailwindcss.com)
[![shadcn/ui](https://img.shields.io/badge/shadcn-ui-000000?style=flat-square)](https://ui.shadcn.com)
[![Tests](https://img.shields.io/badge/Tests-Vitest-6E9F18?style=flat-square&logo=vitest&logoColor=white)](https://vitest.dev)

**[🔗 Live App](https://classync-nine.vercel.app)**

</div>

## 🎯 Overview

**ClassSync** is a department-level operations platform for colleges that puts **timetables, staff workload, room occupancy, feedback sentiment, and staff wellbeing** behind a single role-aware dashboard. Built for the three people who actually run a department:

- **HOD** — full department oversight
- **Staff** — their schedule, classes, and workload
- **Students** — their timetable and notifications

> 🧪 **This is a frontend prototype**: all data lives in [`src/lib/mock-data.ts`](src/lib/mock-data.ts) and auth is demo-only, so the whole flow is explorable without a backend. The data layer is isolated in one file — swapping in a real REST/GraphQL API is a contained change.

## ✨ Features

### 🗓️ Timetable & Classes
- Weekly timetable grid with per-slot details (`/timetable`)
- Class sections, subjects, attendance and notes entry points

### 👨‍🏫 Staff Management
- Staff directory with roles and departments (`/staff`)
- **Workload analysis** — weekly hours per staff member, visualized

### 📈 Analytics (`/analytics`)
- Feedback **sentiment trend** over time
- Workload distribution across staff
- **Room utilization** and occupancy rates

### 🧠 Burnout Monitor (`/burnout`)
- Staff wellness scoring with **high / medium / low risk** tiers
- Average score and at-a-glance risk cards

### 💬 Feedback & Occupancy
- Feedback entries with sentiment breakdown (`/feedback`)
- Live-style classroom **occupancy dashboard** (`/occupancy`)

### 🔔 Notifications
- Department-wide notification feed (`/notifications`)

### 🔐 Role-Based Demo Auth
- Pick a role at login — each role lands on its own dashboard experience (HOD / Staff / Student)

## 🗺️ Routes

| Route | Page |
|-------|------|
| `/` | Landing |
| `/dashboard` · `/classes` · `/subjects` · `/attendance` · `/notes` | Role dashboard |
| `/timetable` | Weekly timetable |
| `/staff` | Staff directory |
| `/analytics` | Sentiment, workload & space analytics |
| `/burnout` | Staff burnout monitor |
| `/feedback` | Feedback & sentiment |
| `/occupancy` | Room occupancy |
| `/notifications` | Notifications |
| `*` | 404 |

## 👥 Demo Accounts

Password is ignored in the demo — choose a role on the login page:

| Role | Account |
|------|---------|
| HOD | `hod@college.edu` |
| Staff | `ananya@college.edu` |
| Student | `arjun@college.edu` |

## 🛠️ Tech Stack

- **React 18** + **TypeScript** + **Vite**
- **Tailwind CSS** + **shadcn/ui** (full Radix component set)
- **React Router** for the route map
- **TanStack Query** for server-state plumbing
- **Recharts** for analytics charts
- **Framer Motion** + **lucide-react** for motion and icons
- **React Hook Form** + **Zod** for validated forms
- **Vitest** + Testing Library for unit tests, ESLint for linting

## 🚀 Getting Started

```bash
git clone https://github.com/princekumar-dev/classync-.git
cd classync-
npm install
npm run dev
```

Open **http://localhost:5173**, log in with any demo account above.

### Scripts

| Command | What it does |
|---------|--------------|
| `npm run dev` | Dev server with HMR |
| `npm run build` | Production build → `dist/` |
| `npm run preview` | Preview the production build |
| `npm run lint` | ESLint |
| `npm run test` | Run unit tests (Vitest) |

## 📁 Project Structure

```
classync-/
├── src/
│   ├── pages/          # Dashboard, Timetable, Staff, Analytics,
│   │                   # Burnout, Feedback, Occupancy, Notifications…
│   ├── layouts/
│   │   └── AppLayout.tsx   # Sidebar/topbar shell for the app area
│   ├── components/     # Feature components + shadcn/ui primitives
│   ├── hooks/          # Reusable hooks
│   ├── lib/
│   │   ├── mock-data.ts    # All demo data (swap for a real API here)
│   │   ├── auth-context.tsx# Demo role-based auth
│   │   └── utils.ts
│   ├── test/           # Unit tests
│   └── App.tsx         # Route definitions
├── vitest.config.ts    # Unit test config
├── playwright.config.ts# E2E config (for future flows)
└── vite.config.ts
```

## 🔌 Wiring a Real Backend

All domain objects (`StaffMember`, `ClassSection`, `TimetableSlot`, `Notification`, `FeedbackEntry`, …) are typed in `src/lib/mock-data.ts`. To go live:

1. Replace the exported constants with API calls (TanStack Query is already wired)
2. Replace `auth-context.tsx`'s mock login with your identity provider
3. Point the app at your API — no page-level changes required

## 📄 License

All rights reserved.
