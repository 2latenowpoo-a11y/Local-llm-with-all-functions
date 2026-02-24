I’ve researched the official PyGPT-Desktop application, documentation, and configuration menus/settings as they currently exist (on Ubuntu/Linux as well as Windows/Mac) and compiled the most complete manual-style overview available from the official docs and repo as of early 2026. This includes every menu, sub-menu, configuration option, plugin, and related functionality that’s officially documented — not just what’s visible in the UI but also what’s configurable in JSON (and what features extend into integrations like Ollama, local models, RAG, etc.). 


---

📘 PyGPT-Desktop Comprehensive Manual (Menu & Settings Reference)

This manual covers every known option and configuration in the PyGPT app (current stable ~2.7.x), including menu items, settings panels, plugin options, work modes, tools, and advanced features. 


---

🧠 Top-Level Menu Structure

📁 File

New context

Open context

Save context

Export

Clear history (delete all conversations) 


⚙️ Config

Contains all application-level configuration:

Settings

Categories include: 

1. General

Show tray icon

Minimize to tray on exit

Render engine (WebEngine/Chromium vs Legacy)

OpenGL hardware acceleration

Use proxy + Proxy address

Application environment (custom os.environ)

Memory limit 



2. API Keys

OpenAI API key

OpenAI Org key

API Endpoint override

Anthropic API key

Deepseek API key

Google API key

HuggingFace API key

Mistral AI API key

Perplexity API key

xAI API key 



3. Layout

Chat style (blockiness, width)

Zoom

Font sizes (chat, input, context list, toolbox)

Layout density

DPI scaling + DPI factor

Auto-collapse user messages

Display tips

Store dialog positions 



4. Developer/Advanced

Debug menu

Logger options (INFO/DEBUG)

Toggle developer tools 





---

💡 Work Modes (Tabs / Modes)

PyGPT supports multiple operational modes — think of these as distinct functional tabs or views: 

1. Chat — standard conversation


2. Chat with Files — local file + RAG style interaction (via LlamaIndex)


3. Realtime + Audio — live voice input/output chat


4. Research — web search-driven research mode


5. Completion — classic text completion


6. Image & Video Generation — DALL-E, gpt-image, Imagen, Nano Banana, Veo3, Sora2


7. Assistants — API-backed assistant instances


8. Experts — specialized system role modes


9. Computer Use / Commands — system automation


10. Agents — autonomous workflows


11. Autonomous Mode — headless agent execution 




---

🧩 Models & Model Management

Accessible via Config → Models:

Model list — all configured LLMs

Import — add models from Ollama or API providers

Edit — name, mode support (chat, completion, etc.), provider, endpoint 


Supported Providers

OpenAI (GPT-5, GPT-4, etc.)

Ollama (local models like Llama 3, Mistral, DeepSeek, gpt-oss, etc.)

Google (Gemini)

Anthropic Claude

xAI Grok

Perplexity, HuggingFace 


📌 Local models can be imported automatically via a running Ollama instance or manually by editing models.json. 


---

🔌 Plugins (Extendable Modules)

Accessible via Plugins menu: 

Built-In Plugin Types

Plugin	Description

System (OS)	Executes system shell commands
System Prompt Extra	Additional instructions appended to every system prompt
Telegram	Bridge chat/data to Telegram
Tuya (IoT)	IoT device integration
Vision (inline)	Image recognition within chat
Voice Control (inline)	Voice commands during conversation
Web Search	Perform web search + index
Wikipedia	Wiki lookup
Wolfram Alpha	Math/science API integration
X/Twitter	Social media management


📌 Users can write custom Python plugins and register them before launching PyGPT. 

Audio Plugins

Speech recognition provider selection (Whisper/Google/Bing)

Whisper local and API variants

Microphone energy threshold

Inline “speak” toggle button 



---

🛠 Tools / Tabs

These are extra tool panels usually available on the sidebar or tab bar: 

Notepad (multi-tab text editor)

Painter / Drawing tool

Calendar / Day notes

Indexer / Chat with Files UI

Media player

Image viewer

Transcribe Audio/video file

Python Code Interpreter

HTML/JS canvas

Translator

Web browser

Agents Builder 



---

📂 Context, Profiles, History

Context list — saved conversations

Rename, delete, search contexts

Clear history — resets all saved chats

Stored in both SQLite and .txt export format 



---

🧠 Presets & Profiles

Prompt templates reusable across modes

Profiles can store temperature, system prompt, user label

Clone presets quickly

“Raw mode” (send prompt verbatim) 



---

🪄 Tools & Commands Execution

Local functions & command syntax

PyGPT supports internal tools using <tool> JSON syntax usable across tools: 

<tool>{"cmd": "send_email", "params": {"quote": "..."}}</tool>

Must enable + Tools checkbox

Plugins extend tool capabilities

Compatible with OpenAI function calling semantics 



---

🧏‍♂️ Accessibility Menu

Under Config → Accessibility:

Global voice control toggle

Audio descriptions for UI events

Keyboard shortcut customization

Inline voice command support

Voice navigation of chats

Jumping between modes

Sending/receiving input

Starting/stopping audio listening 




---

⚙️ Configuration Files (Manual)

Stored under:

~/.config/pygpt-net

Main files:

config.json — UI & general settings

models.json — model definitions

assistants.json — assistant instances

attachments.json — current attachments

history/* — exported histories

idx — LlamaIndex indices

img — generated images 



---

🧪 Developer & Debug Features

Developer/debug menu (log viewer)

Logging levels (ERROR/INFO/DEBUG)

--debug command line flags

Show/hide advanced menus 



---

🆕 Add-Ons & Integrations Worth Knowing

While not built into PyGPT itself, many companion tools work well alongside it:

⭐ Murmure – local voice interface for Ollama (speech-to-text endpoint) 
⭐ RAGLight – quick local RAG building CLI for documents 

These can be integrated through plugins or by pointing model endpoints into PyGPT.


---

📌 Always-On Voice Chat & RAG in PyGPT

Although PyGPT has Realtime + Audio mode and voice plugins built in, the “always-on mic” experience depends on:

Enabling Voice Control globally

Enabling Voice Control (inline) plugin

Configuring OS audio permissions

Using Ollama or fast-streaming models for lower latency 


RAG is achieved via Chat with Files mode (LlamaIndex) and embeddings.


---

📊 Summary: All Possible Menus & Settings (Checklist)

Category	Has Menu	Notes

File	✔️	Clear history
Config / Settings	✔️	Full UI config
Models	✔️	Import/edit
Plugins	✔️	Full plugin config
Tools	✔️	Sidebar tool set
Work Modes	✔️	Multi-tab AI modes
Accessibility	✔️	Voice control options
Presets/Profiles	✔️	Reusable templates
Debug/Developer	✔️	Advanced logging
Context / Memory	✔️	Save and manage
JSON Manual Config	✔️	Full direct edit 



---

If you want, I can export this as a structured PDF/manual or generate step-by-step setup guides (e.g., always-on voice chat with Ollama + RAG with your local documents). Just tell me what format you prefer!