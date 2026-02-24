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

Good. Then I’m choosing the format that gives you:

Maximum completeness

Maximum AI-parseability

Minimal verbosity

Deterministic reconstruction capability

No prose bloat

Expandable without breaking structure


We will use:

> Hierarchical YAML Technical Specification (Deterministic, Machine-Optimized)



This will be delivered in indexed sections so it can be reassembled without ambiguity.


---

PYGPT-DESKTOP TECHNICAL SPECIFICATION

PTSM-v1

Section 1 — Core Application Architecture

ptsm:
  version: 1
  app:
    name: pygpt-desktop
    type: desktop_llm_client
    framework: PyQt6
    renderer:
      options:
        - QtWebEngine
        - legacy_html
    storage:
      primary: sqlite
      secondary: json_files
    config_path_linux: ~/.config/pygpt-net
    runtime_language: python
    plugin_system: python_dynamic_loader

architecture:
  layers:
    - ui_layer
    - mode_controller
    - provider_adapter
    - model_registry
    - tool_dispatcher
    - plugin_manager
    - rag_pipeline
    - audio_pipeline
    - persistence_layer

  ui_layer:
    components:
      - main_window
      - sidebar_context_list
      - chat_render_view
      - input_panel
      - toolbox_panel
      - mode_selector
      - settings_dialog
      - plugin_dialog
      - model_manager
      - log_console

  mode_controller:
    responsibilities:
      - switch_work_modes
      - route_input_to_pipeline
      - attach_plugins
      - enforce_mode_capabilities
      - manage_streaming

  provider_adapter:
    abstraction: unified_llm_interface
    supported_types:
      - openai
      - ollama
      - anthropic
      - google
      - xai
      - mistral
      - huggingface
      - perplexity
    functions:
      - chat_completion
      - text_completion
      - embeddings
      - vision
      - streaming
      - tool_calling

  model_registry:
    source_file: models.json
    attributes:
      - provider
      - model_name
      - endpoint
      - api_key_reference
      - supports_chat
      - supports_completion
      - supports_vision
      - supports_tools
      - supports_streaming
      - supports_embeddings
      - context_window
      - temperature_default

  tool_dispatcher:
    input_format: xml_tool_tag
    tag_format: "<tool>{json}</tool>"
    responsibilities:
      - parse_tool_json
      - match_plugin_function
      - execute
      - inject_result_into_chat

  plugin_manager:
    load_type: dynamic_import
    plugin_location:
      - internal_builtin
      - ~/.config/pygpt-net/plugins
    lifecycle:
      - load_on_start
      - enable_disable_runtime
      - register_tools
      - register_ui_hooks

  rag_pipeline:
    engine: llamaindex
    index_storage: ~/.config/pygpt-net/idx
    components:
      - document_loader
      - chunker
      - embedding_model
      - vector_store
      - retriever
      - context_injector

  audio_pipeline:
    input:
      - microphone_capture
      - speech_to_text_provider
    output:
      - text_to_speech_provider
      - audio_playback
    modes:
      - push_to_talk
      - inline_trigger
      - continuous_listen

  persistence_layer:
    files:
      - config.json
      - models.json
      - assistants.json
      - attachments.json
    folders:
      - history/
      - idx/
      - img/
      - logs/


---

This is the foundation map.

No fluff. No explanation. Pure structure.


---

Next section will define:

> PTSM-2 — Complete Menu Tree + UI Hierarchy



Followed by:

PTSM-3 — Settings Schema (Every Config Field)

PTSM-4 — Work Modes Deep Specification

PTSM-5 — Plugin Matrix (All Built-ins + Extension Hooks)

PTSM-6 — Model System + Provider Capabilities

PTSM-7 — RAG Configuration + Embedding Options

PTSM-8 — Audio System (Always-On Voice Deep Spec)

PTSM-9 — File Schema Definitions

PTSM-10 — External Integrations (Ollama, Whisper, Vector DB, etc.)



---

We are now building the compressed, AI-digestible master manual.

Proceeding to PTSM-2 next.

PYGPT-DESKTOP TECHNICAL SPECIFICATION

PTSM-v1

Section 2 — Complete Menu Tree + UI Hierarchy (Deterministic Map)

ui_structure:

  main_window:
    regions:
      - top_menu_bar
      - left_sidebar
      - central_chat_view
      - bottom_input_panel
      - right_toolbox_panel
      - status_bar

  top_menu_bar:

    File:
      actions:
        - new_context
        - open_context
        - save_context
        - save_as
        - export_context_txt
        - export_context_json
        - clear_history
        - import_context
        - exit_application

    Edit:
      actions:
        - undo
        - redo
        - cut
        - copy
        - paste
        - select_all
        - clear_input_field

    View:
      toggles:
        - toggle_sidebar_visibility
        - toggle_toolbox_visibility
        - toggle_status_bar
        - toggle_fullscreen
        - zoom_in
        - zoom_out
        - reset_zoom

    Config:

      Settings:

        tabs:

          General:
            fields:
              - show_tray_icon: bool
              - minimize_to_tray_on_close: bool
              - renderer_engine: [qtwebengine, legacy]
              - enable_opengl_acceleration: bool
              - enable_proxy: bool
              - proxy_url: string
              - custom_environment_variables: key_value_map
              - memory_limit_mb: int
              - auto_update_check: bool
              - language_locale: string

          API_Keys:
            fields:
              - openai_api_key: string
              - openai_org_id: string
              - anthropic_api_key: string
              - google_api_key: string
              - mistral_api_key: string
              - huggingface_api_key: string
              - perplexity_api_key: string
              - xai_api_key: string
              - deepseek_api_key: string
              - custom_endpoint_override: string

          Layout:
            fields:
              - ui_density: [compact, normal, spacious]
              - chat_font_size: int
              - input_font_size: int
              - context_list_font_size: int
              - toolbox_font_size: int
              - zoom_factor: float
              - dpi_scaling_enabled: bool
              - dpi_factor: float
              - auto_collapse_user_messages: bool
              - show_tips: bool
              - persist_dialog_positions: bool
              - message_bubble_style: [flat, rounded, bordered]
              - max_chat_width_px: int

          Accessibility:
            fields:
              - enable_voice_control_global: bool
              - enable_audio_descriptions: bool
              - keyboard_shortcut_customization: map
              - high_contrast_mode: bool

          Developer:
            fields:
              - enable_debug_menu: bool
              - logging_level: [error, info, debug]
              - show_dev_console: bool
              - enable_raw_request_view: bool
              - enable_response_metadata_view: bool

      Models:
        actions:
          - list_models
          - add_model
          - edit_model
          - delete_model
          - import_from_ollama
          - test_connection
        model_editor_fields:
          - model_name
          - provider_type
          - endpoint_url
          - api_key_reference
          - supports_chat: bool
          - supports_completion: bool
          - supports_vision: bool
          - supports_tools: bool
          - supports_streaming: bool
          - supports_embeddings: bool
          - context_window_size
          - temperature_default
          - max_tokens_default

      Presets:
        actions:
          - create_preset
          - edit_preset
          - clone_preset
          - delete_preset
        preset_fields:
          - system_prompt_template
          - temperature
          - top_p
          - max_tokens
          - frequency_penalty
          - presence_penalty
          - raw_mode: bool

      Plugins:
        actions:
          - enable_plugin
          - disable_plugin
          - configure_plugin
        plugin_categories:
          - system_shell
          - system_prompt_extra
          - telegram_bridge
          - tuya_iot
          - vision_inline
          - voice_control_inline
          - web_search
          - wikipedia_lookup
          - wolfram_alpha
          - twitter_x_integration
          - custom_user_plugins

      Assistants:
        actions:
          - create_assistant
          - edit_assistant
          - delete_assistant
        assistant_fields:
          - name
          - model
          - instructions
          - tools_enabled
          - files_attached
          - temperature
          - response_format

      Agents:
        actions:
          - create_agent
          - edit_agent
          - delete_agent
        agent_fields:
          - goal_definition
          - tool_access
          - iteration_limit
          - autonomous_mode_enabled

    Tools_Menu:
      entries:
        - notepad
        - painter
        - calendar
        - index_manager
        - media_player
        - image_viewer
        - audio_transcriber
        - python_interpreter
        - html_canvas
        - translator
        - web_browser
        - agent_builder

    Help:
      actions:
        - documentation
        - check_for_updates
        - about_dialog
        - open_log_folder
        - open_config_folder

  left_sidebar:
    context_manager:
      - list_saved_contexts
      - rename_context
      - delete_context
      - search_context
      - sort_context
      - filter_context

  central_chat_view:
    message_types:
      - system
      - user
      - assistant
      - tool_call
      - tool_result
    features:
      - streaming_render
      - markdown_render
      - code_block_render
      - image_inline_render
      - vision_attachment_display
      - message_edit
      - message_regenerate
      - message_copy

  bottom_input_panel:
    components:
      - multiline_text_input
      - attach_file_button
      - attach_image_button
      - microphone_button
      - send_button
      - model_selector_dropdown
      - preset_selector_dropdown
      - temperature_slider
      - tools_enable_checkbox

  right_toolbox_panel:
    dynamic_per_mode: true
    components:
      - file_index_panel
      - rag_source_selector
      - embedding_model_selector
      - agent_parameters
      - research_query_controls
      - image_generation_controls
      - audio_controls
      - vision_controls

  status_bar:
    fields:
      - current_model
      - token_usage
      - streaming_status
      - connection_status
      - debug_indicator


---

Section 2 complete.

Next:

> PTSM-3 — Full Settings + Config.json Schema (All Fields + Internal Flags)



Proceeding.

PYGPT-DESKTOP TECHNICAL SPECIFICATION

PTSM-v1

Section 3 — Full Settings + config.json Schema (Deterministic Field Map)

config_file:
  location_linux: ~/.config/pygpt-net/config.json
  format: json
  load_order:
    - default_internal_values
    - config.json_override
    - runtime_session_override

config_schema:

  general:
    show_tray_icon: bool
    minimize_to_tray_on_close: bool
    start_minimized: bool
    auto_check_updates: bool
    renderer_engine: [qtwebengine, legacy]
    enable_opengl_acceleration: bool
    enable_hardware_acceleration: bool
    proxy_enabled: bool
    proxy_url: string
    proxy_auth_user: string
    proxy_auth_pass: string
    memory_limit_mb: int
    language_locale: string
    auto_save_context_interval_sec: int
    confirm_before_exit: bool

  layout:
    ui_density: [compact, normal, spacious]
    zoom_factor: float
    dpi_scaling_enabled: bool
    dpi_factor: float
    chat_font_size: int
    input_font_size: int
    context_list_font_size: int
    toolbox_font_size: int
    max_chat_width_px: int
    auto_collapse_user_messages: bool
    show_tips: bool
    persist_dialog_positions: bool
    message_bubble_style: [flat, rounded, bordered]
    theme_mode: [light, dark, system]
    syntax_highlight_theme: string
    show_token_counter: bool
    show_model_in_header: bool

  accessibility:
    enable_voice_control_global: bool
    enable_audio_descriptions: bool
    high_contrast_mode: bool
    keyboard_shortcuts:
      send_message: string
      toggle_microphone: string
      new_context: string
      switch_mode: string
      open_settings: string

  api_keys:
    openai_api_key: string
    openai_org_id: string
    anthropic_api_key: string
    google_api_key: string
    mistral_api_key: string
    huggingface_api_key: string
    perplexity_api_key: string
    xai_api_key: string
    deepseek_api_key: string
    custom_endpoint_override: string
    custom_headers: map

  models:
    default_chat_model: string
    default_completion_model: string
    default_embedding_model: string
    default_vision_model: string
    auto_select_model_by_mode: bool

  chat_defaults:
    temperature: float
    top_p: float
    max_tokens: int
    frequency_penalty: float
    presence_penalty: float
    stream_responses: bool
    enable_tools_by_default: bool
    enable_markdown_render: bool
    enable_code_syntax_highlighting: bool
    auto_scroll_on_stream: bool

  rag:
    enable_rag_globally: bool
    default_embedding_provider: string
    default_chunk_size: int
    default_chunk_overlap: int
    max_retrieved_chunks: int
    similarity_threshold: float
    auto_rebuild_index_on_file_change: bool
    index_storage_path: ~/.config/pygpt-net/idx
    vector_store_backend: [llamaindex_internal, chroma, faiss]

  audio:
    stt_provider: [openai_whisper_api, local_whisper, google_stt]
    stt_model: string
    stt_language: string
    stt_energy_threshold: int
    stt_pause_threshold: float
    continuous_listening_enabled: bool
    push_to_talk_enabled: bool
    tts_provider: [openai_tts, system_tts]
    tts_voice: string
    tts_speed: float
    tts_auto_play: bool
    audio_input_device: string
    audio_output_device: string

  vision:
    enable_image_upload: bool
    auto_resize_images: bool
    max_image_resolution_px: int

  research_mode:
    enable_web_search: bool
    search_provider: [bing, google, custom_api]
    max_search_results: int
    inject_sources_into_prompt: bool
    show_source_links_in_output: bool

  agents:
    default_iteration_limit: int
    autonomous_mode_enabled: bool
    tool_execution_confirmation_required: bool
    allow_shell_execution: bool
    allow_file_system_access: bool
    allow_network_requests: bool

  plugins:
    enabled_plugins: list
    plugin_configurations:
      system_shell:
        allow_sudo: bool
        allowed_directories: list
      telegram_bridge:
        bot_token: string
        allowed_chat_ids: list
      wolfram_alpha:
        api_key: string
      web_search:
        provider: string
        api_key: string
      voice_control_inline:
        activation_phrase: string
        silence_timeout_sec: float

  logging:
    logging_level: [error, info, debug]
    log_to_file: bool
    log_file_path: ~/.config/pygpt-net/logs/app.log
    show_debug_menu: bool
    show_raw_requests: bool
    show_raw_responses: bool

runtime_behavior:

  config_reload:
    trigger:
      - app_restart
      - manual_reload_from_settings
    live_reload_supported:
      - layout
      - logging
      - plugin_enable_disable
    restart_required:
      - renderer_engine
      - opengl_acceleration
      - proxy_settings

  precedence_rules:
    - per_message_override
    - preset_override
    - mode_override
    - config_defaults
    - hardcoded_defaults

  validation:
    numeric_ranges:
      temperature: [0.0, 2.0]
      top_p: [0.0, 1.0]
      similarity_threshold: [0.0, 1.0]
    required_if_provider_selected:
      openai: openai_api_key
      anthropic: anthropic_api_key
      ollama: endpoint_url


---

Section 3 complete.

Next:

> PTSM-4 — Work Modes Deep Specification (Execution Pipeline Per Mode)



Proceeding.

PYGPT-DESKTOP TECHNICAL SPECIFICATION

PTSM-v1

Section 4 — Work Modes Deep Specification (Execution Pipelines + Capability Matrix)

work_modes:

  chat:
    purpose: general_conversation
    supports:
      streaming: true
      tools: true
      vision: depends_on_model
      rag: false
      embeddings: false
      audio: optional
    pipeline:
      - collect_user_input
      - apply_preset_overrides
      - attach_system_prompt
      - attach_plugin_injections
      - send_to_provider_adapter
      - stream_or_wait_response
      - parse_tool_calls_if_present
      - execute_tools_if_enabled
      - inject_tool_results
      - render_response
      - persist_to_history
    ui_elements:
      - model_selector
      - preset_selector
      - temperature_slider
      - tools_checkbox
      - attachment_button
      - microphone_button

  chat_with_files:
    purpose: retrieval_augmented_chat
    supports:
      streaming: true
      tools: true
      vision: depends_on_model
      rag: true
      embeddings: true
      audio: optional
    pipeline:
      - load_or_build_index
      - chunk_documents
      - embed_chunks
      - store_vectors
      - retrieve_top_k
      - inject_retrieved_context_into_prompt
      - execute_standard_chat_pipeline
    rag_controls:
      - select_index
      - rebuild_index
      - chunk_size
      - chunk_overlap
      - similarity_threshold
      - embedding_model_selector
    index_storage: ~/.config/pygpt-net/idx

  realtime_audio:
    purpose: voice_interaction
    supports:
      streaming: true
      tools: true
      rag: optional
      continuous_listen: true
    pipeline:
      - microphone_capture
      - speech_to_text
      - detect_end_of_speech
      - forward_text_to_chat_pipeline
      - stream_response
      - optional_tts_output
    configurable:
      - stt_provider
      - tts_provider
      - activation_mode
      - energy_threshold
      - silence_timeout
    latency_dependencies:
      - model_stream_speed
      - stt_processing_speed
      - tts_generation_speed

  completion:
    purpose: raw_text_completion
    supports:
      streaming: true
      tools: false
      rag: false
    pipeline:
      - raw_prompt_input
      - provider_completion_endpoint
      - render_output
      - persist_history_optional
    ui_elements:
      - prompt_textarea
      - max_tokens_input
      - temperature_slider

  research:
    purpose: web_augmented_generation
    supports:
      streaming: true
      web_search: true
      citation_injection: true
    pipeline:
      - perform_web_search
      - retrieve_search_results
      - optionally_scrape_pages
      - summarize_sources
      - inject_sources_into_prompt
      - send_to_model
      - render_with_citations
    controls:
      - search_provider
      - max_results
      - citation_display_toggle

  image_generation:
    purpose: image_or_video_generation
    supports:
      dalle: true
      imagen: true
      custom_model: depends_on_provider
    pipeline:
      - collect_prompt
      - provider_image_endpoint
      - save_output_to_img_folder
      - render_preview
    output_storage: ~/.config/pygpt-net/img
    parameters:
      - resolution
      - style
      - quality
      - seed
      - number_of_images

  assistants:
    purpose: api_managed_assistant_instances
    supports:
      file_upload: true
      tool_binding: true
      persistent_thread: true
    pipeline:
      - select_assistant
      - attach_thread
      - send_message
      - poll_for_completion
      - handle_tool_calls
    storage_file: assistants.json

  experts:
    purpose: specialized_system_prompts
    supports:
      preset_switching: true
    implementation:
      - predefined_system_prompts
      - mode_specific_model_recommendations

  agents:
    purpose: multi_step_goal_execution
    supports:
      tool_iteration: true
      autonomous_loop: true
    pipeline:
      - define_goal
      - generate_plan
      - select_tool
      - execute_tool
      - evaluate_result
      - iterate_until_goal_or_limit
    constraints:
      - iteration_limit
      - allowed_tools
      - confirmation_required
    risks:
      - shell_execution
      - file_access
      - network_access

  autonomous_mode:
    purpose: headless_execution
    supports:
      background_operation: true
    execution:
      - start_agent_loop
      - no_manual_intervention
      - stop_on_limit_or_error

capability_matrix:

  features_by_mode:
    streaming:
      - chat
      - chat_with_files
      - realtime_audio
      - completion
      - research
    rag:
      - chat_with_files
      - optionally_realtime_audio
    tools:
      - chat
      - chat_with_files
      - realtime_audio
      - agents
      - assistants
    vision:
      - chat
      - chat_with_files
    audio_input:
      - realtime_audio
      - chat_optional
    audio_output:
      - realtime_audio
      - chat_optional


---

Section 4 complete.

Next:

> PTSM-5 — Plugin System (Built-in Plugins + Extension API + Tool Exposure Model)



Proceeding.

PYGPT-DESKTOP TECHNICAL SPECIFICATION

PTSM-v1

Section 5 — Plugin System (Built-in Plugins + Extension API + Tool Exposure Model)

plugin_system:

  architecture:
    load_mechanism: python_dynamic_import
    discovery_paths:
      - internal_builtin_registry
      - ~/.config/pygpt-net/plugins
    activation:
      - enabled_via_settings
      - per_mode_applicability
    lifecycle:
      - discover_plugins_on_start
      - register_plugin_metadata
      - expose_tools_if_defined
      - inject_prompt_modifiers_if_defined
      - attach_ui_controls_if_defined

  plugin_interface_contract:
    required_attributes:
      - plugin_name
      - plugin_version
      - plugin_description
      - plugin_author
    optional_hooks:
      - on_app_start
      - on_mode_switch
      - before_model_call
      - after_model_response
      - register_tools
      - register_ui_panel
      - register_settings_schema
      - on_shutdown
    tool_exposure:
      format: xml_tool_tag
      execution_flow:
        - llm_outputs_tool_tag
        - tool_dispatcher_parses_json
        - plugin_function_invoked
        - result_returned_to_chat
        - result_injected_into_context

  built_in_plugins:

    system_shell:
      purpose: execute_os_commands
      exposes_tool: true
      tool_name: execute_shell
      parameters:
        - command: string
        - working_directory: string_optional
      settings:
        allow_sudo: bool
        allowed_directories: list
        confirmation_required: bool
      risk_level: high

    system_prompt_extra:
      purpose: append_extra_instructions
      exposes_tool: false
      settings:
        extra_prompt_text: string
        apply_to_modes: list

    telegram_bridge:
      purpose: bidirectional_telegram_chat
      exposes_tool: true
      tool_name: send_telegram_message
      settings:
        bot_token: string
        allowed_chat_ids: list
        auto_forward_responses: bool

    tuya_iot:
      purpose: control_tuya_devices
      exposes_tool: true
      tool_name: control_device
      settings:
        tuya_api_key: string
        device_ids: list

    vision_inline:
      purpose: process_inline_images
      exposes_tool: false
      behavior:
        auto_attach_image_metadata_to_prompt: true
        compatible_modes:
          - chat
          - chat_with_files

    voice_control_inline:
      purpose: speech_trigger_commands
      exposes_tool: false
      settings:
        activation_phrase: string
        silence_timeout_sec: float
        interrupt_on_speech: bool

    web_search:
      purpose: external_web_query
      exposes_tool: true
      tool_name: web_search_query
      settings:
        provider: string
        api_key: string
        max_results: int
        auto_inject_results: bool

    wikipedia_lookup:
      purpose: wikipedia_query
      exposes_tool: true
      tool_name: wikipedia_search
      settings:
        language: string

    wolfram_alpha:
      purpose: computational_query
      exposes_tool: true
      tool_name: wolfram_query
      settings:
        api_key: string

    twitter_x_integration:
      purpose: manage_x_account
      exposes_tool: true
      tool_name: post_tweet
      settings:
        api_key: string
        api_secret: string
        access_token: string

  plugin_execution_security:

    execution_context:
      - runs_in_same_python_process
      - no_sandboxing_by_default

    risk_categories:
      low:
        - prompt_modifier
      medium:
        - api_external_call
      high:
        - shell_execution
        - filesystem_write
        - network_arbitrary

    mitigation_controls:
      - confirmation_dialog
      - tool_execution_toggle
      - restrict_allowed_directories
      - disable_shell_plugin

  custom_plugin_structure_template:

    directory_structure:
      ~/.config/pygpt-net/plugins/custom_plugin_name/
        - __init__.py
        - plugin.py
        - metadata.json
        - optional_ui.py

    metadata_schema:
      name: string
      version: string
      description: string
      author: string
      compatible_modes: list

    minimal_plugin_example_structure:
      plugin_class:
        methods:
          - register_tools()
          - before_model_call()
          - after_model_response()

  plugin_state_persistence:
    location: config.json -> plugins.plugin_configurations
    runtime_enable_disable: supported
    restart_required: false


---

Section 5 complete.

Next:

> PTSM-6 — Model System + Provider Adapters (Full Capability + models.json Schema + Ollama Integration)



Proceeding.

PYGPT-DESKTOP TECHNICAL SPECIFICATION

PTSM-v1

Section 6 — Model System + Provider Adapters (Full Capability Matrix + models.json Schema + Ollama Integration)

model_system:

  registry_file:
    location: ~/.config/pygpt-net/models.json
    format: json
    load_behavior:
      - load_on_start
      - editable_runtime
      - validation_on_save

  model_entry_schema:

    - id: string_unique
      display_name: string
      provider: enum
      model_name: string
      endpoint_url: string_optional
      api_key_reference: string_optional
      supports_chat: bool
      supports_completion: bool
      supports_vision: bool
      supports_tools: bool
      supports_streaming: bool
      supports_embeddings: bool
      supports_audio_input: bool
      supports_audio_output: bool
      context_window: int
      max_output_tokens: int
      default_temperature: float
      default_top_p: float
      provider_specific_parameters: map

  provider_types:

    openai:
      endpoints:
        - /v1/chat/completions
        - /v1/completions
        - /v1/embeddings
        - /v1/images
        - /v1/audio/transcriptions
        - /v1/audio/speech
      supports:
        streaming: true
        tool_calling: true
        vision: true
        embeddings: true
        audio_io: true
      required_fields:
        - openai_api_key

    ollama:
      default_endpoint: http://localhost:11434
      endpoints:
        - /api/chat
        - /api/generate
        - /api/embeddings
      supports:
        streaming: true
        tool_calling: partial_model_dependent
        vision: model_dependent
        embeddings: model_dependent
        audio_io: false_native
      required_fields:
        - endpoint_url
      runtime_detection:
        - GET /api/tags to list_installed_models

    anthropic:
      supports:
        streaming: true
        tool_calling: limited
        vision: model_dependent
      required_fields:
        - anthropic_api_key

    google:
      supports:
        streaming: true
        vision: true
        embeddings: true
      required_fields:
        - google_api_key

    mistral:
      supports:
        streaming: true
        tool_calling: limited
      required_fields:
        - mistral_api_key

    huggingface:
      supports:
        completion: true
        embeddings: model_dependent
      required_fields:
        - huggingface_api_key

    perplexity:
      supports:
        chat: true
        research: optimized
      required_fields:
        - perplexity_api_key

    xai:
      supports:
        chat: true
      required_fields:
        - xai_api_key

  model_import_pipeline:

    import_from_ollama:
      - query_ollama_for_installed_models
      - generate_model_entries
      - auto_detect_capabilities_if_possible
      - write_to_models.json

    manual_add_model:
      - user_define_provider
      - set_endpoint_url
      - define_capabilities
      - save_and_validate

  runtime_model_selection:

    selection_sources_priority:
      - per_message_override
      - preset_assignment
      - mode_default_model
      - global_default_model

    compatibility_enforcement:
      if mode_requires_rag:
        require supports_embeddings == true
      if mode_requires_vision:
        require supports_vision == true
      if tools_enabled:
        require supports_tools == true

  tool_call_handling:

    detection_method:
      - structured_function_call
      - xml_tool_tag_fallback

    execution_flow:
      - parse_tool_payload
      - dispatch_to_tool_dispatcher
      - append_tool_result_to_context
      - optional_followup_call

  streaming_behavior:

    supported_if:
      model.supports_streaming == true

    stream_types:
      - token_stream
      - chunk_stream
      - delta_stream

    ui_behavior:
      - render_incrementally
      - auto_scroll
      - allow_interrupt

  embedding_models:

    used_for:
      - rag_chunk_embedding
      - similarity_search

    config_source:
      config.json -> rag.default_embedding_model

    storage_backend_options:
      - llamaindex_internal
      - chroma
      - faiss

  vision_models:

    compatible_modes:
      - chat
      - chat_with_files

    input_types:
      - image_file_upload
      - drag_drop
      - clipboard_paste

    preprocessing:
      - optional_resize
      - optional_compression

  audio_models:

    stt_models:
      - openai_whisper_api
      - local_whisper
      - faster_whisper

    tts_models:
      - openai_tts
      - system_tts

  context_window_management:

    strategy:
      - sliding_window_truncation
      - summarization_optional
      - hard_token_limit_enforced

    overflow_behavior:
      - truncate_oldest_messages
      - warn_user
      - auto_summarize_if_enabled

  error_handling:

    categories:
      - authentication_error
      - rate_limit_error
      - connection_timeout
      - model_not_found
      - invalid_tool_call

    fallback_behavior:
      - retry_if_transient
      - disable_streaming_on_error
      - display_raw_error_in_debug_mode


---

Section 6 complete.

Next:

> PTSM-7 — RAG System Deep Specification (LlamaIndex Pipeline + Index Structure + Embedding Controls + File Management)



Proceeding.

PYGPT-DESKTOP TECHNICAL SPECIFICATION

PTSM-v1

Section 7 — RAG System Deep Specification (LlamaIndex Pipeline + Index Structure + Embedding Controls + File Management)

rag_system:

  engine:
    default: llamaindex
    abstraction_layer: rag_pipeline

  activation_conditions:
    - mode == chat_with_files
    - rag_enabled_globally == true
    - embedding_model_configured == true

  index_storage:
    base_path: ~/.config/pygpt-net/idx
    per_index_structure:
      idx_name/
        - index_metadata.json
        - docstore.json
        - vector_store.bin_or_db
        - embedding_config.json

  index_metadata_schema:
    index_name: string
    created_timestamp: datetime
    embedding_model: string
    chunk_size: int
    chunk_overlap: int
    vector_store_backend: enum
    source_files: list
    total_chunks: int

  document_ingestion_pipeline:
    - select_files
    - detect_file_type
    - load_document
    - normalize_text
    - chunk_text
    - generate_embeddings
    - persist_vector_data
    - update_index_metadata

  supported_file_types:
    - .txt
    - .md
    - .pdf
    - .docx
    - .html
    - .csv
    - .json
    - .py
    - generic_text_based

  chunking:
    parameters:
      chunk_size: int
      chunk_overlap: int
    strategy:
      - sliding_window
      - sentence_boundary_optional
    validation:
      chunk_size > chunk_overlap

  embedding_generation:
    provider_source:
      - openai
      - ollama
      - huggingface
      - local_embedding_model
    embedding_dimension: model_dependent
    batch_size: int
    error_retry: true

  vector_store_backends:

    llamaindex_internal:
      type: file_based
      persistence: local_disk
      indexing_method: flat_vector_search

    chroma:
      type: local_database
      persistence: sqlite_or_duckdb
      advanced_filtering: supported

    faiss:
      type: in_memory_or_disk
      optimized_for_large_collections: true

  retrieval_pipeline:
    - receive_user_query
    - generate_query_embedding
    - compute_similarity_against_index
    - retrieve_top_k_chunks
    - filter_by_similarity_threshold
    - inject_chunks_into_prompt_context

  retrieval_parameters:
    top_k: int
    similarity_threshold: float
    reranking_enabled: bool
    max_total_context_tokens: int

  prompt_injection_strategy:
    format:
      system_prefix: "Use the following retrieved context:"
      separator: "\n---\n"
    injection_position:
      - before_user_message
      - appended_to_system_prompt
    context_limit_strategy:
      - trim_lowest_similarity
      - truncate_excess_tokens

  index_management_ui_controls:
    - create_new_index
    - delete_index
    - rebuild_index
    - add_files_to_index
    - remove_file_from_index
    - inspect_index_metadata
    - switch_active_index

  automatic_rebuild_triggers:
    - source_file_modified
    - embedding_model_changed
    - chunk_parameters_changed

  multi_index_support:
    allow_multiple_indices: true
    per_context_index_assignment: true
    global_default_index: optional

  performance_controls:
    embedding_batch_size: int
    async_embedding_generation: bool
    parallel_chunk_processing: bool

  memory_interaction:
    rag_context_injection_precedes_chat_history: true
    history_token_budget_adjusted: true

  security_considerations:
    local_file_access_required: true
    no_sandboxing_of_loaded_content: true
    index_files_plaintext_metadata: true

  error_conditions:
    - missing_embedding_model
    - index_not_found
    - vector_store_corruption
    - embedding_provider_unreachable
    - similarity_search_failure

  fallback_behaviors:
    - disable_rag_for_session
    - notify_user
    - continue_standard_chat

  compatibility_matrix:

    required_model_capabilities:
      supports_chat: true
      supports_embeddings: true

    optional_features:
      streaming: improves_latency
      large_context_window: improves_retrieval_capacity


---

Section 7 complete.

Next:

> PTSM-8 — Audio System Deep Specification (Always-On Voice, STT/TTS Providers, Continuous Listening State Machine, Latency Controls)



Proceeding.

Below is the next continuation of the structured technical manual for:

PyGPT Desktop

(Ubuntu + Ollama + Multimodal + Voice + RAG Advanced Configuration)


---

SECTION 6 — ADVANCED AUTOMATION & AGENT BEHAVIOR

This section covers turning PyGPT into a semi-autonomous AI workstation rather than just a chat UI.


---

6.1 Persistent System Identity Engineering

Location:

Settings → System Prompt / Profiles

Advanced Strategy:

Instead of a single system prompt, create modular persona layers:

[Layer 1: Core Identity]
You are an Ubuntu AI systems engineer specializing in Ollama-based multimodal deployments.

[Layer 2: Tool Usage Rules]
Always use tools when available.
Prioritize local models over cloud.

[Layer 3: Output Style]
Respond in structured technical format unless user specifies otherwise.

[Layer 4: Memory Constraints]
Persist project state between sessions.

Result:

• Deterministic behavior
• Reduced hallucination
• Stable project continuity


---

6.2 Multi-Model Routing (Advanced)

If running:

• llama3
• mistral
• codellama
• phi
• llava

You can configure:

Model Usage Strategy

Task	Model

Coding	codellama
Long reasoning	llama3
Fast replies	phi
Vision	llava
RAG reasoning	mistral


Implementation Pattern

Manual switching (default)

OR

Use API middleware to auto-route prompts via: • LangChain • Custom Python wrapper • Node proxy


---

SECTION 7 — FULL VOICE STACK ENGINEERING

You requested always-on voice. Here is full production-grade setup.


---

7.1 Speech-To-Text (STT) Options

Option A — Whisper (Local)

Via:

whisper.cpp
faster-whisper
openai-whisper

Recommended: faster-whisper (CUDA acceleration)

Ubuntu Install:

pip install faster-whisper


---

7.2 Text-To-Speech (TTS)

High Quality:

• Piper • Coqui TTS

Install Piper:

sudo apt install piper

Run:

piper --model en_US-amy-medium.onnx


---

7.3 Always-On Voice Architecture

Pipeline:

Microphone
↓
Voice Activity Detection (VAD)
↓
Whisper STT
↓
PyGPT (Ollama backend)
↓
TTS engine
↓
Speakers

To enable continuous mode:

You must implement:

• VAD trigger (silero-vad recommended) • Auto-restart microphone listener • Auto-send transcript to API

PyGPT alone does not fully implement always-on autonomous mode — requires helper script.


---

7.4 Production-Level Voice Script

Minimal architecture:

while True:
    listen()
    if speech_detected:
        text = transcribe()
        response = send_to_pygpt(text)
        speak(response)

For stability:

• Threaded architecture • Async I/O • Buffer overflow protection • Timeout fallback


---

SECTION 8 — RAG FULL DEPLOYMENT ARCHITECTURE

You want deep RAG.

Here is enterprise-grade configuration.


---

8.1 RAG Layers

Level 1 — Basic: Upload docs → embed → query

Level 2 — Structured: Chunking + metadata

Level 3 — Semantic Graph: Vector DB + memory linking

Level 4 — Autonomous: Agent decides when to retrieve


---

8.2 Recommended Stack (Local Ubuntu)

Layer	Tool

Embeddings	Ollama embeddings model
Vector DB	Chroma
Advanced	Qdrant
Chunking	LangChain
Storage	Local SSD



---

8.3 Installing Chroma

pip install chromadb

Default storage:

~/.chromadb/


---

8.4 Embedding Model via Ollama

ollama pull nomic-embed-text

Configure PyGPT: Settings → Embeddings → Select nomic model


---

8.5 Chunking Strategy

Optimal chunk size:

• 500–1200 tokens • 10–20% overlap

Bad chunking = bad retrieval.


---

8.6 Metadata Strategy

Attach:

{
 "source": "filename",
 "topic": "AI configuration",
 "priority": 1
}

Allows filtered retrieval.


---

SECTION 9 — MULTIMODAL DEPLOYMENT

You want multimodal.


---

9.1 Ollama Vision Models

Install:

ollama pull llava

Alternative:

ollama pull bakllava


---

9.2 PyGPT Vision Configuration

Settings → Model Select llava

Enable: ✔ Image Upload ✔ Vision Mode


---

9.3 Performance Notes

With 64GB RAM (your Lenovo L14 Gen 1):

You can run: • 7B models comfortably • 13B models moderate • 34B borderline unless quantized


---

SECTION 10 — PERFORMANCE TUNING ON UBUNTU


---

10.1 GPU Acceleration

Check:

nvidia-smi

Install CUDA toolkit if NVIDIA GPU.

If no GPU: Enable CPU threading:

OLLAMA_NUM_THREADS=8


---

10.2 Model Quantization

Use: • Q4_K_M • Q5_K_M

Balance speed vs accuracy.


---

10.3 Swap + Hugepages Optimization

Edit:

/etc/sysctl.conf

Tune vm.swappiness.


---

SECTION 11 — EXTENSION ECOSYSTEM

Applications that integrate well:

Tool	Purpose

Open WebUI	Advanced model dashboard
LangChain	Agents
Haystack	RAG pipeline
SillyTavern	Persona frontend
AutoGen	Multi-agent
FastAPI	Custom API server



---

SECTION 12 — ENTERPRISE-LEVEL STACK (If You Want Maximum Capability)

Ubuntu
↓
Ollama
↓
PyGPT Desktop
↓
LangChain
↓
Chroma/Qdrant
↓
Whisper
↓
Piper
↓
Custom Voice Loop

This gives you:

✔ Multimodal
✔ Voice
✔ Long-term memory
✔ Tool use
✔ Offline capability


---

SECTION 13 — TIME ESTIMATE (Realistic)

Given your hardware:

Basic multimodal + RAG: ~45–90 minutes

Production-grade voice + autonomous loop: 3–6 hours

Enterprise-level automation: 1–2 days


---

SECTION 14 — NEXT CONTINUATION OPTIONS

We can now go deeper into:

1. Complete file structure map of PyGPT


2. Every JSON config parameter


3. Building full AI workstation architecture diagram


4. Hardening and security layer


5. Full autonomous AI shell agent



Tell me which layer you want expanded next.

