# PRD — CoverGrail

## 1. Problem

Comic collectors decide whether to submit raw books for professional grading using inconsistent home inspection: desk lighting, biased self-assessment, limited defect vocabulary, and poor understanding of grade-value cliffs. The wrong decision wastes grading fees, shipping, pressing costs, and weeks of waiting.

## 2. Customer

### Primary ICP
- Raw comic collectors with 50–2,000 books.
- eBay/Whatnot sellers deciding whether slabbing improves sale price.
- Local comic shops triaging customer collections.
- Convention dealers doing fast intake decisions.

### Secondary ICP
- Pressing/cleaning services using the tool as a lead funnel.
- Insurance/estate appraisal workflows.

## 3. Core Job-To-Be-Done

“When I’m considering grading a raw comic, help me estimate the likely grade band and economics before I spend money submitting it.”

## 4. User Stories

1. As a collector, I can upload guided images so the tool can inspect relevant surfaces.
2. As a seller, I can see a likely grade range and confidence score before deciding to slab.
3. As a presser, I can identify pressable vs non-pressable defects.
4. As a shop owner, I can batch-triage books and export a submit list.
5. As a collector, I can compare estimated slab value vs raw value and grading costs.

## 5. MVP Scope

### Inputs
- Front cover photo.
- Back cover photo.
- Spine close-up.
- Corner close-ups or auto-cropped corners.
- Optional raking-light photo to expose bends/finger dents.
- Metadata: title, issue, year, publisher, variant if known.

### Outputs
- Predicted grade band: e.g. `7.5–8.5`, `9.2–9.6`.
- Confidence score.
- Defect map with bounding boxes/annotations.
- Grader-style notes.
- Pressability estimate: pressable / maybe / not pressable.
- Economic decision: submit, press then submit, sell raw, skip.

### Explicit Non-Goals for MVP
- Official certification.
- Interior page-by-page analysis.
- Restoration detection beyond visible red flags.
- Guaranteed CGC/CBCS exact-grade prediction.

## 6. Success Metrics

### Product Metrics
- 70%+ of first-time users complete guided capture.
- 40%+ create a saved book report.
- 25%+ run a second scan within 7 days.

### Model Metrics
- Within ±0.5 grade for 45%+ of test books by month 3.
- Within ±1.0 grade for 75%+ of test books by month 3.
- Defect detection precision target: 0.70+ on visible spine/corner defects.

### Business Metrics
- Opportunity score target from source analysis: 9/10; feasibility target: 8/10.
- Paid conversion: 5–8% from three free scans.
- ARPU: $1.99/pay-per-scan users, $29/mo collector subscribers, $499/mo dealer accounts.
- Partner lead revenue from pressing/cleaning referrals.

## 7. Pricing Hypothesis

- Free: 3 scans on signup to create the first trust moment.
- Pay-per-scan: $1.99 per prediction for casual collectors.
- Collector Unlimited: $29/mo for frequent grading decisions and saved library.
- Dealer: $499/mo for bulk scanning, estate-purchase triage, and submission-lot building.
- Pressing partner marketplace: lead fee or rev share.

## 8. Key Product Principle

Do not pretend to be an official grader. Sell decision confidence and submission triage.
