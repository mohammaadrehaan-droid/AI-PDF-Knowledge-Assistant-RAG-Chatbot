# AI-PDF-Knowledge-Assistant-RAG-Chatbot
AI PDF Knowledge Assistant built with n8n, Ollama (Llama 3), and Google Gemini Embeddings. This workflow allows users to upload PDF documents and ask questions, receiving clear AI-generated answers based on the document's content using RAG (Retrieval-Augmented Generation).
AI PDF Knowledge Assistant
An AI-powered document question-answering workflow built with n8n, Ollama (Llama 3), and Google Gemini Embeddings.

This workflow receives a PDF through a webhook, extracts its text, stores the document in a vector store, and uses an AI agent to answer questions based on the uploaded document.
Project Overview
The AI PDF Knowledge Assistant helps users ask questions about information inside a PDF document. The AI agent is instructed to answer using the uploaded file only and to clearly say when the answer cannot be found in the document.
Workflow
1. Webhook – Receives a POST request containing the PDF file.
2. Extract from File – Extracts text from the PDF.
3. Simple Vector Store – Stores the document in vector form.
4. Google Gemini Embeddings – Converts document text into embeddings.
5. Default Data Loader – Loads the extracted content as documents.
6. AI Agent – Processes the user's question and uses the document information to answer.
7. Ollama Chat Model (Llama 3) – Generates the response locally.
8. Respond to Webhook – Returns the AI agent's answer to the requester.
Technologies Used
- n8n – Workflow automation
- Ollama – Local AI model runtime
- Llama 3 – Chat model
- Google Gemini Embeddings – Text embedding model
- Simple Vector Store – Document vector storage
- Webhook – Input and response interface
- PDF text extraction – Document processing
How It Works
The user sends a PDF and a question to the webhook. n8n extracts the PDF text and processes it for vector storage. The AI agent then uses the document context to prepare a clear answer and returns it through the webhook.

The configured AI instructions aim to:
- Answer using information from the uploaded PDF only
- Avoid guessing or adding unsupported information
- Respond in English or Urdu/Roman Urdu based on the user's question
- Keep answers simple and relevant
- State when the answer is not available in the document
Setup
1. Install and run n8n.
2. Install and run Ollama.
3. Download the configured model:ollama pull llama3
4. Configure your Ollama credentials in n8n.
5. Configure Google Gemini API credentials for the embeddings node.
6. Import the workflow JSON file into n8n.
7. Check the webhook input and ensure the uploaded PDF is sent in the binary property named file.
8. Configure the AI Agent to receive the user's question along with the document context.
9. Test the workflow using the webhook test URL.
Example Use Case
Upload a PDF containing course notes and ask:
Explain the main topic discussed in this PDF.

The assistant returns an answer based on the document's content.
Notes
- This workflow uses Llama 3 through Ollama for chat responses.
- The embeddings node uses Google Gemini, so an API credential and internet connection are required for embeddings.
- The workflow currently uses the Simple Vector Store, which is an in-memory vector store.
- The exported workflow is inactive by default. Activate it in n8n when ready to use the production webhook.
- Ensure the webhook request includes both the PDF file and the user's question in the format expected by your n8n workflow.
Project Goal
To build a practical document-based AI assistant using workflow automation, embeddings, vector search, and a local language model.
