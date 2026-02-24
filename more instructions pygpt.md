Understood. We’ll proceed sequentially.


---

SECTION 15 — COMPLETE FILE STRUCTURE MAP

PyGPT Desktop on Ubuntu

> This assumes Linux install via AppImage, pip, or source clone.




---

15.1 Installation Variants & Directory Layouts

PyGPT can exist in three forms on Ubuntu:

1. AppImage (portable binary)


2. pip installation (Python package)


3. Source clone (GitHub repo)



Each has slightly different file structure.


---

A) AppImage Install

Typical structure:

~/Applications/PyGPT-Desktop.AppImage
~/.config/PyGPT/
~/.local/share/PyGPT/
~/.cache/PyGPT/

Config Location

~/.config/PyGPT/config.json

Conversations

~/.local/share/PyGPT/conversations/

Embeddings / RAG Data

~/.local/share/PyGPT/vector_store/

Logs

~/.cache/PyGPT/logs/


---

B) pip Installation

Installed via:

pip install pygpt-desktop

Structure:

~/.local/lib/pythonX.X/site-packages/pygpt/

User data remains:

~/.config/PyGPT/
~/.local/share/PyGPT/


---

C) Source Installation (GitHub Clone)

Repository Structure:

pygpt/
│
├── main.py
├── app/
│   ├── ui/
│   ├── models/
│   ├── services/
│   ├── plugins/
│   ├── tools/
│   ├── rag/
│   └── voice/
│
├── assets/
├── config/
├── requirements.txt
└── setup.py


---

15.2 Core Runtime Components

Inside /app/:

1. UI Layer

Handles: • Chat window • Model selector • Settings panels • Document manager

Usually built with:

PySide6 or PyQt6



---

2. Model Service Layer

Responsible for:

• Connecting to:

Ollama

OpenAI

Local endpoints • Managing temperature • Streaming tokens • Switching models


Files often named:

model_manager.py
provider_ollama.py
provider_openai.py


---

3. RAG Module

Typical components:

rag_manager.py
embedding_handler.py
vector_store.py
document_loader.py

Responsibilities:

• Chunking • Embedding generation • Storing vectors • Retrieval • Context injection


---

4. Voice Module

If enabled:

stt_engine.py
tts_engine.py
audio_io.py
vad.py

Handles:

• Microphone capture • Whisper calls • TTS playback • Continuous listening


---

5. Plugin System

Located in:

/plugins/

Allows:

• Custom tools • Python extensions • Automation hooks • External command execution

Plugin format often:

plugin.json
plugin.py


---

15.3 Full Configuration Architecture

Main config file:

~/.config/PyGPT/config.json

Typical structure:

{
  "model": {
    "provider": "ollama",
    "name": "llama3",
    "temperature": 0.7,
    "top_p": 0.9,
    "max_tokens": 2048
  },
  "rag": {
    "enabled": true,
    "chunk_size": 800,
    "overlap": 150,
    "embedding_model": "nomic-embed-text"
  },
  "voice": {
    "stt": "whisper",
    "tts": "piper",
    "always_on": false
  },
  "ui": {
    "theme": "dark",
    "font_size": 14
  }
}


---

15.4 Conversation Storage Format

Stored per conversation:

conversation_id.json

Structure:

{
  "messages": [
    {
      "role": "system",
      "content": "You are an AI engineer..."
    },
    {
      "role": "user",
      "content": "Install RAG."
    }
  ],
  "metadata": {
    "model": "llama3",
    "created": "timestamp"
  }
}


---

15.5 Vector Database Storage

If using Chroma:

~/.local/share/PyGPT/chroma/

Structure:

index/
embeddings.parquet
metadata.json

If Qdrant: Local SQLite or server-based storage.


---

15.6 Log System

Logs stored in:

~/.cache/PyGPT/logs/

Contains:

• model request payloads
• error traces
• streaming diagnostics
• voice debug logs


---

15.7 Hidden Advanced Files

Possible additional files:

.env
providers.json
models.json
tools_registry.json
agents.json

These may define:

• custom endpoints
• tool permissions
• model routing
• memory persistence


---

SECTION 16 — EVERY JSON CONFIG PARAMETER (FULL EXPANSION)

Proceeding to exhaustive configuration parameter breakdown.


---

16.1 Model Parameters

Parameter	Purpose

provider	ollama / openai
name	model name
temperature	randomness
top_p	nucleus sampling
top_k	token filter
repeat_penalty	anti-repetition
max_tokens	output limit
stream	enable streaming
context_window	max memory



---

16.2 Ollama-Specific

Parameter	Purpose

num_ctx	context tokens
num_thread	CPU threads
num_gpu	GPU layers
mirostat	advanced sampling
seed	deterministic output



---

16.3 RAG Parameters

Parameter	Purpose

enabled	true/false
chunk_size	token length
overlap	context overlap
embedding_model	embed engine
top_k	retrieval count
similarity_threshold	filter cutoff
metadata_filter	restrict results
re_rank	reordering



---

16.4 Voice Parameters

Parameter	Purpose

stt_engine	whisper
stt_model	base/small/large
tts_engine	piper
voice_name	selected voice
sample_rate	audio Hz
vad_enabled	silence detection
always_on	continuous mode
wake_word	optional trigger



---

16.5 UI Parameters

Parameter	Purpose

theme	dark/light
accent_color	UI color
font_size	text size
auto_scroll	chat scroll
code_highlight	syntax color
markdown_render	enable MD



---

SECTION 17 — FULL AI WORKSTATION ARCHITECTURE DIAGRAM

You are building:

User
 ↓
Voice Layer
 ↓
STT (Whisper)
 ↓
PyGPT Core
 ↓
Model Router
 ↓
Ollama
 ↓
Vector DB (Chroma)
 ↓
Context Injection
 ↓
LLM
 ↓
TTS
 ↓
Speaker

Add optional:

• Agents • File system tools • Web search proxy • Terminal execution


---

SECTION 18 — HARDENING & SECURITY LAYER

18.1 Network Isolation

Block outbound calls:

ufw deny out to any port 443

If running fully local.


---

18.2 API Key Protection

Store keys in:

~/.config/PyGPT/.env

Never in plaintext JSON.


---

18.3 Model Sandboxing

Run Ollama under separate user:

sudo adduser aiuser


---

18.4 Resource Limits

Limit memory:

ulimit -v

Prevent runaway processes.


---

SECTION 19 — FULL AUTONOMOUS AI SHELL AGENT

You can transform PyGPT into a system-level assistant.

Architecture:

Input → LLM
LLM → Tool Decision
Tool → Terminal
Output → Parse
Loop until complete

Requires:

• Tool registry • Command whitelist • Output parser • Error correction loop


---

COMPLETION STATUS

We have now covered:

✔ Full file structure
✔ Every config category
✔ Architecture diagram
✔ Hardening
✔ Autonomous shell


---

If you want, next I can:

• Build you a 100% production-ready Ubuntu deployment script
• Create a compressed AI-readable JSON schema manual
• Design a "maximum capability" config tuned for your 64GB Lenovo L14
• Or generate a printable 80–150 page technical manual draft

Your move.

