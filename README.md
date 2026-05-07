# CoverGrail — Comic Book Pre-Grading Scanner

**IdeaBrowser Idea of the Day — 2026-05-07**  
A computer-vision product that helps comic collectors decide whether a raw comic is worth submitting to CGC/CBCS before spending grading fees and waiting weeks.

> Working premise: collectors overestimate condition under home lighting. CoverGrail asks for front cover, back cover, spine, and raking-light photos, then returns a predicted grade range, confidence score, defect map, and submit/press/sell-raw recommendation.

## Public Build Plan

- [Product Requirements](docs/PRD.md)
- [Technical Architecture](docs/ARCHITECTURE.md)
- [MVP Roadmap](docs/ROADMAP.md)
- [Go-To-Market Plan](docs/GTM.md)
- [Risk Register](docs/RISKS.md)
- [Research Notes](research/notes.md)

## Why This Exists

CGC direct comic grading fees commonly start around ~$30 for modern comics and go materially higher for vintage/high-value books, with turnaround measured in working days/weeks. A collector with a borderline 9.2/9.4/9.6 candidate needs a pre-submission signal before paying grading, pressing, imaging, shipping, insurance, and opportunity cost.

## MVP

1. Upload 4–6 guided photos.
2. Detect major visible defects: spine ticks, corner blunting, color-breaking creases, rub, tears, stains, miswrap/spine roll.
3. Produce a grade band, not a false-certainty grade: e.g. `Likely 8.5–9.2, confidence 0.71`.
4. Generate grader-style notes and a decision recommendation:
   - submit now
   - press/clean first
   - sell raw
   - do not grade unless sentimental/high-value

## Positioning

**Not** “replace CGC.”  
**Yes** “avoid dumb submissions and prepare better books.”

## Disclaimer

CoverGrail is a planning concept and does not affiliate with or represent CGC, CBCS, PSA, or any third-party grading company. Any grade prediction is an estimate only.
