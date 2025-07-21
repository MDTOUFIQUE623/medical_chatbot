# Medical Chatbot

A web-based medical chatbot that leverages retrieval-augmented generation (RAG) using LangChain, Pinecone, and Google Generative AI to answer user queries based on medical documents.

## Features

- **Conversational Medical Assistant:** Answers user questions using context from uploaded medical PDFs.
- **RAG Pipeline:** Combines document retrieval (Pinecone) with generative AI (Google Gemini).
- **PDF Ingestion:** Loads and processes PDFs from the `data/` directory.
- **Web Interface:** Simple chat UI built with Flask.

## Setup

### 1. Clone the Repository

```bash
git clone <repo-url>
cd medical_chatbot
```

### 2. Install Dependencies

It's recommended to use a virtual environment.

```bash
pip install -r requirements.txt
```

### 3. Environment Variables

Create a `.env` file in the root directory with the following keys:

```
PINECONE_API_KEY=your_pinecone_api_key
GOOGLE_API_KEY=your_google_api_key
```

### 4. Prepare Data

Place your medical PDF files in the `data/` directory.

### 5. Index Documents

Run the following script to process PDFs and create the Pinecone index:

```bash
python store_index.py
```

### 6. Start the Web App

```bash
python app.py
```

The app will be available at [http://localhost:8080](http://localhost:8080).

## Project Structure

```
medical_chatbot/
│
├── app.py                # Main Flask app
├── store_index.py        # Script to process PDFs and build Pinecone index
├── requirements.txt      # Python dependencies
├── setup.py              # Packaging info
├── data/                 # Directory for PDF files
├── src/
│   ├── helper.py         # PDF loading, text splitting, embedding helpers
│   └── prompt.py         # Prompt template for the chatbot
├── static/               # Static files (CSS)
├── templates/            # HTML templates (chat UI)
└── .env                  # Environment variables (not committed)
```

## How it Works

1. **Indexing:**  
   - `store_index.py` loads PDFs, splits them into chunks, generates embeddings, and stores them in Pinecone.

2. **Chatbot:**  
   - `app.py` serves a Flask web app.
   - On user query, retrieves relevant document chunks from Pinecone.
   - Uses Google Gemini (Generative AI) to answer based on retrieved context.

3. **Prompting:**  
   - The system prompt is defined in `src/prompt.py` to ensure concise, context-based answers.

## Requirements

- Python 3.8+
- Pinecone account & API key
- Google Generative AI API key

## Author

- MD TOUFIQUE (ahmedtoufiqkhan37@gmail.com)
