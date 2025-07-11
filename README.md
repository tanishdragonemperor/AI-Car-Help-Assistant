# AI Car Help Assistant

This project showcases a prototype voice support agent for automotive customers. It
uses [LiveKit](https://livekit.io/) to stream audio between the user and an AI
assistant powered by large language models. A brief demo of the project can be
seen in [this LinkedIn post](https://www.linkedin.com/posts/tanish-gupta-a83167186_ai-genai-llm-activity-7293284753141567488-ORLQ).

## Features

- **Real‑time voice conversations** using the LiveKit voice assistant components.
- **Car profile lookup** by VIN and automatic profile creation if a vehicle is not
  found. Data is stored in a small SQLite database (see
  [`backend/db_driver.py`](backend/db_driver.py)).
- **LLM‑powered responses**: the backend defines tools in
  [`backend/api.py`](backend/api.py) that allow the agent to reason about car
  data and answer questions.
- **React + Vite frontend** that connects to the LiveKit room and renders the
  conversation (see [`frontend/src`](frontend/src)).

## Repository Structure

```
backend/   # Python Flask server and agent logic
frontend/  # React client built with Vite
```

Key backend components:

- `server.py` – issues LiveKit access tokens for clients.
- `agent.py` – runs the multimodal agent using the OpenAI plugin.
- `prompts.py` – prompt templates and welcome messages.

The frontend uses LiveKit React components to render a simple interface where a
user can enter their name and start talking to the assistant.

## Getting Started

1. **Environment variables** – copy `.env.example` files (if present) or create
   `.env` files for both the frontend and backend with the required values
   (LiveKit API key/secret, OpenAI key, etc.).
2. **Install dependencies**:

   ```bash
   pip install -r backend/requirements.txt
   npm install --prefix frontend
   ```

3. **Run the backend server**:

   ```bash
   uvicorn backend.server:app
   ```

4. **Start the agent worker** (in a separate terminal):

   ```bash
   python backend/agent.py
   ```

5. **Launch the frontend**:

   ```bash
   npm run dev --prefix frontend
   ```

The application will open in your browser (defaults to `localhost:5173`). After
entering your name you can speak to the assistant and it will respond in real
time.

## Why this project?

The goal of the AI Car Help Assistant is to demonstrate how modern LLMs can be
combined with real‑time voice technology to create a helpful, conversational
customer support experience. Recruiters and hiring managers can review the code
in this repository to see how LiveKit, Flask and React work together to deliver a
working prototype.

