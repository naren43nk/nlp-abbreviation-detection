NLP Abbreviation Detection with BERT, BiLSTM, and CRF
This project focuses on token classification for biomedical abbreviation and long-form detection, using both classical and modern NLP approaches. Implemented as part of my NLP learning journey, the project explores the strengths and limitations of CRF, BiLSTM, and BERT models for span-level prediction on the PLOD-CW-25 dataset.

Problem Statement
The task is to identify abbreviations (B-AC) and their corresponding long forms (B-LF, I-LF) from biomedical text using BIO tagging. This is critical in medical NLP where domain-specific abbreviations are widespread and often ambiguous.

Dataset
Name: PLOD-CW-25 and PLODv2

Source: Hugging Face – bionlp/abbreviation-detection

Features: Token sequences with BIO tags for:

B-AC: Abbreviation start

B-LF: Long-form start

I-LF: Continuation of long-form

O: Outside

Additional POS tagging was used for feature enrichment in CRF and HMM models.

 Models Implemented
🔸 1. Conditional Random Field (CRF)
Feature-based tagging using POS, casing, prefixes, suffixes

High precision but weak at deep context modeling

F1 Score: 0.83

🔸 2. BiLSTM
Context-aware sequential tagging using:

Random embeddings

Pretrained GloVe vectors

Stronger generalization and recall than CRF

F1 Score: 0.86 (with GloVe)

🔸 3. BERT (Fine-Tuned)
Used bert-base-cased from Hugging Face Transformers

Subword-level tokenization with offset alignment

Trained using augmented dataset (PLODv2)

Best performance with F1 Score: 0.89

📊 Evaluation Summary
Model	Macro F1	Precision	Recall
Baseline	0.36	0.57	0.35
HMM	0.65	0.61	0.56
CRF	0.83	0.68	0.63
BiLSTM	0.71	0.76	0.72
BiLSTM + GloVe	0.86	0.86	0.87
BERT	0.89	0.94	0.89

 Key Learnings
CRF works well for structured patterns but lacks contextual flexibility

BiLSTM+GloVe strikes a great balance between efficiency and accuracy

BERT handles ambiguity and nested spans best, especially with proper token alignment

Subword tokenization brings accuracy but requires careful label mapping

 Deployment
Frontend: Built using Streamlit

Backend: Loads fine-tuned model directly from Hugging Face

Functionality: Users input sentences, model returns color-coded token tags

Logs: Sessions saved in .csv and .jsonl for reproducibility

Live Demo (if available): [Insert your own deployment link or remove]

Installation
1. Clone the repository
git clone https://github.com/YOUR_USERNAME/nlp-abbreviation-detection.git
cd nlp-abbreviation-detection
2. Install dependencies
pip install -r requirements.txt
3. Run the notebook
jupyter notebook COMM061_NLP_PG_33.ipynb
📁 Files Included
COMM061_NLP_PG_33.ipynb: Full implementation notebook

requirements.txt: List of required Python packages

/screenshots/: Visuals (optional)

 Future Improvements
Add CRF decoder to BERT for better BIO structure enforcement

Use BioBERT or domain-specific transformers

Explore span-based NER instead of token classification

Improve deployment with FastAPI and cloud-hosted inference

👤 Author
Narendran Mohan
MSc Data Science – University of Surrey
LinkedIn
📧 narenkarthi29776@gmail.com
