# Client Ops Autopilot

n8n workflows that automate the repetitive parts of client operations — lead intake, CRM sync, and invoice follow-ups — so they run on a schedule instead of manually.

Built for [Oniqutes Digital Solutions](https://oniqutes.com) — this is the automation behind our Workflow Automation service, not just a portfolio demo.

## Status

**Planning / early build.** Workflow design below is locked in; the workflows themselves are being built and tested in a self-hosted n8n instance before their JSON exports land in `workflows/`. Nothing gets committed here until it's actually been run.

## What it does (planned)

| # | Workflow | Trigger | Steps |
|---|----------|---------|-------|
| 1 | **Lead intake** | Form/email submission | Parse submission → add row to CRM sheet → send email notification |
| 2 | **CRM sync** | Schedule | Keep two systems in sync on a recurring interval |
| 3 | **Invoice follow-up** | Schedule | Check unpaid invoices past due date → send reminder → log it |

## Stack

- **Automation engine:** [n8n](https://n8n.io), self-hosted via Docker
- **CRM/data store:** Google Sheets (simple, no extra accounts, easy to swap for a real CRM later)
- **Notifications:** Email

## Setup

1. Run n8n locally with Docker:
   ```
   docker run -it --rm --name n8n -p 5678:5678 -v n8n_data:/home/node/.n8n docker.n8n.io/n8nio/n8n
   ```
2. Open `http://localhost:5678` and create an owner account.
3. Import a workflow from `workflows/*.json` via **Workflows → Import from File**.
4. Connect your own Google Sheets and email credentials in n8n's credential manager — none are bundled here.

## Importing a workflow

Once exported workflow files exist in `workflows/`, each one is a self-contained JSON file. In the n8n editor: **Workflows → Import from File** → select the file → review/set credentials → activate.

## Roadmap

- [ ] Build and test lead intake workflow in n8n
- [ ] Export and commit `workflows/lead-intake.json`
- [ ] Build and test CRM sync workflow
- [ ] Build and test invoice follow-up workflow
- [ ] Document per-workflow setup notes

## License

MIT
