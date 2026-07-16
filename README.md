# Symptom-to-Disease Prediction using RAG and LLM Fine-Tuning

A comparative study of **Retrieval-Augmented Generation (RAG)** and **parameter-efficient fine-tuning (QLoRA)** for symptom-to-disease prediction using **BioBERT**, **LLaMA-3.2**, and **LIME Explainability**.

This project evaluates the trade-offs between retrieval-based and fine-tuned language models for clinical decision support systems, focusing on **accuracy, scalability, and interpretability**.

---

## Features

- Comparative evaluation of **RAG**, **BioBERT**, and **Fine-Tuned LLaMA-3.2**
- Parameter-efficient fine-tuning using **QLoRA**
- Retrieval pipeline built using **Sentence Transformers** and **ChromaDB**
- Explainable predictions using **LIME**
- Performance comparison across **Symptoms2Disease** and **DDxPlus** datasets

---

## Architecture

```
                Symptoms
                    │
        ┌───────────┴────────────┐
        │                        │
        │                        │
 Fine-Tuned Models            RAG Pipeline
(BioBERT / LLaMA-3.2)             │
        │                  Sentence Embeddings
        │                         │
        │                    ChromaDB Search
        │                         │
        └────────────┬────────────┘
                     │
              Disease Prediction
                     │
              LIME Explainability
```

---

## Tech Stack

### Languages
- Python

### Machine Learning
- TensorFlow
- Hugging Face Transformers
- Sentence Transformers
- Unsloth
- PEFT (LoRA)
- QLoRA

### RAG
- ChromaDB
- Vector Embeddings

### Explainability
- LIME

### Data Processing
- Pandas
- NumPy
- Scikit-learn

---

## Datasets

### Symptoms2Disease

- 1,200 patient symptom descriptions
- 24 disease classes
- Used for BioBERT and LLaMA fine-tuning

### DDxPlus

- ~420K patient records used
- Evaluated scalability of the RAG pipeline
- Top 12 disease categories selected

---

## Project Structure

```
symptom-disease-rag/
│
├── notebooks/
│   ├── LLaMA_QLoRA_Finetuning.ipynb
│   └── LIME_Explainability.ipynb
│
├── report/
│   └── Minor_Project_Report.pdf
│
├── requirements.txt
└── README.md
```

---

## Results

| Model | Accuracy | Precision | Recall | F1 Score |
|--------|---------:|----------:|--------:|---------:|
| BioBERT | 89% | - | - | - |
| Fine-Tuned LLaMA-3.2 | **98.75%** | **98.93%** | **98.75%** | **98.69%** |
| RAG (Symptoms2Disease) | 42.9% | 37.9% | 38.1% | 33.3% |
| RAG (DDxPlus) | 78.3% | 83.9% | 78.3% | 77.3% |

---

## Key Findings

- Fine-tuned LLaMA achieved the highest performance on the structured Symptoms2Disease dataset.
- RAG significantly outperformed fine-tuned models when evaluated on the larger DDxPlus dataset, demonstrating better scalability to evolving knowledge bases.
- LIME explanations highlighted clinically relevant symptom features, improving prediction interpretability.

---

## Installation

Clone the repository

```bash
git clone https://github.com/<username>/symptom-disease-rag.git
cd symptom-disease-rag
```

Install dependencies

```bash
pip install -r requirements.txt
```

---

## Running the Project

Launch Jupyter Notebook

```bash
jupyter notebook
```

Run notebooks in the following order:

1. Data preprocessing
2. BioBERT prediction
3. LLaMA fine-tuning
4. RAG evaluation
5. LIME explainability

---

## Future Improvements

- Graph-RAG implementation
- Hybrid retrieval
- Multi-modal diagnosis using medical imaging
- Deployment as a REST API
- Web interface for interactive predictions
