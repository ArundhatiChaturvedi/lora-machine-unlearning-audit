# Behavioral Forgetting Without Knowledge Removal: A Mechanistic Audit of LoRA-Based Machine Unlearning

Reference implementation accompanying the manuscript:

**Behavioral Forgetting Without Knowledge Removal: A Mechanistic Audit of LoRA-Based Machine Unlearning**

---

## Authors

**Rajan Gupta** *(First Author & Corresponding Author)*  
Artificial Intelligence and Innovation (AI&I) Laboratory  
Autonomous University of Tamaulipas (UAT), Mexico  
ORCID: https://orcid.org/0000-0002-9851-4047

**Arundhati Chaturvedi**  
Department of Computer Science and Engineering  
Vellore Institute of Technology (VIT), India  
ORCID: https://orcid.org/0009-0005-9921-9399

**Saibal K. Pal**  
Defence Research and Development Organisation (DRDO), India  
ORCID: https://orcid.org/0000-0003-3297-1605

---

## Overview

This repository contains the complete implementation used in our study on **LoRA-based machine unlearning for large language models (LLMs)**.

The work investigates whether current parameter-efficient unlearning methods genuinely remove hazardous knowledge or merely reduce its appearance under greedy decoding.

We evaluate multiple unlearning objectives across two LLM families using both behavioral and mechanistic analyses.

---

## Models Evaluated

- Zephyr-7B-Beta
- Llama-3-8B-Instruct

---

## Unlearning Methods

- Negative Preference Optimization (NPO)
- Fix C
- Sharpness-Aware Minimization (SAM + Fix C)
- Representation Misdirection for Unlearning (RMU)

---

## Evaluation Pipeline

The notebook implements the complete experimental pipeline used in the manuscript:

- LoRA training
- WMDP evaluation
- Leak@5 analysis
- Multi-seed evaluation
- Temperature sensitivity analysis
- Logit Lens analysis
- Attention attribution
- MLP neuron activation tracking
- Suppression Index (SI)
- Causal neuron ablation
- Strong Relearning attacks
- Unified Risk Score (URS)
- Statistical analysis

---

## Experimental Pipeline

```text
                 LoRA Training
                      │
                      ▼
          Behavioral Evaluation
             (WMDP Benchmark)
                      │
                      ▼
        Sampling Leakage Analysis
                (Leak@5)
                      │
                      ▼
      Mechanistic Interpretability
      ├── Logit Lens
      ├── Attention Attribution
      └── MLP Activation Tracking
                      │
                      ▼
          Causal Neuron Ablation
                      │
                      ▼
             Relearning Attack
                      │
                      ▼
          Unified Risk Score (URS)
```

---

## Repository Contents

```
Machine_Unlearning.ipynb
```

This notebook contains the complete implementation used to reproduce the experiments reported in the manuscript.

---

## Experimental Hardware

Experiments were performed across multiple GPU platforms during development.

Development and pilot experiments were carried out on:

- Kaggle (NVIDIA P100)
- Kaggle (Dual NVIDIA T4)
- JarvisLabs
- Vast.ai

The complete experimental pipeline was ultimately executed on a single **NVIDIA H100 80GB GPU** hosted through Vast.ai.

Earlier GPU configurations either exhausted available memory during training or required prohibitively long runtimes for repeated LoRA training and mechanistic analyses.

---

## Compute Summary

Approximate runtime of the final successful experimental pipeline:

| Stage | Approximate Runtime |
|--------|--------------------:|
| LoRA training | ~24 hours |
| Behavioral evaluation | ~2 hours |
| Mechanistic analysis | ~8 hours |
| Causal neuron ablation | ~3 hours |
| Relearning attacks | ~2 hours |
| **Total** | **~39 GPU hours** |

---

## Experimental Cost

Approximate total research compute expenditure (including pilot experiments, debugging, unsuccessful runs, and final experiments):

**₹27,796.61**

Final successful execution:

- Platform: Vast.ai
- GPU: NVIDIA H100 80GB
- Runtime: ~39 GPU hours
- Cost: **₹6,687.63**

---

## Requirements

Main libraries used:

- Python 3.10+
- PyTorch
- Hugging Face Transformers
- PEFT
- Datasets
- Accelerate
- NumPy
- Pandas
- SciPy
- Matplotlib

---

## Citation

If you use this repository, please cite the accompanying manuscript.

```bibtex
@article{gupta2026behavioral,
  title={Behavioral Forgetting Without Knowledge Removal: A Mechanistic Audit of LoRA-Based Machine Unlearning},
  author={Gupta, Rajan and Chaturvedi, Arundhati and Pal, Saibal K.},
  journal={Manuscript},
  year={2026}
}
```

---

## License

This repository is released under the MIT License.

---

## Contact

**Corresponding Author**

Rajan Gupta

Artificial Intelligence and Innovation (AI&I) Laboratory

Autonomous University of Tamaulipas (UAT), Mexico

Email: guptarajan2000@gmail.com

---

## Repository Maintainer

The implementation, experiments, and repository maintenance were carried out by **Arundhati Chaturvedi**.

For issues related to the code, please open a GitHub Issue in this repository.
