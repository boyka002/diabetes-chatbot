# Diabetes Self-Management Chatbot (ADCES7)

AI-powered chatbot prototype for diabetes self‑management grounded in the ADCES7 Self‑Care Behaviors. Built with Next.js and a self‑hosted LLM via Ollama, with streaming responses and proactive context gathering.

## Live Demo

- https://diabeties-chatbot.fly.dev

## Source Code

- https://github.com/boyka002/diabetes-chatbot

## Chosen Diabetes Stage

**Type 2 Diabetes Diagnosis**

**Rationale:** The bot’s tone and guidance are calibrated for newly diagnosed or early‑stage Type 2 users. It focuses on practical, low‑friction behavior changes and builds confidence through small, actionable steps. This matches the onboarding‑style experience of a first‑time self‑management program.

## ADCES7 Alignment

The assistant structures guidance around:

- Healthy Eating
- Being Active
- Monitoring
- Taking Medication
- Problem Solving
- Healthy Coping
- Reducing Risks

When a user asks a vague question (e.g., “What should I eat?”), the bot gathers missing context (recent meal, glucose, activity) before responding with tailored guidance.

**Notes:**
- LLM integration is self‑hosted through Ollama (no third‑party hosted APIs).

## Socratic State Management Strategy

- **Session tracking:** `lib/session.ts` maintains an in‑memory session map keyed by `x-session-id`.
- **Context extraction:** User messages are parsed for glucose values, meals, activity, medication, stress, and goals.
- **History trimming:** Only the most recent 8 messages are retained to control token usage.
- **Socratic prompts:** `lib/promptBuilders.ts` generates follow‑up questions when essential context is missing.

## Performance & Optimization

- **Streaming responses:** API streams tokens to the client for low latency perceived output.
- **Token management:** Message history is trimmed and user snippets are truncated.
- **Efficient UI:** Minimal client state and simple component tree for fast render.

## Deployment

### Chatbot (Fly.io)

Environment variables:

```bash
OLLAMA_URL
OLLAMA_MODEL
```

### Ollama (AWS EC2)

- Public endpoint accessible from the chatbot host.
- `gemma3:1b` model pulled and ready.

## SonarQube (Maintainability Focus)

- Use SonarQube/SonarCloud to analyze code quality, duplication, and maintainability.

## Architecture Document Checklist (Per Requirements)

- Diabetes stage + personality rationale (above)
- System design diagram (above)
- Socratic state management strategy (above)
- SonarQube report link/PDF (add below)

**SonarQube Report:**
- (<img width="1470" height="956" alt="Screenshot 2026-02-14 at 9 59 31 AM" src="https://github.com/user-attachments/assets/69c3a051-a14c-4a4e-b084-6beb348000e0" />


## Screenshots

<img width="2896" height="1118" alt="image" src="https://github.com/user-attachments/assets/84e1e9f6-5431-474f-bbef-212325485dcf" />


![Streaming Response](docs/screenshots/streaming-response.png)
