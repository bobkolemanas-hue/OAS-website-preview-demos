# Source Notes

Demo: OAS Demo Auto Care Contra Proof Lab Auto Demo

## Purpose

This demo shows whether a fictional local-service landing page with a quote/request form and follow-up walkthrough can serve as a reusable public proof asset.

## Fictional Status

- Business name: OAS Demo Auto Care
- Phone: (613) 555-0142
- Email: quotes@example.com
- Address/service area: Ottawa demo area — fictional

The business, contact details, service area, owner workflow, and lead examples are fictional or reserved demo data. The demo does not represent real client work or a real auto repair shop.

## Lead-Capture Workflow Demonstrated

The page demonstrates a browser-only intake flow:

1. Visitor submits a quote request.
2. Lead would be stored in a CRM/sheet in production.
3. Owner would receive an alert/summary.
4. Customer would receive a confirmation/follow-up after review.
5. A human reviews before any customer-impacting automation.

In this public demo, the form only updates the on-page owner summary and confirmation message.

## Mocked vs Production

- Mocked here: form submission, owner lead summary, CRM/sheet storage, owner alert, and customer confirmation.
- Production equivalent: a real static landing page could connect to approved lead storage, owner alerts, and confirmation messages after privacy, consent, review, and delivery choices are approved.

## Scope Boundaries

- Static HTML, CSS, JavaScript, and local image asset only.
- No backend, database, paid dependency, third-party form service, outreach, Contra profile, proposal, subscription, deployment setting change, or client commitment.
- No private OAS research pack content, client data, real business identity, real street address, real testimonial, or real review count is included.

## Local Review

From the repo root, serve the site with a simple static server and open the demo path:

```text
python -m http.server 4173 --bind 127.0.0.1
http://127.0.0.1:4173/contra-proof-lab-auto-demo/
```
