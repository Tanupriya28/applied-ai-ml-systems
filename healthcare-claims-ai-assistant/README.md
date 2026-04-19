#  Healthcare Claims AI Assistant

A GenAI-powered document question answering system that helps users query healthcare insurance policy PDFs and get instant answers related to claims, timelines, reimbursements, exclusions, and policy procedures.

##  Project Overview

Insurance policy documents are often lengthy and difficult to navigate manually. This project uses Retrieval-Augmented Generation (RAG) to extract relevant information from uploaded policy PDFs and generate accurate, grounded answers using an LLM.

Users can upload multiple insurance policy PDFs and ask natural language questions such as:

- What documents are required for claim submission?
- What is the emergency hospitalization claim intimation timeline?
- Summarize all reimbursement rules.
- What exclusions are mentioned in the policy?

---

##  Key Features

- Upload multiple PDF policy documents
- Ask questions in natural language
- Retrieval-Augmented Generation (RAG)
- Semantic search using embeddings
- Source citation with file name and page number
- Professional Streamlit UI
- Hallucination-controlled prompt engineering

---

##  Tech Stack

- Python
- Streamlit
- LangChain
- FAISS Vector Database
- HuggingFace Embeddings (`all-MiniLM-L6-v2`)
- Groq API
- Llama 3.1 8B Instant
- PyPDF

---

##  How It Works

Upload PDFs
↓
Extract text from documents
↓
Split into chunks
↓
Convert chunks into embeddings
↓
Store vectors in FAISS
↓
Retrieve top relevant chunks for user query
↓
LLM generates grounded answer
↓
Display answer + sources

###  Example Use Cases
- Healthcare claims support automation
- Insurance customer service assistant
- Internal policy lookup tool
- Claims operations productivity tool

###  Sample Questions
- What is the claim submission timeline?
- What documents are required for reimbursement claims?
- Compare hospitalization timelines across uploaded policies.
- What are the exclusions in this policy?


###  Installation
git clone <your-repo-link>

cd healthcare-claims-ai-assistant

pip install -r requirements.txt

streamlit run app.py

###  Environment Variables
Create a .env file:

GROQ_API_KEY=your_api_key_here

##  Future Enhancements
- OCR support for scanned PDFs
- Policy comparison dashboard
- Chat history memory
- Deployment on Streamlit Cloud
- Support for DOCX / Excel documents
