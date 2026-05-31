# n8n Workflows

This folder contains exported n8n workflows (`.json`) plus screenshots of the workflow canvas. Each workflow can be imported into any n8n instance.

## Folder Layout

- `workflows/` — exported workflow JSON files (import these into n8n)
- `screenshots/` — workflow canvas screenshots (optional but recommended)

## How To Export (n8n → JSON)

1. Open the workflow in n8n
2. Click the menu (three dots)
3. Export / Download workflow
4. Save into `workflows/` using a clear name, e.g. `webhook-api-router.json`

## Security Checklist (Before Committing)

Do not commit secrets.

Before pushing, open the exported JSON and search for:

- `apiKey`
- `token`
- `Authorization`
- `password`
- `secret`

If you see a real value:

- move it to n8n Credentials (preferred), or
- use environment variables, or
- reference it via a variable expression

## How To Import (JSON → n8n)

1. In n8n, go to Workflows
2. Import from file
3. Select a JSON file from `workflows/`
4. Recreate credentials inside your n8n instance

## Workflow Documentation Template

When you add a new workflow, include these details in the project README or in a short note near the workflow name:

- Name:
- Trigger:
- Inputs (example payload):
- External services:
- Required credentials:
- Required env vars:
- Output (what it creates/returns):
- Error handling / retries:

## Included Workflows

### 1) webhook-api-router.json

**Goal:** Single webhook endpoint that routes requests based on `action` and returns a JSON response.

**Trigger:** Webhook (POST)  
**Path:** `api-router`  
**Response Mode:** When Last Node Finishes (returns the last node output)

**Request examples**

- Ping:

```json
{ "action": "ping" }
```

- Echo:

```json
{ "action": "echo", "hello": "world" }
```

- Summarize (uses OpenAI):

```json
{ "action": "summarize", "text": "Paste any text here..." }
```

**Environment variables**

- `OPENAI_API_KEY` (required only for `action=summarize`)

**Notes**

- If `action` is not recognized, workflow returns an error JSON.

### 2) gmail-automation.json

**Goal:** Small demo flow that sends a test email on a schedule.

**Trigger:** Cron (Every day 09:00)  
**Action:** Gmail → Send message

**Setup**

1. Import the workflow JSON
2. Create Gmail credentials in n8n and select them in the Gmail node
3. Open the “Compose Email” node and replace `YOUR_EMAIL@example.com`
4. Activate the workflow

## Next Workflows (Add Later)

- Add workflow screenshots into `screenshots/`
- Add more routes to the webhook router (for example: `create_ticket`, `send_slack`, `rag_query`)
