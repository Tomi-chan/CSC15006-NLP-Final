# SinoNômBERT – Language Modeling for Vietnamese Chữ Nôm

Final project for the course **Introduction to Natural Language Processing (CSC15006)** at VNUHCM - University of Science.

---

## Group Members

| Student ID | Name              |
|------------|-------------------|
| 22120068  | Nguyễn Anh Đức     |
| 22120135  | Lê Quang Huy     |
| 22120147  | Bùi Trần Quang Khải    |
| 22120458  | Quách Hải Đăng     |

---

## Project Overview

This project aims to build a Vietnamese language model capable of understanding **Chữ Nôm**, the historical logographic script used in Vietnam, by adapting a BERT model pretrained on Ancient Chinese.

### Objectives

- Collect and preprocess large-scale Chữ Nôm textual data from public digital archives.
- Extend the vocabulary of an existing BERT tokenizer to support Sino-Nôm characters.
- Fine-tune a masked language model (MLM) using the cleaned Chữ Nôm corpus.
- Evaluate the model’s ability to predict masked tokens (accuracy & perplexity).

---

## Project Structure

```bash
CSC15006-NLP-Final/
├── data_acquisition/     # Web crawlers to collect raw Chữ Nôm text
├── preprocessing/        # Data cleaning, vocab extraction, tokenizer building
├── model_training/       # Fine-tuning BERT with MLM objective
├── report/               # Final PDF report
└── README.md             # This file

```

## Pipeline Summary

### 1. Data Acquisition
- Sources: `nomfoundation.org`, `chunom.org`, and other digital archives
- Data includes:
  - Historical records (e.g. History of Greater Vietnam)
  - Classical Vietnamese poetry (e.g. Hồ Xuân Hương, Trinh Phụ Ngâm Khúc)
- Tools: `requests`, `BeautifulSoup`, `Selenium` to parse and extract HTML-rendered content

### 2. Preprocessing & Tokenizer Construction
- Normalize and clean text data
- Extract unique Sino-Nôm characters and Unicode Private Use Area (PUA) glyphs
- Extend tokenizer vocabulary using Hugging Face's `add_tokens()` method
- Save customized tokenizer for use in downstream tasks

### 3. Model Fine-Tuning
- Base model: [`btqkhai/Ancient-Chinese-BERT-wwm`](https://huggingface.co/btqkhai/Ancient-Chinese-BERT-wwm)
- Task: Masked Language Modeling (MLM)
- Frameworks: Hugging Face Transformers & Datasets
- Training configuration:
  - Epochs: 3
  - Batch size: 8
  - Evaluation every N steps
  - Masking probability: 15%
- Datasets:
  - **Original format:** One sentence or verse per line
  - **Concatenated format:** Sentences merged using `[SEP]` to preserve context

### 4. Evaluation Results

| Dataset Type              | Perplexity | Accuracy |
|---------------------------|------------|----------|
| Original (line-by-line)   | 77.73      | 33.32%   |
| Concatenated (with `[SEP]`) | 48.25      | 39.33%   |

The concatenated format leads to better contextual understanding and more accurate predictions.

---

## Report

A full technical report is included in:

[`report/SinoNomBERT_Report.pdf`](./report/SinoNomBERT_Report.pdf)

It covers:
- Literature review on Chữ Nôm and classical Vietnamese
- Details on tokenizer customization
- Evaluation methodology and results
- Future research directions

---

## Dependencies

Install required libraries:

```bash
pip install transformers==4.47.0
pip install pandas==2.2.3