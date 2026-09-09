# Public Project Outputs

## Source artifact reviewed

- `[산학연병협동연구프로젝트] 정승주,원준하_스마트폰 장루 병변 이미지 추출을 위한 파이프라인 자동화 연구.pdf`

## Current authoritative framing

The current README and Portfolio detail page summarize the final pipeline as:

**WSOL candidate generation → stoma-specific domain-knowledge refinement → retained pseudo-labels → Faster R-CNN retraining**.

The final detector result reported in the Portfolio is **mean IoU 0.7796** and **Dice score 0.8681**, with **673 / 707** pseudo-label candidates retained.

## Portfolio-aligned representative figure

- Portfolio source: `Juna0926/Portfolio/assets/media/research-localization.webp`
- The repository README displays this current Portfolio figure as the primary visual summary.

## Public-safe evidence included

- `assets/figure-01-dataset-structure.svg` — limited-annotation / unlabeled-data structure: 15 bounding-box-labeled images and 707 unlabeled images.
- `assets/figure-02-pseudolabel-results.svg` — intermediate pseudo-label selection / refinement-stage summary. The values shown there belong to that stage and should not be confused with final held-out detector performance.
- `assets/figure-03-conclusion.svg` — final held-out detector summary: mean IoU **0.7796**, Dice score **0.8681**, and the inference-time value reported in the source material.
- `localization-public-technical-excerpt.pdf` — curated public-safe technical excerpt.

## Result provenance

The project contains metrics from different pipeline stages. The Portfolio and README use **0.7796 mean IoU / 0.8681 Dice** as the final detector result. Intermediate candidate-selection figures are retained only to document the pseudo-label refinement process and are not presented as the final detector score.

## Privacy note

The full original presentation contains patient-derived clinical imagery. Those pages are intentionally not redistributed in this public repository. Public figures preserve the technical workflow and quantitative findings without exposing clinical images.
