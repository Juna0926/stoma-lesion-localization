# Data-Efficient Stoma Lesion Localization via WSOL and Pseudo-Label Refinement with Domain Knowledge

> A data-efficient localization pipeline for smartphone-captured stoma images under extremely limited bounding-box supervision.

**Period:** Feb. 2026 - Jun. 2026  
**Affiliation:** Machine Learning & Data Mining Laboratory, Ajou University  
**Type:** Collaborative medical-image research  
**Core methods:** Weakly Supervised Object Localization (WSOL) · Domain-guided pseudo-label refinement · Faster R-CNN

---

## Overview

This research addressed lesion localization in a **limited-annotation setting** with only **15 bounding-box-labeled images** and **707 unlabeled smartphone-captured stoma images**.

Instead of relying on exhaustive manual annotation, the pipeline:

1. generates candidate lesion regions through **WSOL**,
2. refines the candidates using **stoma-specific domain knowledge**, and
3. retrains **Faster R-CNN** using the retained pseudo-labels.

The goal was to build a practical localization workflow that can learn clinically relevant regions even when detailed bounding-box annotation is scarce.

![Dataset structure](assets/figure-01-dataset-structure.svg)

## Research problem

Patient-captured stoma images vary substantially in lighting, angle, distance, background, and image quality. Detailed lesion bounding-box annotation is also expensive and difficult to scale.

The project therefore asked whether weak localization cues and domain knowledge could be combined to create useful pseudo-labels for detector training.

## Method

### 1. Candidate generation

**Weakly Supervised Object Localization (WSOL)** was used to generate candidate lesion regions from unlabeled smartphone-captured stoma images.

### 2. Domain-informed pseudo-label refinement

Candidate regions were evaluated using stoma-specific visual signals including:

- red-color prominence,
- luminance contrast,
- orientation, and
- center proximity.

These rules were used to filter unreliable WSOL candidates before detector retraining.

### 3. Final detector

The refined pseudo-labels were added as training supervision for **Faster R-CNN**, which served as the final lesion detector.

## Main results

![Pseudo-label selection results](assets/figure-02-pseudolabel-results.svg)

| Metric | Result |
|---|---:|
| Bounding-box-labeled images | 15 |
| Unlabeled images | 707 |
| Retained pseudo-labels | **673 / 707** |
| Mean IoU | **0.7796** |
| Dice score | **0.8681** |

The final detector achieved **mean IoU 0.7796** and **Dice score 0.8681** after retaining 673 of 707 pseudo-label candidates.

## Why this mattered

The key contribution is **domain-knowledge-guided pseudo-label refinement**. Rather than treating every weakly localized region as equally reliable, the pipeline filters candidates using medically relevant visual characteristics before detector retraining.

This study also followed naturally from the earlier stoma-classification project. After identifying **background shortcut learning** in classification, this project explicitly localized the clinically relevant lesion region before downstream prediction.

![Conclusion](assets/figure-03-conclusion.svg)

## My contribution

- Experimental pipeline implementation
- WSOL / weakly supervised localization experiments
- Domain-guided pseudo-label refinement
- Faster R-CNN retraining and evaluation
- Quantitative localization analysis
- End-to-end preprocessing-to-evaluation workflow

## Public outputs

- [`outputs/localization-public-technical-excerpt.pdf`](outputs/localization-public-technical-excerpt.pdf) — curated public technical excerpt containing non-clinical methodology and quantitative results.
- [`outputs/PROJECT_OUTPUTS.md`](outputs/PROJECT_OUTPUTS.md) — source manifest, evidence notes, and public-release scope.

## Data & privacy

No original patient-captured stoma images are included in this repository. Public materials are limited to diagrams, quantitative summaries, and curated non-identifiable artifacts.

---

**Junha Won** · Ajou University  
[Portfolio detail](https://juna0926.github.io/Portfolio/research/localization.html) · [Portfolio](https://juna0926.github.io/Portfolio/) · [GitHub](https://github.com/Juna0926)
