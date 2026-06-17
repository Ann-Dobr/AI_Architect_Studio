# 🏗️ AI Architect Studio

n8n-based tool for generating architecture and business process diagrams from text descriptions and images using AI.

## 📋 What it does

- Generates 7 diagram types from a text prompt: BPMN 2.0, Flowchart, Sequence, ER-Diagram, State, Use Case, C4 Context
- Accepts an image (PNG, JPG) as input — AI extracts the process description and builds a diagram from it
- Live Mermaid code editor — edit the generated diagram directly in the browser
- Export to SVG, PNG, HTML, and Markdown
- Clean dark-themed web UI served directly from n8n — no external frontend needed

## 🛠 Tech Stack

- **n8n** — workflow automation and web server
- **OpenAI GPT-4o** — diagram generation and image analysis
- **OpenAI Whisper** — voice input transcription *(requires HTTPS on a custom domain)*
- **Mermaid.js** — rendering flowcharts, sequence diagrams, ER diagrams, and more
- **bpmn-js** — rendering BPMN 2.0 diagrams with pan and zoom
- **Cloudflare Tunnel** — HTTPS access without exposing ports

## 📊 Architecture

<img width="1130" height="826" alt="image" src="https://github.com/user-attachments/assets/1e03b3a4-8a35-410f-a84d-388b11cdd7d2" />


## ⚙️ Key Features

- AI agent interprets free-form text and generates valid diagram code
- Image analysis — attach a screenshot or diagram and AI reconstructs it as editable code
- Switch-based routing handles diagram generation, image analysis, and voice transcription in a single workflow
- Two webhook triggers (GET + POST) keep diagram serving and file processing cleanly separated
- Base64 file encoding handled on the frontend — no binary data issues in n8n filesystem mode

## 📁 Files

- [`download_workflow.json`](download_workflow.json) — n8n workflow export (import directly into your n8n instance)

## ⚙️ Setup Requirements

- n8n instance (self-hosted)
- OpenAI API key (GPT-4o access required)

## 🔖 Notes

Voice input requires HTTPS on a custom domain due to browser MediaRecorder security restrictions — does not work on `trycloudflare.com` tunnels. PDF and DOCX file analysis is planned for a future version.
