# n8n Workflows

Production n8n automations I built for conversational commerce: AI agents on
Facebook Messenger, lead capture into CRM, and WhatsApp broadcasting with delivery
tracking. They come from real client work and from
[ThinFlow](https://beta.thinflow.co), the AI sales agent for WhatsApp, Messenger and Instagram I'm building.

All credentials, tokens, webhook URLs, document IDs, phone numbers and client names
have been removed and replaced with `YOUR_*` placeholders.

## Workflows

| Workflow | What it does | Channels | AI / Data | Nodes |
|---|---|---|---|---|
| [Messenger AI Lead Capture](./messenger-ai-lead-capture) | Arabic AI agent answers Messenger DMs using a RAG knowledge base and captures validated phone numbers as leads | Messenger | Gemini, Supabase pgvector, Postgres memory, Google Sheets, HubSpot | 35 |
| [Messenger AI Message Router](./messenger-ai-message-router) | Classifies incoming messages (technical / sales / support) into structured JSON and routes them to the right agent, with human takeover | Messenger | Gemini, structured output, Postgres memory, Google Sheets, HubSpot | 24 |
| [WhatsApp Bulk Sender with Tracking](./whatsapp-bulk-sender-tracking) | Telegram-controlled personalized WhatsApp broadcast with confirmation step, sent/delivered/read tracking and a stats report | WhatsApp (WAHA), Telegram | Google Sheets, JS code nodes | 20 |

## Patterns used across these workflows

- **Meta webhook handling**: verification challenge plus filtering echo messages so the bot never replies to itself
- **Human-in-the-loop**: a per-contact `AI` / `MANUAL` mode lets a human take over any conversation
- **RAG**: a business document is embedded into Supabase and exposed to the agent as a retrieval tool
- **Structured LLM output**: JSON schema parsing so routing never breaks on free-text replies
- **Rate-limited sending**: batches plus a wait step, with per-message status logging

## How to use

1. In n8n: **Workflows → Import from file** → choose a `workflow.json`.
2. Create the credentials listed in that workflow's README.
3. Search the workflow for `YOUR_` and replace each placeholder.

## Author

**Iheb Brahmi**, founder of [ThinFlow](https://beta.thinflow.co). See my [GitHub profile](https://github.com/2zwegi).
