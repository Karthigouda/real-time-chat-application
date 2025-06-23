# 🧠 Real-Time Chat App with OpenAI Realtime API

A low-latency, real-time chat (text and audio) app powered by OpenAI’s Realtime API via WebSockets.

Leveraging a backend relay server to secure API keys and streamline token-based streaming.

---

## 🚀 Features

- Persistent WebSocket connection to OpenAI Realtime API  
- Real-time streaming of text *and/or* audio messages  
- Support for token-by-token “delta” streaming  
- Handles conversation lifecycle events  
- Optional function calling for enriched functionality  

---

## 💡 How It Works

1. Establish a secure WebSocket to `wss://api.openai.com/v1/realtime...`  
2. Send events for user input (`conversation.item.create`)  
3. Prompt model responses with `response.create`  
4. Stream responses in chunks using `response.text.delta`, `response.text.done`, and `response.done` :contentReference[oaicite:1]{index=1}  
5. Optionally, handle streamed audio input/output :contentReference[oaicite:2]{index=2}  
6. Use a relay (Express or FastAPI) to secure API key usage :contentReference[oaicite:3]{index=3}  

---

## 🧩 Tech Stack

| Role      | Tech                   |
|-----------|------------------------|
| Server    | Node.js + Express or Python + FastAPI |
| Client    | Browser WebSocket or custom UI         |

Example repos:
- 🧱 Node relay: `smaameri/openai-realtime-api-websocket-server` :contentReference[oaicite:4]{index=4}  
- 🐍 Python FastAPI audio relay: sample in Online tutorials :contentReference[oaicite:5]{index=5}

---

## 🔧 Getting Started (Node.js Example)

### 📋 Prerequisites
- Node.js v18+, npm  
- Realtime API access (public beta) :contentReference[oaicite:6]{index=6}  
- Your OpenAI API key

### 🛠️ Setup
```bash
git clone <your-repo>
cd your-repo
npm install
cp .env.example .env
# In .env: set OPENAI_API_KEY and optionally REALTIME_MODEL and REALTIME_URL
node index.js
