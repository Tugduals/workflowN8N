# Automated AI Monitoring

An n8n workflow that collects AI news from Google Alerts and Google News, analyses it with Gemini Flash-Lite, then creates a detailed Notion report and sends a short Gmail briefing.

![Workflow overview](images/workflow.png)

## How it works

1. **Collect** — a manual click starts both RSS feeds; Merge combines their items.
2. **Filter** — recent, relevant articles are kept and duplicates removed.
3. **Analyse** — Gemini ranks stories using RSS titles and excerpts. It must state evidence limits; article pages are not downloaded.
4. **Deliver** — Notion receives the detailed report; Gmail sends key points and source links.

## Repository contents

- [workflows/workflow.ts](workflows/workflow.ts) — TypeScript workflow definition, managed with n8ncli.
- [skills/](skills/) — the three project skills: interview, doubt-driver-dev and hostile-review.
- [images/workflow.png](images/workflow.png) — workflow screenshot.
- [videos/](videos/) — demonstration video and transcript.

Before running, connect your Gemini, Notion and Gmail credentials, set your Notion data source ID, Google Alerts RSS feed and email recipient, and adjust the RSS sources as needed. The report is based on RSS evidence; original articles remain available through their source links.
