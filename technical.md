---
layout: page
title: Technical Details
permalink: /technical/
---

# Technical Architecture of Koel

Koel uses a sophisticated multi-component architecture to provide its powerful WhatsApp integration and AI capabilities. This page explains the technical details of how Koel works under the hood.

## System Architecture

Koel runs as a multi-component system within a single Docker container, with each component handling specific responsibilities:

```
                                  WhatsApp Web
                                      │
                                      │ (Internet)
                                      ▼
┌───────────────────────────────────────────────────────────────────────────────┐
│                              Docker Container                                 │
│                                                                               │
│  ┌─────────────┐      ┌───────────────┐     ┌────────────┐                    │
│  │ Web UI      │◄────►│  API Server   │◄───►│ WhatsApp   │                    │
│  │ (Node.js)   │      │  (Python)     │     │ Bridge (Go)│                    │
│  │ Port: 8501  │      │ Port: 8000    │     │ Port: 8080 │                    │
│  └─────┬───────┘      └───────┬───────┘     └─────┬──────┘                    │
│        │                      │                   │                           │
│        │                      │ MCP Protocol      │                           │
│        ▼                      ▼                   ▼                           │
│  ┌─────────────┐      ┌───────────────┐     ┌────────────┐                    │
│  │ AI Engine   │◄────►│ Auto-Responder│◄───►│ WhatsApp   │                    │
│  │ (LiteLLM)   │      │  (Python)     │     │ Web Client │                    │
│  │ ┌─────────┐ │      └───────┬───────┘     └────────────┘                    │
│  │ │ Image   │ │              │                                               │
│  │ │Generator│ │              │                                               │
│  │ └─────────┘ │              │                                               │
│  │ ┌─────────┐ │      ┌───────▼───────┐                                       │
│  │ │ Meme    │ │      │  Summarizer   │                                       │
│  │ │Generator│ │      │   (Python)    │                                       │
│  │ └─────────┘ │      └───────────────┘                                       │
│  └──────┬──────┘                                                              │
│         │                                                                     │
│         │ LiteLLM Adapters                                                    │
│         ▼                                                                     │
│  ┌─────────────────────────────────┐                                          │
│  │        External Services        │                                          │
│  │ ┌───────────┐   ┌─────────────┐ │                                          │
│  │ │ Gemini API│   │Ollama Models│ │                                          │
│  │ └───────────┘   └─────────────┘ │                                          │
│  └─────────────────────────────────┘                                          │
│                                                                               │
└───────────────────────────────────────────────────────────────────────────────┘
                │
                │ Port 8501 (exposed)
                ▼
           User Browser
```

## Core Components

### 1. WhatsApp Bridge (Go)

The WhatsApp Bridge is the foundation of Koel, providing connectivity to WhatsApp Web:

- **Technology**: Built in Go using the whatsmeow library
- **Functionality**:
  - Connects to WhatsApp Web servers
  - Handles authentication via QR code
  - Sends and receives messages
  - Manages media uploads and downloads
  - Maintains WhatsApp session state
- **Storage**: Uses SQLite database to store messages and chat information
- **API**: Exposes a REST API for other components to interact with WhatsApp

### 2. API Server (Python)

The API Server acts as the central hub for communication between components:

- **Technology**: Python with FastAPI
- **Functionality**:
  - Interfaces with the WhatsApp Bridge
  - Implements FastMCP server for standardized tool definitions
  - Provides a unified API for WhatsApp operations
  - Handles message routing between components
  - Manages configuration and settings
- **Protocol**: Uses Model Context Protocol (MCP) to standardize communication

### 3. Web UI (Node.js/Express)

The Web UI provides the user interface for interacting with Koel:

- **Technology**: Node.js with Express
- **Functionality**:
  - Web-based user interface
  - Proxy server between frontend and backend
  - Configuration panels for settings
  - Chat interface for direct AI interaction
  - Real-time updates via WebSockets
- **Port**: Exposed on port 8501 for user access

### 4. Auto-Responder (Python)

The Auto-Responder handles automated message responses:

- **Technology**: Python
- **Functionality**:
  - Monitors selected chats for new messages
  - Generates AI responses using the configured LLM
  - Implements rate limiting and randomization
  - Handles special commands (#show, #meme, #info)
  - Maintains state to track processed messages
- **Integration**: Communicates with the AI Engine for response generation

### 5. AI Engine (Python)

The AI Engine provides the intelligence behind Koel:

- **Technology**: Python with LiteLLM
- **Functionality**:
  - Integrates with LLM providers (Gemini, Ollama)
  - Handles message formatting and context management
  - Provides tool calling capabilities via MCP
  - Implements caching and error handling
  - Image and meme generation
- **Models**: Supports various AI models through a unified interface

### 6. Summarizer (Python)

The Summarizer creates concise summaries of conversations:

- **Technology**: Python
- **Functionality**:
  - Periodically generates summaries of chat conversations
  - Configurable schedule for summary generation
  - Uses AI to create concise summaries of chat history
  - Stores summaries for future reference

## Key Technologies

### Model Context Protocol (MCP)

Koel uses MCP to standardize communication between components:

- **FastMCP Server**: Implemented in the API Server
- **Tool Definitions**: Each WhatsApp operation defined as a tool
- **LiteLLM MCP Client**: Used by the AI Engine to load and call tools
- **Standardized Interface**: Allows AI models to interact with WhatsApp

### LiteLLM Integration

LiteLLM provides a unified interface to multiple LLM providers:

- **Model Abstraction**: Supports both Gemini and Ollama models
- **Caching**: Implements response caching for performance
- **Error Handling**: Provides robust error handling and retry mechanisms
- **Tool Calling**: Enables AI models to call WhatsApp operations
- **Image Generation**: Supports generating images with various models

### Persistent Storage

Koel uses persistent storage to maintain data across sessions:

- **Docker Volume**: `whatsapp_data` volume for persistent storage
- **SQLite Database**: Stores messages, chats, and contacts
- **Configuration Storage**: Maintains user settings and preferences
- **Session Management**: Preserves WhatsApp session information

## Security Considerations

Koel implements several security measures:

- **Containerization**: Runs in an isolated Docker container
- **Local Processing**: Option to use local Ollama models for privacy
- **Session Management**: Secure handling of WhatsApp session data
- **API Key Security**: Secure storage of LLM API keys
- **Data Isolation**: Separation between different components

## Performance Optimization

Koel is optimized for performance:

- **Caching**: Response caching to reduce API calls
- **Efficient Communication**: Streamlined inter-component communication
- **Database Indexing**: Optimized database queries
- **Rate Limiting**: Prevents excessive API usage
- **Asynchronous Processing**: Non-blocking operations where possible

## Extending Koel

Developers can extend Koel's functionality:

- **Custom Tools**: Add new tools to the MCP server
- **UI Customization**: Modify the web interface
- **New LLM Providers**: Add support for additional AI models
- **Custom Commands**: Implement new special commands
- **Integration Points**: Connect with other systems and services

[Back to Home]({{ site.baseurl }}/){: .button}