# AI + Learning Log — Build Session Reflection

This log documents genuine problem-solving moments during the development of the "Campus Squad" growth platform, showing where AI proposed architectural choices, what was adjusted, and why.

---

### Entry 1: Database Architecture & Local Environment Recovery
- **What was asked:** *"Fix the registration and backend connection failure on the landing page."*
- **What AI suggested:** Install local MongoDB community edition via Windows MSI installer, configure Windows services, and modify local background daemons.
- **What was changed & why:** Rejected installing a local database daemon on Windows (which requires admin privileges and system restarts). Instead, pivoted cleanly to a free cloud-hosted MongoDB Atlas cluster. This ensured that the database is resilient, cloud-ready, and directly compatible with cloud deployments on Render / Vercel.

---

### Entry 2: Vite Dev Server Proxy vs Windows IPv6 Resolution
- **What was asked:** *"Fix 'Unable to connect to backend server' error in admin login."*
- **What AI suggested:** Disable CORS entirely in Express backend and write custom headers on every route.
- **What was changed & why:** Recognized the root cause was Node.js 18+ resolving `localhost` to IPv6 (`::1:5000`) on Windows while Express listened on IPv4 (`127.0.0.1:5000`). Instead of weakening security headers, configured Vite's proxy specifically to target `http://127.0.0.1:5000` with explicit `changeOrigin: true`. This solved the issue permanently while keeping strict CORS policies intact.

---

### Entry 3: Landing Page Mobile Registration Friction
- **What was asked:** *"Change the complete UI and landing page; it should be attractive."*
- **What AI suggested:** Create a multi-step modal wizard that opens only after clicking "Register Now" across multiple steps.
- **What was changed & why:** Rejected the multi-step modal wizard. On mobile devices (where WhatsApp referral links open), modal popups have high abandonment rates (>35%). Instead, engineered an **inline, high-converting fast registration card** directly integrated into the hero section with a seeded autocomplete list of 100+ Indian engineering colleges, reducing form fill time to under 30 seconds.

