# 📊 Intelligent Complaint Analysis for Financial Services

**CrediTrust Financial **


##  Project Objective

CrediTrust Financial receives thousands of customer complaints every month. Product managers, support teams, and compliance officers need a better way to extract actionable insights from this unstructured feedback.

This project develops a **Retrieval-Augmented Generation (RAG) chatbot** that lets internal teams:
- Query complaints in plain English.
- Retrieve the most relevant complaint narratives via semantic search.
- Generate evidence-based summaries and answers in seconds.


## Key Features

- **Supports 5 key product categories:**  
  - Credit Cards  
  - Personal Loans (including BNPL)  
  - Savings Accounts  
  - Money Transfers  
- **Uses real CFPB complaint narratives**
- **Vector similarity search** using embeddings and FAISS (or ChromaDB)
- **LLM-based answer generation** with robust prompt engineering
- **Gradio/Streamlit web app** for an intuitive user experience

###  Data Loading & EDA
- Loaded the full **CFPB complaints dataset** (~5.6 GB) in Colab.
- Filtered for the 5 relevant products: Credit card, Personal loan, BNPL, Savings account, and Money transfers.
- Cleaned the free-text narratives (lowercased, removed special characters, dropped boilerplate text).
- Analyzed narrative lengths by product to understand data quality.

###  Chunking & Embedding
- Tested **two chunking strategies**:
  - **Word-based chunker:** Fixed word count.
  - **Recursive chunker:** LangChain-style with overlap for better context.
- Embedded a sample of ~50,000 recursive chunks using `sentence-transformers/all-MiniLM-L6-v2`.
- Built a **FAISS index** for semantic search.
- Fixed metadata structure to link each vector to:
  - The original product category
  - The source row ID
  - The actual chunk text
- Saved:
  - Filtered dataset: `filtered_complaints.csv`
  - Vector index: `faiss_recursive_sample.index`
  - Metadata: `recursive_sample_metadata.pkl`

##  Next Steps

- Finalize the **RAG pipeline**:
  - Connect the retriever to an accessible LLM (Falcon, Llama, or local Mistral).
  - Run end-to-end tests with representative PM questions.
- Build an interactive **Gradio/Streamlit app** for internal use.
- Evaluate quality: log questions, retrieved sources, and AI answers.
- Package final scripts and generate a Medium-style report.

##  Key Tools

- **Python** 
- **Hugging Face Hub** (`sentence-transformers` for embeddings, `InferenceClient` for LLM)
- **FAISS** for vector similarity search
- **Pandas**, **Matplotlib**, **Seaborn** for EDA
- **Gradio/Streamlit** for upcoming UI

## Installation

```bash
pip install -r requirements.txt
```

