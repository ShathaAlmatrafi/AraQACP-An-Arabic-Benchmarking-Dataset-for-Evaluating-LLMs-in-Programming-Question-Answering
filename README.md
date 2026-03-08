# AraQACP: An Arabic Benchmarking Dataset for Evaluating LLMs in Programming Question Answering
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
![Language](https://img.shields.io/badge/Language-Arabic-blue)
![Domain](https://img.shields.io/badge/Domain-Python%20Programming-green)
![Platform](https://img.shields.io/badge/Platform-Jupyter%20Notebook-orange)
## Overview
**AraQACP** (Arabic Question Answering for Computer Programming) is a benchmarking dataset designed to evaluate the performance of Large Language Models (LLMs) on programming-related question answering in **Modern Standard Arabic**. The dataset focuses on **Python programming** and covers a wide range of knowledge points, question types, and learner levels.

This project addresses the scarcity of high-quality Arabic NLP benchmarks in the technical and programming domain by providing a curated, translated, and LLM-evaluated dataset of over **520 Python Q&A pairs** in Arabic.

---
## Dataset Description
The dataset was constructed by translating a Chinese Python Q&A corpus (`QACP`) into Arabic using an LLM-based translation pipeline, then using GPT models to generate reference answers and evaluate them.
### Dataset Files
| File | Description |
|------|-------------|
| `QACP_A.csv` | The original source dataset (base QACP corpus) |
| `QACP_Python_QA_zh_ar.csv` | Bilingual dataset with Chinese questions/answers alongside their Arabic translations |
| `QACP_Python_QA_ar_only.csv` | Arabic-only subset with questions and expert-translated reference answers |
| `QACP_Python_QA_ar_with_model_answers.csv` | Arabic dataset enriched with LLM-generated answers (`answer_model_ar`) |
| `QACP_Python_QA_ar_with_model_answers_scored.csv` | Final dataset including automated evaluation scores |
### Schema
Each record contains the following fields:
| Column | Description |
|--------|-------------|
| `id` | Unique question identifier |
| `Knowledge Point` | Python topic (e.g., *Introduction to Python*, *Lists*, *Functions*) |
| `Question Type` | Learner level: `Beginner` or `Experience in Programming` |
| `Answer Type` | Response format (e.g., `Explain in Detail`) |
| `question_ar` | Question in Modern Standard Arabic |
| `answer_ar` | Expert reference answer in Arabic (translated from Chinese) |
| `answer_model_ar` | LLM-generated answer in Arabic *(in enriched files)* |
| `score` | Automated evaluation score *(in scored file)* |
---
## Repository Structure
```
├── QACP_A.csv                                      # Original source dataset
├── QACP_Python_QA_zh_ar.csv                        # Chinese-Arabic bilingual dataset
├── QACP_Python_QA_ar_only.csv                      # Arabic-only Q&A pairs
├── QACP_Python_QA_ar_with_model_answers.csv        # With GPT-generated answers
├── QACP_Python_QA_ar_with_model_answers_scored.csv # With evaluation scores
├── Translating Chinese to Arabic.ipynb             # Translation pipeline notebook
├── Generating Answers on Python Questions.ipynb    # Answer generation notebook
└── Evaluating Answers Generated.ipynb              # Evaluation scoring notebook
```
---
## Methodology
The dataset was built in three main stages:
### 1. Translation — `Translating Chinese to Arabic.ipynb`
The original Chinese Python Q&A pairs were translated into Modern Standard Arabic using an LLM-based translation pipeline, producing `QACP_Python_QA_zh_ar.csv`.
### 2. Answer Generation — `Generating Answers on Python Questions.ipynb`
For each Arabic question, a GPT model (specifically `gpt-5-nano`) was prompted as an expert Python instructor to generate a reference answer in Modern Standard Arabic. The prompt was designed to:
- Always respond in clear, formal Modern Standard Arabic (no dialect)
- Keep all Python code, keywords, and identifiers in English
- Adapt explanations to the learner level (Beginner vs. Experienced)
- Include Python code examples when helpful
Over **520 questions** were processed and saved to `QACP_Python_QA_ar_with_model_answers.csv`.
### 3. Evaluation — `Evaluating Answers Generated.ipynb`
The generated answers were automatically scored by comparing them against the expert reference answers using an LLM-as-judge approach. Results were saved to `QACP_Python_QA_ar_with_model_answers_scored.csv`.

---
## Getting Started
### Prerequisites
- Python 3.10+
- Jupyter Notebook or JupyterLab
- An OpenAI API key
### Installation
```bash
git clone https://github.com/ShathaAlmatrafi/AraQACP-An-Arabic-Benchmarking-Dataset-for-Evaluating-LLMs-in-Programming-Question-Answering.git
cd AraQACP-An-Arabic-Benchmarking-Dataset-for-Evaluating-LLMs-in-Programming-Question-Answering
pip install pandas openai
```
### Running the Notebooks
Set your OpenAI API key before running the generation or evaluation notebooks:
```python
import os
os.environ["OPENAI_API_KEY"] = "your-api-key-here"
```
Then run the notebooks in order:
1. `Translating Chinese to Arabic.ipynb`
2. `Generating Answers on Python Questions.ipynb`
3. `Evaluating Answers Generated.ipynb`
---
## Use Cases
- **LLM Benchmarking**: Evaluate how well LLMs answer Python programming questions in Arabic.
- **Arabic NLP Research**: A resource for researchers working on Arabic technical language processing.
- **Educational Tools**: Basis for building Arabic-language Python tutoring systems.
- **Cross-lingual Studies**: Compare LLM behavior across Chinese, Arabic, and English in technical domains.
---
## Citation
If you use this dataset in your research, please cite:
```bibtex
@dataset{AraQACP2026,
  author    = {Taif AlWizainani, Afrah Almalki1, Ghaida Al-Luhaibi, Shatha Almatrafi, and Mourad Mars},
  title     = {AraQACP: An Arabic Benchmarking Dataset for Evaluating LLMs in Programming Question Answering},
  year      = {2026},
  url       = {https://github.com/ShathaAlmatrafi/AraQACP-An-Arabic-Benchmarking-Dataset-for-Evaluating-LLMs-in-Programming-Question-Answering}
}
```
---
## License
This project is open-source. Please refer to the repository for licensing details.
