# Model Training – Fine-Tuning SinoNômBERT

This folder contains the training scripts and configuration used to fine-tune a BERT-based language model on Vietnamese Chữ Nôm texts. The model is adapted from a pre-trained BERT model for ancient Chinese.

---

## Overview

Two training configurations are provided:

1. **`original_version.ipynb`**  
   - Fine-tunes the model on the original dataset, where each line corresponds to a single sentence or verse.
   - Lower context, higher perplexity.

2. **`concate_version.ipynb`**  
   - Fine-tunes the model on a modified dataset in which multiple lines are concatenated with `[SEP]` tokens.
   - Allows the model to learn across-sentence dependencies.
   - Yields better evaluation performance.

---

## Model Details

- **Base model:** [`btqkhai/Ancient-Chinese-BERT-wwm`](https://huggingface.co/btqkhai/Ancient-Chinese-BERT-wwm)
- **Tokenizer:** Custom tokenizer extended with additional Sino-Nôm characters (loaded from `../tokenizer/`)
- **Task:** Masked Language Modeling (MLM)
- **Framework:** Hugging Face Transformers + Datasets

---

## Training Configuration

| Parameter           | Value           |
|---------------------|------------------|
| Epochs              | 3                |
| Batch size          | 8                |
| Evaluation strategy | Every `n` steps |
| Warmup ratio        | 10%              |
| Masking probability | 15%              |
| Optimizer           | AdamW            |
| Logging             | TensorBoard / console logs |

---

## Evaluation Metrics

| Dataset Type        | Perplexity | Accuracy |
|---------------------|------------|----------|
| Original (line-by-line)   | 77.73      | 33.32%   |
| Concatenated (with [SEP]) | 48.25      | 39.33%   |

> Concatenating multiple lines improves both accuracy and perplexity due to better contextual learning.

---

## Files

- `original_version.ipynb`: Fine-tuning on original line-by-line dataset
- `concate_version.ipynb`: Fine-tuning on concatenated dataset with [SEP] tokens
- `README.md`: This documentation

---

## Notes

- Training was performed on Google Colab with NVIDIA A100 GPUs.
- Resulting models were saved locally and uploaded to Hugging Face:
  [SinoNômBERT](https://huggingface.co/btqkhai/SinoNomBERT)

---

## Suggestions

- Further improvements can be achieved with:
  - Larger training corpus
  - Longer training schedule
  - Embedding character-level features or phonetic components