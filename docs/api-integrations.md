# API Integrations

## n8n Webhook

Receives `POST /webhook/ai-lead` with the lead JSON payload.

## OpenAI

Used only for flexible qualification and scoring. The workflow validates the returned JSON before routing.

## Google Sheets

Acts as the demo CRM and duplicate-detection store. The `Email` column is the duplicate key.

## Gmail

Sends a confirmation to qualified leads and a nurture response to non-qualified leads.

## Slack

Posts qualified lead alerts to the sales channel.

## Credentials

Configure all service credentials inside n8n. Never commit API keys, access tokens, OAuth secrets, or `.env` files.
