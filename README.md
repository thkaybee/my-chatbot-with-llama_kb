# My Chatbot with Llama

An end-to-end pipeline for generating domain-specific synthetic datasets and fine-tuning a Llama-based LLM to create a specialized conversational agent.

## 🚀 Features
* **Synthetic Data Generation:** Automated generation of valid Q&A pairs from raw text corpora (`politics.txt`, `chemistry-by-chapter.txt`).
* **Fine-Tuning Ready:** Pre-processes data into a standard structured JSON format (`finetune.json`) optimized for LLM training.
* **Custom Knowledge Base:** Tailored to respond accurately to niche domains like Chemistry and Politics.

## 📁 Repository Structure
* `generate_valid_questions.py` - Script to process text corpora and generate structured training questions.
* `finetune.json` - The compiled dataset used for training/fine-tuning the model.
* `chemistry-by-chapter.txt` & `politics.txt` - Raw source knowledge assets used for dataset generation.

## 🛠️ Getting Started

### Prerequisites
Make sure you have Python 3.x installed and the required dependencies:
```bash
pip install -r requirements.txt
