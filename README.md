
# Personalized Medical Pre-Consultation via AI

This repository presents a comparative study of two AI-driven systems for automating the pre-consultation process in medical triage: a fine-tuned Large Language Model (LLM) and a Knowledge Graph-based semantic retrieval system. The goal is to dynamically generate follow-up questions and recommend the most appropriate specialist using only patient dialogue input.

---

## 🧠 Project Overview

We designed and implemented two separate pipelines:

- **Fine-Tuned LLM (LLaMA 3.2-3B + LoRA)** trained on weakly labeled medical dialogues for dynamic generation of questions and predictions.
- **Knowledge Graph (Neo4j + BioBERT embeddings)** that retrieves questions and specialists from previously matched similar cases.

This project compares their accuracy, adaptability, interpretability, and usability in real-world medical pre-consultation settings.

---

## 📁 Directory Structure

```
📁 llmtuning/               # Notebook for LoRA-based LLM fine-tuning (llmtuning.ipynb)
📁 truelabeling/            # Notebook for expert-guided labeling evaluation (truelabeling.ipynb)
📁 data/                    # Dialogue data and structured patient case information
📁 figures/                 # Architecture diagrams and comparative illustrations
📁 knowledge_graph/         # Neo4j setup, case embedding, and retrieval scripts (see KG.ipynb)
📄 requirements.txt         # Python dependencies
📄 README.md                # This file
```

---

## ⚙️ System Pipelines

### 🔷 1. Fine-Tuned LLM Pipeline
- **Labeling:** Uses Snorkel for weak supervision with keyword, TF-IDF, and zero-shot heuristics.
- **Training:** Fine-tunes Meta’s LLaMA 3.2-3B with LoRA adapters using Hugging Face Transformers.
- **Inference:** Takes patient dialogue as prompt, generates follow-up questions, and predicts a specialist.
- See: `llmtuning.ipynb`

### 🔶 2. Knowledge Graph Pipeline
- Refer to: `KG.ipynb` for end-to-end pipeline and graph construction.
- **Data Storage:** Neo4j graph with nodes: Case, Symptom, Question, Specialist.
- **Semantic Search:** Sentence embeddings (BioBERT) match incoming symptoms to previous cases.
- **Dialogue Replay:** Follows historic dialogue path and adapts based on patient responses.
- See: `knowledge_graph/`

---

## 📊 Evaluation Methodology

Evaluation was done using LLaMA 3.2-3B-Instruct in an expert simulation setting:
- Prompted as a senior medical expert.
- Rated each model’s question quality (scale 1–10).
- Judged specialist predictions as "Correct" or "Incorrect".

### 🧪 Results Summary

| Metric                             | Fine-Tuned LLM | Knowledge Graph |
|------------------------------------|----------------|-----------------|
| Specialist Accuracy                | 65%            | 70%             |
| Question Quality Score (1–10)      | 7.0            | 6.0             |

---

## 🖼️ System Architecture

Refer to `/figures/system_architecture.png` for a comparative visual.

---

## 🧪 Requirements

```bash
pip install -r requirements.txt
```

- Python 3.10+
- Transformers (Hugging Face)
- Neo4j + neo4j-driver
- SentenceTransformers
- Snorkel
- LoRA modules (PEFT)

---

## 🚀 Running the System

### Fine-Tuned LLM
```bash
# Inside llmtuning.ipynb:
# 1. Load dataset
# 2. Apply Snorkel labeling
# 3. Fine-tune with LoRA adapters
# 4. Inference using text-generation pipeline
```

### Knowledge Graph
```bash
# knowledge_graph/
# 1. Load Neo4j
# 2. Insert cases with embeddings
# 3. Run symptom matching queries
```

---

## ✍️ Authors

- Salma Salem  
- Malak El Samman  
- Rovan Ehab  
- Mohamed Youssef Hafez  
- Khadija Nasser

Department of Artificial Intelligence, Nile University – Egypt

---

## 📜 License

For academic and research purposes only. Contact authors for usage permissions.
