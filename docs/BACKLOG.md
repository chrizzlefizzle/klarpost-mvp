# Codex Backlog

Work top to bottom. Keep each task reviewable.

## Task 1 — Build clickable senior-first demo
Create a Next.js + TypeScript app implementing Home, Capture, Analysis Result, Tasks and Trusted Circle using demo data. No external backend required. The entire happy path must be usable on a phone-sized viewport.

Acceptance criteria:
- `npm install`, `npm run lint`, `npm run build` succeed.
- Home has one dominant “Post fotografieren” CTA.
- Demo capture accepts an image/file and then runs a simulated typed analyzer.
- Result clearly says what to do and by when.
- User can confirm result, creating/updating a task.
- Task can be marked done.
- Trusted-circle screen demonstrates escalation configuration.
- Include at least three seeded scenarios from PRD.
- Add unit tests for urgency/status derivation.

## Task 2 — Persistence boundary
Move demo storage behind typed repositories/services. Persist locally for demo (e.g. localStorage) without coupling UI to storage implementation.

## Task 3 — Real document analysis
Implement a server-side OpenAI-backed `DocumentAnalyzer` using structured output. Keep demo analyzer as fallback when no API key is configured. Add validation and low-confidence review behavior.

## Task 4 — Supabase foundation
Add auth, household/person model, document metadata and private storage. Define RLS policies. Never make uploaded documents public.

## Task 5 — Reminder engine
Implement due-soon/overdue derivation and notification abstraction. Demo notifications in-app first.

## Task 6 — Trusted contact invitations
Implement explicit consent/invite model and scoped access for trusted contacts.

## Task 7 — PWA polish
Installable PWA, camera-friendly capture, offline-friendly shell, accessibility pass and senior usability polish.
