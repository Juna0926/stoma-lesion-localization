# Data-Efficient Stoma Lesion Localization via WSOL and Pseudo-Label Refinement with Domain Knowledge

> A data-efficient lesion-localization pipeline for smartphone-captured stoma images under limited bounding-box annotation.

**Period:** Feb. 2026 - Jun. 2026  
**Affiliation:** Machine Learning & Data Mining Laboratory, Ajou University  
**Type:** Collaborative medical-image research  
**Core methods:** WSOL · Domain-guided pseudo-label refinement · Faster R-CNN

---

## Overview

This research addressed lesion localization in a **limited-annotation setting** with only **15 bounding-box-labeled images** and **707 unlabeled smartphone-captured stoma images**. Rather than relying on exhaustive manual annotation, the study generated candidate lesion regions through weak supervision, refined them using stoma-specific domain knowledge, and used the retained pseudo-labels to train a final detector.

![Dataset structure](assets/figure-01-dataset-structure.svg)

## Research problem

Patient-captured stoma images vary in lighting, angle, distance, background, and image quality. At the same time, detailed lesion bounding-box annotation is expensive. The goal was therefore to build a pipeline that can learn clinically relevant lesion localization from **very limited bounding-box supervision** while making effective use of a much larger unlabeled image set.

## Method

1. **WSOL candidate generation** - generate candidate lesion regions from unlabeled stoma images.
2. **Domain-knowledge refinement** - evaluate candidates using stoma-specific signals including red-color prominence, luminance contrast, orientation, and center proximity.
3. **Pseudo-label retention** - retain candidates that satisfy the domain-informed refinement criteria.
4. **Faster R-CNN retraining** - use refined pseudo-labels as additional training supervision for the final lesion detector.
5. **Localization evaluation** - evaluate predicted regions with IoU and Dice Score.

## Main results

![Pseudo-label selection results](assets/figure-02-pseudolabel-results.svg)

- **673 / 707** candidate pseudo-labels were retained after domain-informed refinement.
- Final detector **mean IoU: 0.7796**
- Final detector **Dice score: 0.8681**

| Metric | Result |
|---|---:|
| Bounding-box-labeled images | 15 |
| Unlabeled images | 707 |
| Retained pseudo-labels | **673** |
| Mean IoU | **0.7796** |
| Dice score | **0.8681** |

## Research significance

The main contribution is the use of **domain-knowledge-guided pseudo-label refinement** to make lesion localization more data-efficient. Instead of treating weakly localized regions as equally reliable, the pipeline uses medically relevant image characteristics to filter candidate regions before detector retraining.

This research also followed naturally from the earlier stoma-classification study: after identifying background shortcut learning in classification, the next step was to explicitly localize the clinically relevant region before downstream prediction.

![Conclusion](assets/figure-03-conclusion.svg)

## My contribution

- Experimental pipeline implementation
- WSOL / weakly supervised localization experiments
- Domain-guided pseudo-label refinement
- Faster R-CNN retraining and evaluation
- Quantitative localization analysis
- End-to-end preprocessing-to-evaluation workflow

## Public outputs

- [`outputs/localization-public-technical-excerpt.pdf`](outputs/localization-public-technical-excerpt.pdf) - curated public technical excerpt containing non-clinical methodology and quantitative results.
- [`outputs/PROJECT_OUTPUTS.md`](outputs/PROJECT_OUTPUTS.md) - source manifest, evidence notes, and public-release scope.
- The original full presentation is not redistributed publicly because it contains clinical images.

## Data & privacy

No original patient-captured stoma images are included in this repository. Public figures are limited to diagrams, quantitative summaries, and curated non-identifiable materials.

---

**Junha Won** · Ajou University  
[Portfolio detail](https://juna0926.github.io/Portfolio/research/localization.html) · [Portfolio](https://juna0926.github.io/Portfolio/) · [GitHub](https://github.com/Juna0926)
