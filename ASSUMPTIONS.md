# ASSUMPTIONS.md — NxtWave Growth Intern Challenge

This document records the sensible strategic, technical, and operational assumptions made while architecting the **"Campus Squad"** referral-driven registration platform.

---

## 1. Growth & Campaign Assumptions
1. **Target Student Segment:** 
   - Final-year (and pre-final year) engineering students (2025/2026 batch) across Tier-2 and Tier-3 Indian colleges.
   - Core anxiety is placement readiness; placing an AI project on the resume provides immediate, high-converting value.
2. **Channel Distribution (Target: 500 Registrations):**
   - **WhatsApp Groups (via Class Reps & Club Leads):** 300 registrations (60%). WhatsApp has >95% daily active usage among Indian college students.
   - **Coding Clubs & Placement Cell Outreach:** 100 registrations (20%). Official endorsements provide institutional trust.
   - **Peer-to-Peer "Campus Squad" Referral Loop:** 100 registrations (20%). Every registrant is incentivized to refer 3–10 classmates.
3. **Budget Allocation (₹2,000 Total):**
   - ₹1,000 allocated to top-referrer reward incentives (5 × ₹200 UPI / Amazon vouchers).
   - ₹500 allocated to micro-targeted Instagram story boost to test copy variants.
   - ₹300 allocated to cloud infrastructure and domain buffers.
   - ₹200 contingency buffer.

---

## 2. Technical & Architecture Assumptions
1. **Database Layer:**
   - Designed for MongoDB / MongoDB Atlas (cloud) with automatic reconnection.
   - Auto-bootstrapped default admin credentials (`admin@nxtwave.tech` / `Admin@123456`) and seeded initial workshop.
2. **Mobile-First WhatsApp Ingress:**
   - Over 75% of incoming clicks arrive from WhatsApp links on smartphones.
   - The landing page contains **zero heavy 3D assets** (using lightweight CSS mesh glows instead of 15MB 3D canvas files) to ensure sub-second First Contentful Paint (<1.2s) even on mobile 4G.
3. **Form Friction Optimization:**
   - Seeded an autocomplete dataset of 100+ top Indian engineering institutes (IIT, NIT, IIIT, BITS, VIT, SRM, PSG, etc.) to allow 1-tap college selection with free text fallback.
   - Indian WhatsApp numbers (+91) validated with regex.
4. **Attendance Rate Mitigation:**
   - Industry show-up rate for free student webinars is 30–40%. Automated reminders at T-24h and T-1h, combined with certificate issuance tied strictly to live verification, are assumed to elevate attendance above 65%.

