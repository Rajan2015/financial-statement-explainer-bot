# 📊 Financial Statement Explainer Bot

The Financial Statement Explainer Bot is a Retrieval-Augmented Generation (RAG) based application that helps users query financial statements and annual reports using natural language. It extracts, vectorizes, and indexes PDF documents and uses an LLM (GPT) to answer questions based on the document context.

## Features

- Upload and parse financial statement PDFs.

- Chunk and embed documents for semantic search.

- Query using natural language and receive grounded responses.

- Hallucination control using strict context-based prompts.

- Cache responses for faster performance.

- Works locally using FAISS or integrates with external Vector DBs (Pinecone, Azure Cognitive Search).

- Interactive UI with Streamlit (or optional FastAPI backend).

📂 Repository Structure
```
financial-statement-explainer-bot/
│
├── app/
│   ├── main.py                  # Entry point (FastAPI/Streamlit app)
│   ├── parser.py                # PDF/text extraction & cleaning
│   ├── chunker.py               # Chunking strategies
│   ├── embedder.py              # Embedding generation (OpenAI/HF)
│   ├── vectorstore.py           # Vector DB (FAISS/Pinecone/Azure)
│   ├── retriever.py             # Retrieval pipeline (top-k search)
│   ├── llm_client.py            # GPT model integration & prompts
│   ├── cache.py                 # Redis or in-memory caching
│   └── utils.py                 # Common helpers (logging, config)
│
├── data/
│   ├── samples/                  # Sample PDFs (annual reports)
│   └── processed/                # Parsed text/chunks (optional)
│
├── vectorstore/                  # Local FAISS index storage
│
├── ui/
│   └── streamlit_app.py          # Streamlit UI (if using)
│
├── tests/                        # Unit tests
│
├── requirements.txt              # Dependencies
├── .env                          # API keys (OpenAI/HF)
└── README.md                     # This file
```

## Getting Started

1️⃣ Clone the repo
```
git clone https://github.com/your-username/financial-statement-explainer-bot.git
cd financial-statement-explainer-bot
```
2️⃣ Create and activate virtual environment
```
python -m venv venv
source venv/bin/activate   # Linux/Mac
venv\Scripts\activate      # Windows
```
3️⃣ Install dependencies
```
pip install -r requirements.txt
```
4️⃣ Set up environment variables
Create a .env file:
```
OPENAI_API_KEY=your_api_key_here
```
5️⃣ Run the application

Option 1: Streamlit UI
```
streamlit run ui/streamlit_app.py
```
Option 2: FastAPI backend
```
uvicorn app.main:app --reload
```
## How It Works

- Parse PDFs using pdfplumber or PyMuPDF.

- Chunk text into smaller segments with overlap.

- Generate embeddings using OpenAI's text-embedding-3-small (or Hugging Face models).

- Store vectors in FAISS (local) or Pinecone/Azure Cognitive Search.

- On query:

    - Embed query and search top-k relevant chunks.

    - Pass retrieved chunks to GPT (e.g., gpt-4o-mini) with context.

    - Return grounded answer with sources.


## Tech Stack

- **LLM**: OpenAI GPT (gpt-4o-mini) / Hugging Face

- **Vector Store**: FAISS / Pinecone / Azure Cognitive Search

- **UI**: Streamlit / FastAPI

- **PDF Parsing**: pdfplumber / PyMuPDF

- **Caching**: Redis (optional)

## Future Enhancements

- Add visualization of financial metrics.

- Multi-document query support.

- Document version management.

- Role-based authentication.

## Contributing

Fork the repository

Create your feature branch (git checkout -b feature-name)

Commit your changes (git commit -m 'Add some feature')

Push to the branch (git push origin feature-name)

Open a Pull Request

## License

MIT License

## Contact

For queries or suggestions, feel free to reach out!
