###📄 Document Controller

AI-Powered Document Processing & Tracking Workflow (n8n)

The Document Controller is an advanced automation workflow built with n8n that processes documents sent via Telegram, analyzes them using AI, stores structured data in Google Sheets, uploads files to Google Drive, and manages follow-up logic through intelligent routing and scheduling.

This workflow acts as a document ingestion and analysis pipeline, ideal for:

- Internal document processing
- Knowledge ingestion
- AI-powered document classification
- Automated record keeping
- Scheduled reviews and follow-ups
---

##🌐 Overview

This workflow listens for incoming documents via Telegram, analyzes their content using an AI model, extracts meaningful data, and stores results in Google Sheets while optionally uploading files to Google Drive.

It supports:

- File-based ingestion (PDFs, images, documents)
- AI-powered text and image analysis
- Conditional logic based on document content
- Persistent storage and tracking
- Automated notifications
- Scheduled processing and cleanup
---

##✨ Key Features

📥 Telegram File Intake
Accepts documents and images sent via Telegram

  🧠 AI-Powered Analysis

Text understanding (Claude / LLM)

Image understanding

Content classification

🗃️ Google Sheets Integration

Stores extracted metadata

Tracks document status

Supports updates and lookups

📁 Google Drive Upload

Automatically uploads files

Shares files when required

🔀 Conditional Routing

Different logic paths based on content

Handles empty or invalid files safely
