# Fastapi-pdf-chatbot
This project allows users to upload a PDF file, and then ask questions about its content via a chatbot interface. The chatbot reads the text from the PDF, processes it using LangChain, and responds intelligently using OpenAI’s API.

This repository contains a FastAPI application integrated with LangChain for question answering and document retrieval. The application allows uploading PDF files, extracting text, and querying for answers based on user input.

## Project's File Structure like :-
```
pdf-chatbot-fastapi/
├── app/
│   ├── main.py                ← FastAPI app setup
│   ├── pdf_reader.py          ← Reads and extracts text from PDF
│   ├── chain_handler.py       ← Handles LangChain chat logic
│   └── vector_store.py        ← Handles FAISS vector database
├── data/                      ← Folder to store uploaded PDFs
├── .gitignore                 ← Git ignore settings (more below)
├── LICENSE                    ← License info (more below)
├── README.md                  ← Project description & setup guide
├── requirements.txt           ← Python dependencies
└── .env                       ← API keys and config (not tracked in git)
```

## Basic Flow of the Project:-

1. User uploads a PDF
2. Text is extracted from the PDF.
3. Text is converted into embeddings using OpenAI + FAISS.
4. When user asks a question:
   
  -Query is embedded and matched with PDF chunks via similarity search.
  
  -Best matching chunks are fed to LangChain, and a response is generated.

5. Response is returned to user via the FastAPI backend.

### Endpoints

- **GET /get_documents/**: Retrieve a list of uploaded documents.
- **POST /upload_pdf/**: Upload a PDF file for processing.
- **WebSocket /ws/chat**: WebSocket endpoint for real-time question answering.

### Example Usage

1. Upload a PDF file using `/upload_pdf/` endpoint.
2. Connect to `/ws/chat` WebSocket endpoint using a WebSocket client.
3. Send a text message to ask a question and receive real-time answers.

## Technologies Used

- **FastAPI**: Web framework for building APIs with Python 3.7+.
- **LangChain**: Library for NLP tasks including question answering and document retrieval.
- **Chroma Vector Store**: Persistent storage for document embeddings.
- **PyPDF2**: Library for PDF file manipulation.
## Future Scope:
Some of the cool upgrades to be made in the project to make it look next-level:

| Feature                  | Description                                                   |
|--------------------------|---------------------------------------------------------------|
| 🔐 Authentication        | User login using JWT or OAuth2                                |
| 🗂️ Multi-PDF Support     | Let user select from multiple uploaded PDFs                   |
| 💾 Save Conversations    | Store chat history per user in a DB                           |
| 🧠 Use Local Embedding Model | Use SentenceTransformers instead of OpenAI                 |
| 🐳 Dockerization         | Make the app portable using Docker                            |
