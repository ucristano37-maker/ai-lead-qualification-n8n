# Architecture

## Main flow

```text
Website Lead Form
       ↓
n8n Webhook (POST /webhook/ai-lead)
       ↓
Validate Lead
       ↓
Google Sheets: Lookup Email
       ↓
Duplicate?
   ↙          ↘
 YES           NO
  ↓             ↓
Update CRM   OpenAI Qualification
                 ↓
             Parse & Validate JSON
                 ↓
              Qualified?
              ↙       ↘
            YES        NO
             ↓          ↓
        Slack Alert   Nurture Email
             ↓          ↓
        Customer Email  │
              ↘        ↙
             Google Sheets CRM
```

## Reliability principles

- Validate input before external API calls.
- Keep AI output constrained to a small JSON schema.
- Parse and validate AI output before routing.
- Use email as the duplicate key for the starter CRM.
- Keep secrets in n8n Credentials, never in exported JSON committed to Git.
- Add an error workflow for operational visibility.

## Production note

Google Sheets is suitable for a portfolio/demo CRM. For higher volume, replace the duplicate lookup and lead storage layer with PostgreSQL or Supabase.
