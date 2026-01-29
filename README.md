# Multilingual Diabetes Management Chatbot using RAG
A retrieval-augmented, multilingual healthcare chatbot designed to provide diabetes-related guidance using trusted medical sources.
The system combines LLMs, semantic retrieval, empathetic prompting, and multilingual translation to generate safe, context-aware, and supportive responses for patient-style queries.
This is a graduate-level NLP project completed as part of the Natural Language Processing course at the University at Buffalo.
___

# Project Motivation
Diabetes management requires continuous education, lifestyle awareness, and emotional support.
However, access to personalized, multilingual, and empathetic medical guidance is limited—especially in low-resource settings.
This project explores how large language models (LLMs) combined with Retrieval-Augmented Generation (RAG) can help bridge this gap by:
Grounding responses in authoritative medical guidelines
Supporting multiple languages
Avoiding unsafe medical advice
Adapting responses to patient context (age, glucose level, symptoms, medications)
___

# System Overview
The chatbot architecture consists of four main components:
Medical Knowledge Base (RAG)
WHO and ADA diabetes guidelines
Chunked and indexed using semantic embeddings
Language Model
BLOOMZ-3B, an instruction-tuned multilingual LLM
Retrieval-Augmented Generation
Relevant medical passages are retrieved using FAISS
Retrieved context is injected into the prompt before generation
Empathetic & Personalized Prompting
Patient attributes (age, glucose level, symptoms, medications)
Safety-aware response design to avoid unsafe recommendations
___

# Datasets Used
1. Medical Knowledge Sources (RAG Corpus)
WHO – Management of Diabetes Mellitus: Standards of Care
ADA – Standards of Care in Diabetes (2024)
2. Training & Evaluation Data
MedQuAD – Medical question–answer pairs (diabetes-filtered)
MedicationQA (TrueHealth) – Drug-related Q&A
MedQA (USMLE-style) – Clinical reasoning QA
MedDialog-EN – Multi-turn medical dialogues
Custom Synthetic QA – Author-created diabetes scenarios
All datasets were normalized into a JSONL conversational format suitable for instruction tuning and evaluation.
___

# Methodology
🔹 Fine-Tuning
Framework: Hugging Face Transformers
Technique: Parameter-Efficient Fine-Tuning (LoRA)
Model: BLOOMZ-3B
Precision: FP16
Training Style: Instruction-based conversational formatting
🔹 Retrieval-Augmented Generation (RAG)
Embedding model: all-MiniLM-L6-v2
Index: FAISS
Top-k retrieval: 8 passages
Retrieved medical context appended to the prompt before generation
🔹 Multilingual Support
Translation pipelines using Helsinki-NLP Opus-MT
Supported languages:
English
Spanish
French
🔹 Safety & Personalization
Conservative response design (no dosage prescriptions)
Patient profile conditioning:
Age
Glucose level
Symptoms
Medications
___

# Evaluation
The system was evaluated on realistic patient-style queries across multiple languages.
Quantitative Metrics
BLEU: 0.00
(Expected for open-ended medical dialogue)
BERTScore (F1): 0.7873
(Indicates semantic relevance despite lexical variation)
Qualitative Evaluation
Tested on English, Spanish, and French patient profiles
Demonstrated:
Strong multilingual understanding
Safety-first behavior
Context-aware responses
Conservative handling of medical advice
Full experimental analysis and UI screenshots are available in the project report
NLP Report - Final
___


# Example Capabilities
Answers lifestyle and diet questions safely
Avoids unsafe medical recommendations
Adapts tone and content based on patient context
Handles multilingual input seamlessly
Grounds responses in authoritative medical documents
___

# Technology Stack
Python
PyTorch
Hugging Face Transformers
PEFT / LoRA
FAISS
Sentence Transformers
BLOOMZ-3B
Opus-MT (Multilingual Translation)
Jupyter Notebook
___

# Repository Structure
├── datasets_used/
│   ├── WHO.pdf
│   ├── ADA.pdf
│   ├── train.jsonl
│   ├── dev.jsonl
│   ├── test.jsonl
│   ├── US_qbank.jsonl
│   └── medDataset_processed.csv
│
├── part1_data_prepor.ipynb
│   └── Data preprocessing, dataset construction, embedding & retrieval
│
├── NLP_Milestone3_part2.ipynb
│   └── RAG pipeline, multilingual chatbot inference, evaluation
│
├── Report - Final.pdf
│   └── Full methodology, experiments, results, and discussion
│
├── Video Demo.mp4
│   └── End-to-end chatbot demonstration
│
└── README.md
___
# Authors
Kanisha Raja
M.S. Artificial Intelligence
University at Buffalo
Sai Deshith Sandakacharla
M.S. Artificial Intelligence
University at Buffalo

# Future Work
Multi-turn dialogue memory
Improved empathetic response modeling
Reinforcement learning from human feedback (RLHF)
Better dialogue-specific evaluation metrics
Expanded language support
