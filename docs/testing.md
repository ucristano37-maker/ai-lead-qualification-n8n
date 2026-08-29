# Testing Checklist

## Happy path

- [ ] POST `examples/qualified-lead.json` to the test webhook.
- [ ] Confirm AI output has a boolean `qualified`, score 0–100, and valid priority.
- [ ] Confirm qualified lead reaches Slack.
- [ ] Confirm customer email is sent.
- [ ] Confirm lead is stored in Google Sheets.

## Nurture path

- [ ] POST `examples/low-quality-lead.json`.
- [ ] Confirm `qualified=false` and a valid priority.
- [ ] Confirm only the nurture email path runs.
- [ ] Confirm the lead is stored with `Status=Nurture`.

## Duplicate path

- [ ] Send the same email twice.
- [ ] Confirm the second request is marked duplicate.
- [ ] Confirm the duplicate does not call OpenAI or send customer/sales notifications.

## Validation failures

Test missing name, malformed email, missing message, negative budget, and non-numeric budget. These should fail before external service calls.

## Credentials

Verify that the imported workflow has valid n8n credentials selected for OpenAI, Google Sheets, Gmail, and Slack before activation.
