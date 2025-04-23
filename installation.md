---
layout: page
title: Installation
permalink: /installation/
---

# Installing Koel

Getting started with Koel is straightforward. Follow these steps to set up your own WhatsApp AI assistant.

## Prerequisites

Before installing Koel, make sure you have:

- **Docker and Docker Compose**: Koel runs in a Docker container for easy deployment
- **For Ollama integration**: Ollama running on the host machine (optional)
- **WhatsApp account**: An active WhatsApp account for authentication

## Installation Steps

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/whatsapp-mcp.git
cd whatsapp-mcp
```

### 2. Start the Application

Using Docker Compose (recommended):

```bash
docker-compose up --build -d
```

Alternatively, you can use the standalone Docker run command:

```bash
docker run -d -it --name whatsapp-mcp -p 8501:8501 -v whatsapp_data:/app/whatsapp-bridge/store yourusername/whatsapp-mcp:latest
```

### 3. Access the Web Interface

Open your browser and navigate to:

```
http://localhost:8501
```

You'll be greeted by Koel's web interface where you can configure settings and interact with the assistant.

### 4. Authenticate with WhatsApp

![QR Code]({{ site.baseurl }}/images/qr_code.png){: .feature-image }

On first run, you'll need to scan a QR code to authenticate with WhatsApp Web:

1. Start the application as described above
2. Check the Docker logs to see the QR code:
   ```bash
   docker logs whatsapp-mcp
   ```
3. Open WhatsApp on your phone
4. Go to Settings > Linked Devices > Link a Device
5. Scan the QR code displayed in the logs
6. Wait for the connection to be established

Once authenticated, Koel will maintain the session until you log out or perform a factory reset.

## Configuration

After installation, you'll need to configure Koel to suit your needs:

### LLM Settings

1. Navigate to the Settings tab in the web interface
2. Choose your preferred LLM provider:
   - **Gemini**:
     - Enter your API key
     - Select the model names
   - **Ollama**:
     - Enter the base URL (e.g., http://host.docker.internal:11434)
     - Select the model names

### Auto-Responder Settings

1. Go to the Auto-Responder tab
2. Select which individual and group chats to monitor
3. Configure rate limiting and randomization
4. Add custom instructions for the AI

### Summary Settings

1. Navigate to the Summary tab
2. Configure when and how often summaries are generated
3. Select which chats to include in summary generation

## Persistent Storage

Koel uses a Docker volume (`whatsapp_data`) to store:
- WhatsApp session data
- Message history
- Configuration settings

This ensures your data persists across container restarts.

## Troubleshooting

### QR Code Issues

If you can't scan the QR code:
1. Try a factory reset from the settings page
2. Restart the container
3. Scan a new QR code

### Connection Problems

If you're experiencing connection issues:
1. Check the Docker logs for error messages:
   ```bash
   docker logs whatsapp-mcp
   ```
2. Ensure your internet connection is stable
3. Verify that your WhatsApp account is active

### LLM Configuration

If the AI responses aren't working:
1. Double-check your API keys and model names
2. Ensure the LLM provider is accessible from the container
3. Check the logs for any error messages related to the AI service

### Ollama Integration

If using Ollama:
1. Make sure Ollama is running on your host machine
2. Verify the URL is correctly set to access Ollama from within the Docker container
3. Ensure the models you want to use are downloaded in Ollama

## Next Steps

Once you have Koel up and running, check out the [Usage Guide]({{ site.baseurl }}/usage) to learn how to make the most of your new WhatsApp assistant.

[Explore Usage Examples]({{ site.baseurl }}/usage){: .button}