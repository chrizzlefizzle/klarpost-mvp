# KlarPost — MVP Product Requirements

## Problem
Older adults receive bills, insurance letters, authority mail, forms and appointment letters. The difficult part is often not reading the document but knowing:

- Muss ich etwas tun?
- Was genau?
- Bis wann?
- Habe ich es schon erledigt?
- Muss jemand helfen?

Adult children/caregivers often become an informal backup system and only learn about missed deadlines too late.

## Product promise
**Ein Foto Ihrer Post. KlarPost sagt Ihnen, was zu tun ist.**

## Primary persona
Older adult with a smartphone who can photograph a letter but does not want to manage administrative workflows.

## Secondary persona
Trusted adult child/caregiver who should be informed only when something relevant remains unresolved.

## MVP success criterion
A test user can photograph/upload a document and, without understanding the original administrative language, correctly answer within seconds:

1. What is this?
2. Do I need to act?
3. What do I need to do?
4. By when?

## Core screens

### 1. Home
Three possible top-level messages:
- `Alles gut` — no user action currently required.
- `Etwas ist zu tun` — one or more actionable tasks.
- `Bitte prüfen` — analysis contains important uncertainty.

Dominant CTA: **Post fotografieren**.

### 2. Capture/upload
Camera-first on mobile, file upload fallback.
Copy: “Fotografieren Sie die ganze Seite. Bei mehreren Seiten fotografieren Sie alle Seiten.”

### 3. Analysis result
Show:
- friendly document label
- sender
- one/two sentence simple-language explanation
- required action or “Sie müssen nichts tun.”
- due date when present
- amount when relevant
- confidence/review warning only when needed

Actions: `Stimmt so`, `Ändern`.

### 4. Tasks
Cards grouped by urgency, not document taxonomy.
Each card shows person, action, due date, state.

### 5. Trusted circle
Configure a child/caregiver and escalation behavior.
Example MVP rule: notify trusted contact when an unresolved task is 3 days from deadline or overdue. In demo mode notification is simulated.

## Demo scenarios
Seed at least these examples:
1. Zahnarztrechnung, €186.40, due soon, action: pay.
2. Health insurer informational letter, no action.
3. Authority form requiring signature and return, due date, marked review if extraction confidence is low.

## Domain model

### Person
- id
- displayName
- role (`self`, `managed`)

### Document
- id
- personId
- createdAt
- type
- sender
- summary
- amount optional
- dueDate optional
- analysisConfidence
- needsReview

### Task
- id
- documentId
- personId
- actionText
- dueDate optional
- status (`open`, `waiting`, `done`, `review`)
- completedAt optional

### TrustedContact
- id
- name
- relationship
- notificationTarget (demo-safe placeholder)
- notifyBeforeDueDays
- notifyWhenOverdue

## AI contract
The analyzer should eventually return typed JSON similar to:

```ts
{
  documentType: "invoice" | "reminder" | "appointment" | "form" | "information" | "insurance_notice" | "authority" | "other",
  sender: string | null,
  summarySimpleGerman: string,
  actionRequired: boolean,
  actionText: string | null,
  dueDate: string | null,
  amountCents: number | null,
  confidence: number,
  uncertainFields: string[]
}
```

Critical fields (action, due date, amount) must not be presented as certain if confidence is insufficient.

## MVP exclusions
No automatic bank transfers, insurance submissions, email sending, WhatsApp/SMS sending, legal interpretation, medication management or health diagnosis.

## Later phases
- OpenAI vision/document analysis
- Supabase auth/storage/database
- push notifications
- email import / share-to-KlarPost
- multi-page document capture
- real trusted-contact notifications
- Open Banking for payment matching
- insurer/authority integrations where feasible
