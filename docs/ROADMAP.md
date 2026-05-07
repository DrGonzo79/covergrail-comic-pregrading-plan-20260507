# MVP Roadmap

## Week 1 — Validation Sprint

- Build landing page with value prop: “Know before you slab.”
- Interview 15 collectors/sellers/local comic shop owners.
- Collect 100 sample books: raw photos + known slab grades where possible.
- Manually create 20 sample reports to test willingness to pay.

Deliverable: concierge MVP + waitlist.

## Week 2 — Guided Capture Prototype

- Build PWA capture flow.
- Enforce front/back/spine/raking-light inputs.
- Add image quality checks: blur, glare, resolution, perspective.
- Store scans in S3/R2 with Postgres metadata.

Deliverable: upload-to-report skeleton.

## Week 3 — AI Report Generator

- Implement multimodal condition analysis.
- Convert observations to structured defect taxonomy.
- Add rubric-based grade-band estimator.
- Generate report PDF/share page.

Deliverable: first automated report.

## Week 4 — Economics Layer

- Add user-provided raw value and expected slab comps.
- Add configurable grading/pressing/shipping cost assumptions.
- Output submit/press/sell-raw recommendation.

Deliverable: decision-support MVP.

## Weeks 5–8 — Accuracy/Data Moat

- Partner with collectors for blinded before/after grading tests.
- Build evaluation dataset of photos + official grades + grader notes.
- Add defect bounding boxes manually for first 500 images.
- Train first specialized defect detector.

Deliverable: model v0.2 with measurable accuracy.

## 90-Day Goal

A paid beta with:
- 500+ users.
- 10,000+ scans.
- 1,000+ opted-in labeled images.
- 3–5 pressing/shop partners.
- Public accuracy report from blind submissions.
