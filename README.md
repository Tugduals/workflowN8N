# Automated AI News Monitoring with n8n

This course project automates a daily watch on artificial intelligence news. It collects articles from an RSS feed, asks Google Gemini to write a French summary, saves the report in Notion, and sends it as an HTML newsletter with Gmail.

## How it works

The workflow runs every day at 8:00. It keeps RSS items with a title and a publication date from the last 24 hours, removes duplicate links, and groups each article’s title, URL, date, and excerpt. Gemini turns those items into an XML report with a summary, reported facts, analysis, a suggested action, article details, and source limitations. The report is saved in Notion and formatted for email.

<!-- TODO: Add a screenshot of the workflow here. -->

## Setup

Import [`workflows/Veille automatique.json`](workflows/Veille%20automatique.json) into n8n, then configure:

- Your RSS feed URL (a Google Alerts RSS feed can be used).
- Google Gemini, Notion, and Gmail credentials.
- The Notion data source and Gmail recipient.
- The workflow timezone, such as `Europe/Paris`.

A full test creates a Notion page and sends an email, so use the intended test destination and database.

## Files and limitations

- `workflows/Veille automatique.json` is the file to import into n8n.
- `workflows/Veille automatique.workflow.ts` is the TypeScript representation generated with `@n8n/workflow-sdk` and n8ncli.
- `skills/` contains the interview, development, and review instructions used for this project; they are not n8n nodes.
- `videos/` is reserved for a demonstration video.

The summary is based on RSS excerpts; the workflow does not open or verify full articles. Repeated runs can create multiple Notion pages for the same day.
