---
layout: page
title: Features
permalink: /features/
---

# Koel Features

Koel offers a comprehensive set of features designed to enhance your WhatsApp experience with AI capabilities and automation.

## Core Features

### AI-Powered Auto-Responder

![Chat Interface]({{ site.baseurl }}/images/chat_interface.png){: .feature-image }

Koel's auto-responder automatically handles incoming WhatsApp messages using advanced AI:

- **Intelligent Responses**: Generates contextually appropriate replies based on message content
- **Rate Limiting**: Control message frequency to prevent spam
- **Selective Monitoring**: Choose which individual and group chats to monitor
- **Customizable AI Instructions**: Guide the AI's response style and content
- **Randomization**: Make responses more natural by not responding to every message

### Web-Based User Interface

![Settings Interface]({{ site.baseurl }}/images/settings_interface.png){: .feature-image }

Configure and interact with Koel through a user-friendly web interface:

- **Chat Interface**: Direct interaction with the AI assistant
- **Configuration Panels**: Easy setup for LLM and auto-responder settings
- **Monitored Chat Selection**: Visual selection of chats to monitor
- **Real-time Updates**: See new messages and responses as they happen
- **Summary Management**: View and manage chat summaries

### LLM Integration

Koel supports multiple AI models through a unified interface:

- **Gemini Support**: Connect to Google's Gemini models
- **Ollama Integration**: Use local Ollama models for privacy and control
- **Caching**: Improved performance and reduced API costs
- **Error Handling**: Robust error handling and retry mechanisms
- **Context Management**: Maintains conversation context for more coherent responses

### Media Handling

Send and receive various types of media through WhatsApp:

- **Images**: Share and receive photos and pictures
- **Audio**: Exchange voice messages and audio files
- **Video**: Share video content
- **Documents**: Exchange PDF, Word, and other document formats
- **Image Generation**: Create images from text descriptions

## Special Features

### Chat Monitoring

Select which conversations Koel should monitor and respond to:

- **Individual Chat Monitoring**: Choose specific contacts
- **Group Chat Monitoring**: Select which groups to monitor
- **Monitoring Rules**: Set conditions for when to respond
- **Notification Settings**: Get alerts about monitored activity

### Direct AI Chat with Active Intelligence

Interact with Koel's AI assistant to perform WhatsApp operations:

- **Natural Language Commands**: Control WhatsApp with conversational requests
- **Message Management**: Send, search, and organize messages
- **Contact Management**: Find and interact with contacts
- **Media Sharing**: Share files and media through simple requests
- **Information Retrieval**: Ask about chat history and statistics

### Chat Summarization

Automatically generate concise summaries of chat conversations:

- **Scheduled Summaries**: Configure when summaries are generated
- **Customizable Focus**: Choose what aspects of conversations to highlight
- **Historical Context**: Maintain conversation history for better summaries
- **Summary Storage**: Access past summaries for reference

### Special Commands

Use special commands in your chats for enhanced functionality:

- **#show [prompt]**: Generate an image based on the prompt
- **#meme**: Generate a meme based on recent chat context
- **#info [question/request]**: Ask a direct question to the AI assistant

## Technical Features

### Multi-Component Architecture

Koel uses a sophisticated architecture for reliability and performance:

- **WhatsApp Bridge**: Connects to WhatsApp Web using the whatsmeow library
- **API Server**: Interfaces with the WhatsApp Bridge and exposes operations
- **Auto-Responder**: Monitors chats and generates AI responses
- **AI Engine**: Integrates with LLM providers and handles message formatting
- **Summarizer**: Periodically generates summaries of chat conversations

### Persistent Storage

Koel maintains your data securely:

- **WhatsApp Session Data**: Persistent login sessions
- **Message History**: Stored chat history for context
- **Configuration Settings**: Saved preferences and settings
- **Docker Volume Support**: Data persists across container restarts

[Get Started with Koel]({{ site.baseurl }}/installation){: .button}