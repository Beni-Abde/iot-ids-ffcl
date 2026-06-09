# IoT-IDS-FFCL — Deep Learning for Intrusion Detection in the Internet of Things

A scientific study comparing two deep learning approaches to intrusion detection in IoT networks, and an original proposal, **Federated Focal Continual Learning (FFCL)**, that unifies their strengths.

> **Nature of this project.** This is a research and state-of-the-art analysis project, not a software implementation. The repository contains the article and supporting material. The quantitative results discussed are those of the cited works; FFCL is a conceptual proposal whose empirical validation is left to future work.

## Overview

Learning-based intrusion detection in the IoT must overcome two obstacles that are usually treated in isolation:

- **Class imbalance** — attacks are a tiny minority of traffic (up to a 1:1000 ratio), which biases supervised learning toward benign flows.
- **Concept drift and distribution** — threats and benign behaviour evolve over time, while IoT networks are inherently distributed, so static and centralized models become obsolete.

This work analyses one representative approach for each obstacle, exposes their limits, and shows that they are *orthogonal* rather than competing.

| | Dina et al. (2023) | Soltani et al. (2024) |
|---|---|---|
| Tackles | class imbalance (focal loss) | concept drift (federated continual learning) |
| Architecture | centralized | distributed, multi-agent, federated |
| Training | offline / static | online / continual |
| Main weakness | rapid obsolescence | implementation complexity, compute cost |

## Contribution: Federated Focal Continual Learning (FFCL)

Soltani's agents train **locally with standard cross-entropy**, so an agent facing imbalanced sub-network traffic is biased before it ever shares its knowledge. **FFCL replaces that local cross-entropy with the focal loss**, so each agent learns its rare local attacks correctly, and this knowledge is then propagated to the global model through federated distillation. The result is a single framework that is robust to both class imbalance and concept drift.

## Repository contents

- `paper/FFCL_IoT_IDS_article.pdf` — the full article (formulas, architectures, results, proposal).
- `paper/FFCL_IoT_IDS_article.tex` — LaTeX source.
- `references.bib` — bibliography in BibTeX.

## Authors and supervision

Mohamed Ait Lhouari · Imad Baghdad · Abderrahman Benider · Youness Tourabi
École Centrale Casablanca — Scientific Project
Supervisor: Mme Kawtar Zerhouni

## References

See [`references.bib`](references.bib). Core sources: Dina et al. (2023, focal loss for IoT IDS); Soltani et al. (2024, multi-agent federated continual IDS); Lin et al. (2017, focal loss); McMahan et al. (2017, federated averaging); Kirkpatrick et al. (2017, elastic weight consolidation).