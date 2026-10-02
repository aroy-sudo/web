# 1. Mission (Project Context)
**Project:** Next.js Frontend for an ML-powered hackathon application.
**Core Constraint:** Speed to MVP. We have 24-48 hours. Prefer existing UI components over custom CSS. Write the minimum amount of code necessary to achieve the requirement (The Ponytail Philosophy). 

# 2. Technical Stack
- **Framework:** Next.js (App Router only, no Pages router).
- **Language:** TypeScript.
- **Styling:** Tailwind CSS.
- **State Management:** React Context or native hooks. No Redux.
- **Data Fetching:** Native `fetch()` to our local FastAPI backend.

# 3. Toolchain Registry
| Intent | Command | Notes |
| :--- | :--- | :--- |
| **Start Dev** | `npm run dev` | Runs on localhost:3000 |
| **Install** | `npm install <pkg>` | ASK before adding new dependencies |
| **Build** | `npm run build` | Run this before final submission to catch TS errors |

# 4. Judgment Boundaries
**NEVER (Hard Limits):**
- Never write legacy React class components.
- Never write custom CSS if a Tailwind utility class can achieve the same result.
- Never guess the JSON shape coming from the ML API. If it is ambiguous, ask the human to check the FastAPI schema.
- Never strip out existing error handling to make a feature work.

**ASK (Human-in-the-loop Triggers):**
- Ask before adding heavy npm packages (e.g., Three.js, Framer Motion) unless explicitly requested.
- Ask before deleting existing files.

**ALWAYS (Proactive Action):**
- Always include `"use client";` at the top of files that use React hooks (`useState`, `useEffect`).
- Always type your API request payloads and responses using TypeScript interfaces.
- Always check if the standard library or browser API can solve the problem before writing a custom utility function.

# 5. Architecture & Routing Rules
- **`/src/app/`**: Contains page layouts and route definitions. Keep logic here minimal.
- **`/src/components/`**: All reusable UI (buttons, cards, forms).
- **`/src/lib/`**: API fetching logic and helper functions.
- **Client vs. Server:** Default to Server Components. Only convert a component to a Client Component if it requires interactivity (onClick, state) or browser APIs.
- **API Calls:** Route all data fetching through helper functions in `src/lib/api.ts` to ensure the FastAPI base URL is consistent.