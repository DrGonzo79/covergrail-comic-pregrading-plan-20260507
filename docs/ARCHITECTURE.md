# Technical Architecture — CoverGrail

## 1. System Overview

CoverGrail is a guided image-capture + computer vision + decision-support system.

```text
Mobile/Web Capture
      ↓
Image Quality Gate
      ↓
Comic Segmentation + Normalization
      ↓
Defect Detection Models
      ↓
Grade Band Estimator
      ↓
Economics Engine
      ↓
Report Generator + Saved Library
```

## 2. Recommended Stack

### Frontend
- Next.js + TypeScript.
- Tailwind CSS.
- Mobile-first PWA capture flow.
- Later: native iOS/Android if capture quality becomes the moat.

### Backend
- FastAPI or Node/Express API.
- PostgreSQL for users, books, scans, reports.
- S3-compatible object storage for images.
- Redis/queue for async image processing.

### ML/CV Layer
- Phase 1: GPT-4o / Gemini multimodal prompt pipeline + deterministic rubric engine.
- Source-data targets: eBay sold listings, Heritage Auctions records, and GoCollect-style data where high-resolution photos can be matched to verified slab grades.
- Phase 2: Fine-tuned defect detection model using YOLOv8/RT-DETR for visible defects.
- Phase 3: Ensemble grade band model trained on known slabbed books and grader notes.

### Infrastructure
- Vercel for web app.
- Render/Fly.io/AWS ECS for API workers.
- Supabase or Neon Postgres to move quickly.
- Cloudflare R2/S3 for images.
- Sentry + PostHog for observability.

## 3. Core Data Model

```sql
users(id, email, plan, created_at)
books(id, user_id, title, issue, publisher, year, variant, raw_estimated_value)
scans(id, book_id, status, capture_set_id, model_version, created_at)
images(id, scan_id, type, storage_url, quality_score, width, height)
defects(id, scan_id, defect_type, severity, x, y, w, h, confidence)
reports(id, scan_id, grade_low, grade_high, confidence, recommendation, report_json)
comparables(id, book_id, source, raw_value, slab_values_json, checked_at)
```

## 4. Image Capture Quality Gate

Before grading, reject low-quality inputs:
- Blur detection via Laplacian variance.
- Glare detection via saturated region analysis.
- Perspective skew detection.
- Minimum resolution threshold.
- Missing required photo angles.

This is a product moat: better capture → better predictions.

## 5. Defect Taxonomy

Initial visible defects:
- Spine tick / stress line.
- Color-breaking crease.
- Non-color-breaking bend/dent.
- Corner blunting/crunch.
- Edge tear/chip.
- Cover rub/scuff.
- Stain/water mark/foxing.
- Miswrap/off-center cover.
- Spine roll.
- Staple wear/rust visible from exterior.

## 6. Grade Estimation Strategy

### MVP Hybrid Approach
1. Multimodal model describes visible condition.
2. Structured extractor converts observations into defect taxonomy.
3. Rubric engine applies grade caps and grade-band heuristics.
4. Confidence score combines image quality, defect ambiguity, and model agreement.

### Why grade bands, not exact grades
Exact grading is subjective and opaque. A grade band is more honest and more actionable for submission economics.

## 7. Economics Engine

Inputs:
- Estimated raw sale value.
- Estimated slab values for grade band.
- Grading fee.
- Pressing/cleaning cost.
- Shipping/insurance.
- Marketplace fee.
- Turnaround time.

Outputs:
- Expected value if submitted now.
- Expected value if pressed first.
- Downside scenario.
- Recommendation.

## 8. Report Format

Each report should include:
- Hero image with annotated defects.
- Grade range + confidence.
- Defect summary.
- Pressability notes.
- Submit economics.
- “What would improve this book?” checklist.

## 9. Security / Privacy

- Private scans by default.
- Signed image URLs.
- Delete images on account deletion.
- No training on user images unless opted in.
- Public sharing only by explicit report link.
