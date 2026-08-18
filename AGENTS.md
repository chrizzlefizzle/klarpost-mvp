# AGENTS.md — KlarPost

## Product mission
Build the simplest possible organization assistant for older adults and their trusted relatives.

The primary user should never have to understand document categories or administrative jargon. They take a photo of their post. KlarPost explains what it is, whether action is needed, what action, and by when.

## Product principles
1. **Action before information.** Always answer “Was muss ich tun?” first.
2. **Senior-first UI.** Large tap targets, large readable type, strong hierarchy, short German sentences.
3. **Calm by default.** Do not create anxiety. If nothing is required, explicitly say “Sie müssen nichts tun.”
4. **Progressive disclosure.** Details are secondary; the main screen stays simple.
5. **Human confirmation for uncertainty.** Never silently invent dates, amounts, recipients or actions.
6. **Trusted-circle privacy.** Relatives only receive information explicitly allowed by the primary user/account configuration.
7. **No dark patterns, ads or unnecessary engagement mechanics.**

## MVP user journey
1. User opens app.
2. User taps the dominant “Post fotografieren” button.
3. User takes/uploads a document photo.
4. Analysis produces structured fields: document type, sender, summary, actionRequired, actionText, dueDate, amount, confidence, needsReview.
5. App presents one simple result card.
6. User confirms/corrects it.
7. If action is required, create a task and reminder.
8. If still unresolved near/after the deadline, notify configured trusted contacts according to settings.

## MVP document types
- Rechnung
- Mahnung
- Termin / Einladung
- Formular / Rückantwort erforderlich
- Informationsschreiben
- Versicherungs-/Kassenbescheid
- Behördenpost
- Sonstiges

## Status model
- `open`: user action required
- `waiting`: user has acted; waiting for another party
- `done`: completed / no further action
- `review`: AI confidence too low or important field unclear

Never let users manually maintain redundant bookkeeping if status can be derived from events.

## Technical direction
- Next.js App Router
- TypeScript strict mode
- Keep dependencies small.
- Mobile-first responsive web app / PWA-ready architecture.
- MVP can use local demo state; isolate persistence behind a repository/service layer so Supabase can replace it later.
- AI analysis must be behind a typed `DocumentAnalyzer` interface. Demo implementation is allowed until API integration.
- Never expose API keys client-side.

## Accessibility
- Minimum primary body text ~18px on mobile where practical.
- Primary controls >= 48px height.
- Do not encode status by color alone.
- Use semantic HTML and visible focus states.
- German copy must be understandable without insurance/administration knowledge.

## Safety and trust
- Treat uploaded documents as sensitive personal data.
- Do not log document content unnecessarily.
- Do not claim legal, medical or financial certainty.
- Low-confidence extraction of a deadline, amount, bank data or required action must trigger review.
- Destructive actions require confirmation.

## Engineering workflow
Before coding:
1. Read this file and `docs/PRD.md`.
2. Keep each change focused and reviewable.
3. Preserve demo usability.

Before finishing:
1. Run `npm run lint`.
2. Run `npm run build`.
3. Add/update tests for non-trivial domain logic.
4. Summarize changes, tests and remaining risks.
