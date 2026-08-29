# AI Lead Qualification & Sales Automation

An AI-powered business automation system built with **n8n, OpenAI, Webhooks, JavaScript, Google Sheets, Gmail, Slack, and REST APIs**.

## What it does

1. Receives business leads through an n8n webhook.
2. Validates required lead information.
3. Detects duplicate leads using email.
4. Sends new leads to OpenAI for qualification.
5. Scores leads from 0–100 and assigns priority.
6. Routes qualified leads to Slack and customer email.
7. Sends a professional nurture email to lower-quality leads.
8. Stores lead and AI analysis in Google Sheets CRM.
9. Includes a dedicated error-handling workflow.

## Architecture

```text
Website Lead Form
       ↓
n8n Webhook
       ↓
Validate Lead
       ↓
Duplicate Check
   ↙         ↘
Duplicate    New Lead
   ↓            ↓
Update CRM   OpenAI Qualification
                 ↓
             Parse Result
                 ↓
              Qualified?
              ↙        ↘
            YES         NO
             ↓           ↓
        Slack Alert   Nurture Email
             ↓           ↓
        Customer Email   │
              ↘         ↙
             Google Sheets
                  ↓
               Complete
```

## Tech Stack

- n8n
- OpenAI API
- REST APIs
- Webhooks
- JavaScript
- JSON
- Google Sheets API
- Gmail API
- Slack API

## Repository

- `workflow/ai-lead-qualification.json` — importable n8n workflow
- `workflow/error-handler.json` — error workflow
- `examples/` — sample webhook payloads
- `docs/` — setup, architecture, integrations, and testing

## Security

No API keys, OAuth tokens, passwords, or secrets are stored in this repository. Configure integrations through n8n Credentials and keep environment secrets outside Git.

## Lead payload

```json
{
  "name": "Ali Khan",
  "email": "ali@example.com",
  "company": "ABC Solutions",
  "message": "We need an AI chatbot and automated lead follow-up system.",
  "budget": 5000,
  "source": "Website"
}
```

## Testing

Use the payloads in `examples/qualified-lead.json` and `examples/low-quality-lead.json` against the webhook endpoint after importing and configuring the workflow.

## Portfolio Summary

Built an end-to-end AI automation system using n8n, OpenAI, REST APIs, Google Sheets, Gmail, Slack and webhooks. The system automatically captures and validates business leads, uses AI to qualify and score them, routes qualified leads to the sales team, sends automated customer responses, and maintains a centralized lead database.
