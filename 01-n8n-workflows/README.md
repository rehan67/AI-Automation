# n8n Workflows

This folder contains exported n8n workflows (`.json`) plus screenshots of the workflow canvas. Each workflow can be imported into any n8n instance.

## Folder Layout

- `workflows/` — exported workflow JSON files (export from n8n)
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

## Planned Workflows (Add Later)

- `webhook-api-router.json` — REST/webhook router + OpenAI decision routing
- `gmail-openai-agent.json` — Gmail trigger + OpenAI + downstream actions

