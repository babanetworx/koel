---
layout: page
title: Usage
permalink: /usage/
---

# Using Koel

Once you've [installed Koel]({{ site.baseurl }}/installation), you can start leveraging its powerful features to enhance your WhatsApp experience. This guide will walk you through the main usage scenarios and provide examples to help you get the most out of Koel.

## Interacting with the AI Assistant

Koel's web interface provides a direct chat with the AI assistant, allowing you to control WhatsApp through natural language commands.

### Example Prompts

Here are some examples of what you can ask the AI assistant:

- **List chats**: "List my recent chats"
- **View messages**: "Show me the last 10 messages from John"
- **Send messages**: "Send a message to Sarah saying I'll be 15 minutes late"
- **Send files**: "Send this file to the Marketing Team group: /path/to/presentation.pdf"
- **Search contacts**: "Find all contacts with 'Smith' in their name"
- **Get information**: "How many messages did I exchange with Alex yesterday?"

![Chat Interface]({{ site.baseurl }}/images/chat_interface.png){: .feature-image }

## Using the Auto-Responder

The auto-responder feature allows Koel to automatically reply to messages in selected chats.

### Setting Up Auto-Responses

1. Navigate to the Auto-Responder tab in the settings
2. Select which chats to monitor:
   - Individual chats: Choose specific contacts
   - Group chats: Select which groups to monitor
3. Configure response behavior:
   - Rate limiting: Set how frequently Koel should respond
   - Randomization: Adjust how often Koel should respond to messages
4. Add custom instructions to guide the AI's responses:
   - "Respond in a professional tone"
   - "Keep responses brief and to the point"
   - "Answer questions about our business hours and services"

### Monitoring Specific Chats

You can choose which chats Koel should monitor and respond to:

1. Go to the Monitored Chats section
2. Browse your contacts and groups
3. Toggle monitoring on/off for each chat
4. Optionally, set specific instructions for individual chats

## Special Commands

Koel supports special commands that can be used directly in WhatsApp chats:

### #show [prompt]

Generate an image based on a text prompt:

```
#show a futuristic city with flying cars
```

Koel will process this command and send back an AI-generated image matching your description.

### #meme

Generate a meme based on the recent chat context:

```
#meme
```

Koel will analyze the recent conversation and create a relevant, humorous meme.

### #info [question/request]

Ask a direct question to the AI assistant without triggering the normal auto-responder flow:

```
#info What's the weather forecast for tomorrow?
```

```
#info Summarize the last 20 messages in this chat
```

## Chat Summarization

Koel can automatically generate summaries of your conversations to help you keep track of important information.

### Configuring Summarization

1. Go to the Summary Settings tab
2. Set the summarization schedule:
   - Daily summaries
   - Weekly summaries
   - Custom intervals
3. Select which chats to include in summaries
4. Choose what to focus on:
   - Action items
   - Decisions made
   - Questions asked
   - All conversation content

### Viewing Summaries

1. Navigate to the Summaries tab
2. Browse summaries by chat and date
3. Search for specific content within summaries
4. Export summaries if needed

## Settings and Configuration

![Settings Interface]({{ site.baseurl }}/images/settings_interface.png){: .feature-image }

### LLM Settings

Configure which AI model Koel uses:

1. Choose between Gemini and Ollama
2. For Gemini:
   - Enter your API key
   - Select the model (e.g., gemini-pro)
3. For Ollama:
   - Enter the base URL
   - Select the model (e.g., llama2, mistral)

### Advanced Settings

Fine-tune Koel's behavior:

1. **Response Templates**: Create templates for common responses
2. **Notification Settings**: Configure when and how you're notified
3. **Data Management**: Control how chat data is stored and processed
4. **Factory Reset**: Reset Koel to its default state if needed

## Best Practices

To get the most out of Koel:

1. **Start Small**: Begin by monitoring just a few important chats
2. **Refine Instructions**: Regularly update your custom instructions based on response quality
3. **Use Special Commands**: Leverage #info, #show, and #meme for enhanced functionality
4. **Review Summaries**: Check conversation summaries to stay informed
5. **Provide Feedback**: Use the feedback mechanism to help improve responses

## Troubleshooting

If you encounter issues:

1. Check the [Troubleshooting section]({{ site.baseurl }}/installation#troubleshooting) in the Installation guide
2. Review the Docker logs for error messages
3. Ensure your WhatsApp connection is active
4. Verify your LLM configuration is correct

[Explore Technical Details]({{ site.baseurl }}/technical){: .button}