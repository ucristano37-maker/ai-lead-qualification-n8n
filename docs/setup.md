# Setup

## 1. Import the workflow

Import `workflow/ai-lead-qualification.json` into n8n.

## 2. Configure credentials

Create n8n Credentials for:

- OpenAI
- Google Sheets
- Gmail
- Slack

Do not paste API keys into Code nodes or commit them to GitHub.

## 3. Configure Google Sheets

Create a spreadsheet named `AI Lead CRM` with these columns:

`Date, Name, Email, Company, Message, Budget, Source, Qualified, Score, Priority, Service, AI Reason, Recommended Action, Status`

Set the spreadsheet and sheet references in the Google Sheets nodes.

## 4. Configure Slack

Select the sales channel where qualified lead alerts should be posted.

## 5. Configure Gmail

Set the sender account through n8n Gmail credentials. The customer email is sent to the validated lead email address.

## 6. Activate the webhook

The production webhook path is:

`POST /webhook/ai-lead`

The exact base URL depends on your n8n deployment.

## 7. Test

Use the JSON files in `examples/` as POST request bodies. Test qualified, low-quality, duplicate, invalid-email, missing-name, and invalid-budget cases before activation.
