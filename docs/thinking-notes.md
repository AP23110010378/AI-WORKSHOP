# Strategic Thinking Notes — Design Decisions & Trade-Offs

## 1. What Changed Between First Idea and Final Solution

- **Initial Concept:** A standard 2-page marketing website with a separate registration page, redirecting users to an external Google Form or third-party event platform (like Luma or Eventbrite).
- **Why It Changed:** 
  1. *Friction Kills Conversion:* Requiring students to jump from WhatsApp → Landing Page → External Form creates massive drop-off (>40% abandonment). We embedded the high-converting registration form directly into the landing page hero.
  2. *Lack of Viral Attribution:* Standard event platforms don't offer dynamic campus referral trees or college leaderboards. We built "Campus Squad" natively into the platform so every registrant instantly gets a trackable link and climbs the leaderboard.
  3. *Static vs Interactive Projects:* Instead of just telling students "you will learn AI", we built an interactive sandbox previewing the exact code, architecture, and resume bullet points they will walk away with.

---

## 2. If I Had 24 More Hours, What I Would Improve

1. **Automated WhatsApp Bot Webhook (via Twilio/Gupshup):**
   - Automatically deliver the student's unique referral link, calendar invite (.ics), and countdown reminder directly via WhatsApp message the instant they register.
2. **AI Resume Project Matcher (Client-side LLM Demo):**
   - Allow students on the landing page to upload their current resume and see an AI-generated match score showing which of the 3 workshop projects will boost their ATS score the highest.
3. **Automated College Verification:**
   - Detect student `.edu` or `.ac.in` email domains and auto-credit extra leaderboard bonus points to verified campus domains.

---

## 3. What AI Suggested That I Deliberately Rejected (And Why)

1. **Rejected: Building a Full 12-Table Relational Schema with Complex Subscriptions**
   - *AI Suggestion:* Set up subscription billing, payment gateways, complex RBAC, and heavy multi-tenant database tables.
   - *Why I Rejected It:* This is a free 60-minute workshop with a 7-day campaign deadline and a ₹2,000 budget. Over-engineering database models increases deployment fragility without delivering growth value. Kept the schema focused on Users, Registrations, Referral Trees, and Analytics.
2. **Rejected: Heavy 3D Spline Canvas Animations in Hero**
   - *AI Suggestion:* Embed a 3D animated robot using `@splinetool/react-spline` in the hero section.
   - *Why I Rejected It:* Over 75% of Indian engineering students open referral links on mid-tier Android smartphones via mobile 4G/5G connections on WhatsApp. A 15MB 3D asset destroys page speed and leads to immediate bounces. Replaced with lightweight CSS glowing orbs and SVG particles, maintaining 90+ mobile Lighthouse performance.
3. **Rejected: Requiring Email OTP Verification Before Showing the Referral Link**
   - *AI Suggestion:* Implement a mandatory 6-digit email OTP gate before allowing registration.
   - *Why I Rejected It:* Adding an email verification barrier kills the referral loop at the top of the funnel. Instead, we generate the referral link instantly upon form submit and verify email asynchronously during workshop login.

