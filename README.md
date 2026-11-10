# EventAxis

**Event Discovery, Registration & Management Platform**

> *Discover. Register. Experience.*

[![React](https://img.shields.io/badge/React-19.2-61DAFB?logo=react&logoColor=black)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-Strict-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Vite](https://img.shields.io/badge/Vite-8.3-646CFF?logo=vite&logoColor=white)](https://vite.dev/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-CSS-3.4-38B2AC?logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)
[![Express](https://img.shields.io/badge/Express-4.21-000000?logo=express&logoColor=white)](https://expressjs.com/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16-4169E1?logo=postgresql&logoColor=white)](https://www.postgresql.org/)

---

EventAxis is a responsive event discovery, registration, and ticketing platform. It features a client-persistent React single-page application powered by client-side persistence and synthesized audio, accompanied by an Express REST API backend and containerized PostgreSQL and Redis infrastructure.

---

## 🎯 Key Features

### 🎟️ Attendee Experience
- **Event Discovery**: Filter and search through upcoming hackathons, workshops, and tech talks with local capacity and category badges.
- **Detailed Event Synopsis**: Inspect event timelines, guest speaker bios, perks, and participation rules.
- **Multi-Step Checkout**: Attendee registration flow with simulated multi-channel payment gateway (UPI, Cards, NetBanking, and free passes).
- **Client-Generated Digital Passes**: Structured verification tokens rendered into high-resolution QR matrix codes (Error Correction Level H) with instant PNG download.
- **Passbook Wallet**: Centralized view of all registered attendee passes with check-in status indicators.

### 🛡️ Organizer Command Center
- **Event Operations**: Create, update, and manage events, quota allocations, fees, and registration deadlines with localStorage persistence and optional backend API integration.
- **Attendee Registry**: Searchable participant directory with one-click CSV export.
- **QR Check-In Terminal**: Fast admission terminal supporting client token verification, duplicate check-in detection, and event door filtering.
- **Synthesized Audio Telemetry**: Procedural Web Audio API synthesizer chords and Web Speech API voice announcements for operational status cues.

---

## 🛠️ Technology Stack

| Layer | Technologies | Implementation Details |
| :--- | :--- | :--- |
| **Frontend Framework** | React 19, TypeScript | Reactive SPA component architecture with TypeScript strict typing |
| **Build & Tooling** | Vite 8, Oxlint | Native ESM development server, bundling, and fast static analysis |
| **Styling & Design** | Tailwind CSS 3.4, PostCSS | Custom glassmorphism, responsive layout, and dark-theme tokens |
| **Icons & Effects** | Lucide React, Canvas Confetti | System iconography and post-registration celebration effects |
| **QR Engine** | QRCode (`qrcode`) | Client-side 2D matrix generation with Level H error correction and PNG export |
| **Audio Engine** | Web Audio API, Web Speech API | Algorithmic polyphonic synthesizer chimes and speech synthesis voice output |
| **Client Persistence** | Browser LocalStorage | Client-side storage for events, registrations, and audio preferences with seed fallback |
| **Backend Service** | Node.js, Express 4.21, Zod | REST API for event catalog endpoints (`server/`) with input schema validation |
| **Database** | PostgreSQL 16 (`pg`) | Relational database schema with pre-configured schema and seed scripts |
| **Caching Infrastructure** | Redis 7 | Container infrastructure defined in Docker Compose (foundational service) |

---

## 📁 Project Structure

```
.
├── public/                # Static assets, icons, and image resources
├── src/                   # Frontend React SPA
│   ├── components/
│   │   ├── admin/         # Organizer dashboard, event editor, and QR scanner terminal
│   │   ├── background/    # Dynamic background visual effects
│   │   ├── events/        # Discovery catalog, filter controls, and synopsis modals
│   │   ├── navigation/    # Navbar brand header, role switcher, and audio toggle
│   │   ├── opening/       # Cyber-styled boot sequence splash screen
│   │   ├── registration/  # Multi-step checkout & payment gateway simulator
│   │   ├── tickets/       # Digital pass passbook modal and downloadable QR cards
│   │   └── ui/            # Toast alert notifications and shared modal primitives
│   ├── hooks/             # Web Audio synthesizer and speech synthesis controller
│   ├── services/          # Client storage service (localStorage) and backend API client
│   ├── types/             # Domain models, event interfaces, and verification types
│   └── utils/             # QR token encoding, parsing, and audio helpers
├── server/                # Express REST API backend service
│   ├── src/
│   │   ├── config/        # Environment variable schemas (Zod)
│   │   ├── db/            # PostgreSQL pool configuration, schema.sql, and seed.sql
│   │   ├── middleware/    # Error handling and CORS configuration
│   │   └── modules/       # Event routes, controllers, and database services
│   ├── package.json       # Backend dependencies
│   └── tsconfig.json      # Backend TypeScript configuration
├── docker-compose.yml     # PostgreSQL 16 and Redis 7 container infrastructure
└── vite.config.ts         # Vite bundler and plugin configuration
```

---

## 🚀 Getting Started

### Prerequisites
- **Node.js**: `^20.19.0 || >=22.12.0` (required by Vite 8)
- **Package Manager**: npm or pnpm
- **Docker & Docker Compose** *(optional, for running containerized database services)*

### Frontend Development

```bash
# Clone the repository
git clone https://github.com/pranjalisantani/jitacm_event-registration_platform.git
cd jitacm_event-registration_platform

# Install frontend dependencies
npm install

# Start development server
npm run dev
```

### Production Build

```bash
# Compile TypeScript and bundle frontend for production
npm run build

# Preview production build locally
npm run preview
```

### Backend & Infrastructure (Optional)

The frontend operates independently using client-side local storage. To run the companion Node.js / Express backend with PostgreSQL:

#### Environment Configuration
Environment defaults are pre-configured in `server/src/config/env.ts` (`PORT=4000`, `CORS_ORIGIN=http://localhost:5173`, and local `DATABASE_URL`). Refer to `server/src/config/env.ts` for defaults, and create a `server/.env` file for overrides.

#### Startup Commands

```bash
# 1. Start PostgreSQL 16 and Redis 7 containers
docker compose up -d

# 2. Install backend dependencies and launch dev server (runs: tsx watch src/server.ts)
cd server
npm install
npm run dev
```

For production backend execution:
```bash
# Compile TypeScript and run Node.js server (runs: node dist/server.js)
npm run build
npm start
```
