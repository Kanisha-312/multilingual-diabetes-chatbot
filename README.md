## Multilingual Diabetes Management Chatbot using RAG

**TL;DR**: A multilingual, safety-aware diabetes chatbot using BLOOMZ-3B + RAG over WHO/ADA guidelines, fine-tuned with LoRA and evaluated across English, Spanish, and French patient queries.

A retrieval-augmented, multilingual healthcare chatbot designed to provide diabetes-related guidance using trusted medical sources.
The system combines LLMs, semantic retrieval, empathetic prompting, and multilingual translation to generate safe, context-aware, and supportive responses for patient-style queries.
This is a graduate-level NLP project completed as part of the Natural Language Processing course at the University at Buffalo.

___

### Project Motivation
Diabetes management requires continuous education, lifestyle awareness, and emotional support.
However, access to personalized, multilingual, and empathetic medical guidance is limited—especially in low-resource settings.
This project explores how large language models (LLMs) combined with Retrieval-Augmented Generation (RAG) can help bridge this gap by:
- Grounding responses in authoritative medical guidelines
- Supporting multiple languages
- Avoiding unsafe medical advice
- Adapting responses to patient context (age, glucose level, symptoms, medications)

---
### 🎥 Short Demo Video

🔗 **Watch the demo:**  
[Multilingual Diabetes Chatbot – Video Demo](https://drive.google.com/file/d/1aFaVEWJ0wYZ6W0Poga5XFfPfdKWa369N/view?usp=sharing)

___

### Methodology

The multilingual diabetes chatbot is implemented using a Retrieval-Augmented Generation (RAG) pipeline with parameter-efficient fine-tuning to ensure medical grounding, personalization, and multilingual support.

#### Fine-Tuning

- Framework: Hugging Face Transformers  
- Technique: Parameter-Efficient Fine-Tuning (LoRA)  
- Base Model: BLOOMZ-3B (instruction-tuned multilingual LLM)  
- Precision: FP16  
- Training Style: Instruction-based conversational formatting using healthcare-specific prompts  

#### Retrieval-Augmented Generation (RAG)

- Embedding Model: all-MiniLM-L6-v2  
- Vector Index: FAISS  
- Top-k Retrieval: 8 semantically relevant passages  
- Authoritative medical documents from WHO and ADA guidelines are chunked, embedded, and retrieved at inference time  
- Retrieved context is dynamically appended to the prompt to ground responses in verified clinical knowledge  

#### Multilingual Support

- Translation pipelines implemented using Helsinki-NLP Opus-MT models  
- Supported Languages: English, Spanish, French  
- Queries are translated to English for retrieval and generation, then translated back to the user’s language  

#### Safety & Personalization

- Conservative response design to avoid unsafe or speculative medical advice  
- No medication dosage or diagnostic claims are generated  
- Responses are conditioned on patient-specific attributes:
  - Age  
  - Glucose level  
  - Symptoms  
  - Current medications  

___

### Datasets Used

#### 1. Medical Knowledge Sources (RAG Corpus)
- **WHO** – *Management of Diabetes Mellitus: Standards of Care*
- **ADA** – *Standards of Care in Diabetes (2024)*

#### 2. Training & Evaluation Datasets
- **MedQuAD** – Medical question–answer pairs (diabetes-filtered)
- **MedicationQA (TrueHealth)** – Drug-related question answering
- **MedQA** – USMLE-style clinical reasoning QA
- **MedDialog-EN** – Multi-turn medical dialogue dataset
- **Custom Synthetic QA** – Author-created diabetes-specific scenarios

These documents form the trusted clinical knowledge base used for retrieval-augmented generation (RAG).
___

### Evaluation
- **BERTScore (F1): 0.7873**
- The system was evaluated on realistic patient-style queries across multiple languages.
- Tested on English, Spanish, and French patient profiles
  
**Demonstrated:**
- Strong multilingual understanding
- Safety-first behavior
- Context-aware responses
- Conservative handling of medical advice
- Full experimental analysis and UI screenshots are available in the project report

**Example Capabilities**
- Answers lifestyle and diet questions safely
- Avoids unsafe medical recommendations
- Adapts tone and content based on patient context
- Handles multilingual input seamlessly
- Grounds responses in authoritative medical documents

___

### Technology Stack
- Python
- PyTorch
- Hugging Face Transformers
- PEFT / LoRA
- FAISS
- Sentence Transformers
- BLOOMZ-3B
- Opus-MT (Multilingual Translation)
- Jupyter Notebook

---

### Future Work
- Multi-turn dialogue memory
- Improved empathetic response modeling
- Better dialogue-specific evaluation metrics
- Expanded language support

---

### Authors

**Kanisha Raja**  
Master’s in Artificial Intelligence, University at Buffalo

**Sai Deshith Sandakacharla**  
Master’s in Artificial Intelligence, University at Buffalo

