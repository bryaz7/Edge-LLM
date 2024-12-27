# LLM-AWQ Project

This repository demonstrates the application of **Activation-Aware Quantization (AWQ)** for compressing Large Language Models (LLMs). The project leverages the [MIT Han Lab's AWQ repository](https://github.com/mit-han-lab/llm-awq) without proposing or implementing any new methods.

---

## Overview

The goal of this project is to evaluate the AWQ technique for reducing LLM size while maintaining performance. AWQ is a novel quantization method that avoids fine-tuning, making it suitable for efficient deployment on resource-constrained devices.

---

## Background

### Large Language Models (LLMs)
LLMs are evaluated using **perplexity**, a metric indicating the model's ability to predict the next word:
- **Lower perplexity = better predictive performance.**

### Challenges in Quantization
- **Fine-tuning dependency**: Traditional methods often require fine-tuning, risking calibration dataset overfitting.
- **Scalability issues**: Existing techniques may not generalize well beyond the calibration dataset.

---

## About AWQ

**Activation-Aware Quantization (AWQ)** quantizes LLMs into **4-bit weights** and **16-bit activations**, focusing on:
1. Scaling only the 1% most salient weights (identified via activations).
2. Achieving compression without fine-tuning.

### Key Steps:
1. **Identify salient weights** using a small calibration dataset.
2. **Scale salient weights** before and after quantization to ensure accuracy.

---

## Experiments

### Models Tested
- **LLaMA 3-8B**
- **LLaMA 2-7B**
- **OPT-1.3B**
- **OPT-6.7B**
- **OPT-13B**

### Results
| Model       | Perplexity (FP16) | Perplexity (AWQ-INT4) | Size (FP16, GB) | Size (AWQ-INT4, GB) |
|-------------|-------------------|-----------------------|------------------|----------------------|
| LLaMA 3-8B  | 8.28              | 8.55                  | 16.1             | 5.4                  |
| LLaMA 2-7B  | 6.94              | 7.11                  | 13.5             | 3.7                  |
| OPT-1.3B    | 14.62             | 14.94                 | 2.6              | 0.8                  |
| OPT-6.7B    | 10.86             | 10.96                 | 13.3             | 3.6                  |
| OPT-13B     | 10.12             | 10.29                 | 25.7             | 6.7                  |

### Key Findings
- AWQ reduces model size significantly while maintaining low perplexity.
- Demonstrated practical deployment of quantized models on resource-constrained hardware.

---

## Repository Contents

- **`llm-awq-project.ipynb`**: Jupyter Notebook containing experiments, including:
  - Model quantization using AWQ.
  - Performance evaluation of compressed models.
- **Reference**: [LLM-AWQ GitHub repository](https://github.com/mit-han-lab/llm-awq).

---

## How to Use

1. Clone this repository:
   ```bash
   git clone https://github.com/bryaz7/Edge-LLM.git
   cd Edge-LLM
