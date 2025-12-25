# 📄 Document Controller  
**AI-Powered Document Processing & Tracking Workflow (n8n)**

The **Document Controller** is an automation workflow built with **n8n** that processes documents received via **Telegram**, analyzes them using **AI**, stores structured data in **Google Sheets**, uploads files to **Google Drive**, and manages document workflows using intelligent logic and scheduling.

This workflow is ideal for:
- Document intake and classification  
- AI-powered document analysis  
- Automated record keeping  
- File storage and tracking  
- Workflow-safe processing with fallbacks  

---

## 🌐 Overview

The Document Controller acts as a **document ingestion and control layer** between external sources (Telegram uploads) and internal storage systems.

It automatically:
- Receives documents
- Analyzes content using AI
- Stores results in Google Sheets
- Uploads files to Google Drive
- Handles missing or invalid data safely
- Routes documents based on content
- Supports scheduled processing

---

## ✨ Key Features

- 📥 **Telegram File Intake**
  - Accepts documents, images, and text
  - Trigger-based execution

- 🧠 **AI-Powered Analysis**
  - Text and image understanding
  - Document summarization
  - Intelligent classification

- 🗃️ **Google Sheets Logging**
  - Stores structured document data
  - Tracks status and metadata

- 📁 **Google Drive Upload**
  - Saves files automatically
  - Generates shareable links

- 🔀 **Conditional Logic**
  - Handles empty or invalid inputs
  - Routes documents intelligently

- ⏱️ **Scheduled Processing**
  - Supports cleanup and batch review

- 🛡️ **Fail-Safe Execution**
  - No crashes on missing data
  - Safe fallback logic in JavaScript

---

## 🧱 Architecture Overview

Telegram Trigger
↓
Download File
↓
AI Document Analysis
↓
Conditional Logic
↓
Store Metadata (Google Sheets)
↓
Upload File (Google Drive)
↓
Send Telegram Response
↓
Scheduled Review / Cleanup


---

## 🧩 Workflow Breakdown

### 1️⃣ Telegram Trigger
- Listens for incoming files or messages
- Supports:
  - Documents
  - Images
  - Text input

---

### 2️⃣ File Processing
- Downloads file from Telegram
- Extracts:
  - File name
  - File type
  - Content

---

### 3️⃣ AI Analysis
Uses an LLM to:
- Extract key information
- Summarize content
- Interpret images
- Classify documents

---

### 4️⃣ Conditional Routing
Logic decides:
- Whether to store the document
- Which path to follow
- Whether to notify or skip

---

### 5️⃣ Data Storage
Stored in **Google Sheets**:
- File name
- Analysis output
- Status
- Timestamp
- Source

---

### 6️⃣ File Upload
- Uploads to Google Drive
- Stores Drive URL
- Optional sharing enabled

---

### 7️⃣ Notifications
- Sends confirmation via Telegram
- Alerts on failures or success

---

### 8️⃣ Scheduled Processing
- Periodic review of stored documents
- Cleanup or reprocessing logic

---

## 🧠 Technology Stack

| Component | Purpose |
|----------|---------|
| **n8n** | Workflow automation |
| **Telegram Bot API** | File ingestion |
| **AI Model (Claude/OpenAI)** | Document analysis |
| **Google Sheets** | Metadata storage |
| **Google Drive** | File storage |
| **JavaScript Nodes** | Logic handling |
| **Cron Trigger** | Scheduled execution |

---

## 🗂️ Data Model

### Document Record
| Field | Description |
|------|-------------|
| `fileName` | Name of uploaded file |
| `fileType` | MIME type |
| `analysis` | AI-generated summary |
| `status` | processed / pending |
| `driveLink` | Google Drive URL |
| `createdAt` | Timestamp |
| `source` | Telegram |

---

## ⚙️ Setup Instructions

### 1️⃣ Import Workflow
n8n → Import → document controller.json


---

### 2️⃣ Configure Credentials
Add credentials for:
- Telegram Bot
- Google Drive
- Google Sheets
- AI Provider (Claude / OpenAI)

---

### 3️⃣ Prepare Google Sheet
Recommended columns:
- fileName  
- fileType  
- analysis  
- driveLink  
- status  
- timestamp  

---

### 4️⃣ Configure Telegram Bot
- Create bot via BotFather
- Add token to n8n
- Enable file access

---

### 5️⃣ Test the Workflow
Send a document to your Telegram bot and verify:
- AI analysis runs
- Sheet is updated
- File uploads to Drive
- Confirmation message is sent

---

## 📊 Example Output

```json
{
  "fileName": "contract.pdf",
  "analysis": "This document contains a service agreement...",
  "status": "processed",
  "driveLink": "https://drive.google.com/...",
  "source": "telegram"
}

---
⚠️ Common Issues & Fixes
| Issue              | Cause                | Solution            |
| ------------------ | -------------------- | ------------------- |
| File not processed | Bot permission issue | Reconnect Telegram  |
| AI fails           | Token expired        | Reauthorize API     |
| Sheet not updated  | Wrong Sheet ID       | Verify credentials  |
| Duplicate entries  | Missing validation   | Enable record check |
| Workflow stops     | Empty input          | Use fallback logic  |
