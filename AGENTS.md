# Ottawa Agent Systems Static Website Demo Builder

This repo is for static GitHub Pages preview demos that show how a cleaner local service business website or lead-capture page could look.

## Core Standard

- Build v1 demos with static HTML, CSS, and JavaScript only.
- Do not add a backend, database, server runtime, build step, analytics, tracking, cookies, secrets, API keys, paid dependencies, or third-party form submission.
- Keep the page deployable from GitHub Pages using the main branch root.
- Use local code and local assets only. Avoid external scripts, external fonts, CDN assets, tracking pixels, map embeds, chat widgets, scheduling widgets, and remote form endpoints.
- If JavaScript is used, keep it progressive and non-essential. Forms must be demo-only and must not send data anywhere.

## Demo Data Rules

- Public demos must use fictional business details only.
- Do not use a real business name, logo, address, phone number, email, reviews, photos, staff names, certifications, awards, ratings, or claims.
- Use obviously safe demo contact details such as `613-555-0198` and `hello@example.com`.
- Mark public demos clearly as fictional concepts.
- Target-specific real-business previews must stay internal and screenshot-only unless the prospect gives explicit consent to publish.
- Do not contact anyone while creating or verifying a demo.

## Design Rules

- Design mobile-first, then enhance for tablet and desktop.
- Put a clear CTA above the fold on mobile and desktop.
- Make copy believable for the local service category: concrete services, practical benefits, service-area language, and normal customer concerns.
- Avoid generic SaaS or AI language such as "revolutionize," "powered by AI," "seamless platform," "unlock growth," "next-gen," and "transform your business."
- Avoid the purple-gradient startup look unless the business context specifically justifies it.
- Use restrained, trade-appropriate visual systems. For local service businesses, prefer clear hierarchy, readable typography, usable contact paths, and grounded colors.
- Keep animations subtle and optional. Do not use motion to hide weak layout or copy.
- Do not make claims that would require proof, such as exact turnaround guarantees, certified status, years in business, real review scores, or named-brand affiliations, unless the demo data is fictional and labeled as such.

## Content Rules

- Above the fold, answer who the demo is for, what service is offered, where it operates, and what action to take.
- Primary CTA should match the page goal. Secondary CTA may support calling or email.
- Include a demo disclaimer near the footer on every public demo page:

  "This is a fictional demo website created to show a website/lead-capture preview concept. It is not a real business."

- Forms must clearly behave as demos. Use `preventDefault()` and show local confirmation text such as "Demo only, no message was sent."
- Avoid filler testimonials. If a review strip is required, label the reviews as demo samples or fictional.

## Verification Required Before Reporting Done

- Check desktop layout and mobile layout.
- Confirm the primary CTA is visible above the fold on mobile.
- Confirm all business details are fictional or demo-safe.
- Confirm there are no analytics, tracking, cookies, secrets, API keys, remote scripts, external assets, or form submission endpoints.
- Confirm the footer disclaimer is present.
- If GitHub Pages is enabled, report the public Pages URL.
- If GitHub Pages cannot be enabled from the current environment, report exact manual steps to enable Pages.

Completion is based on evidence from checks, not on visual confidence alone.
