# Summary GPT Bot

An AI-powered text summarization Telegram bot that generates concise summaries of text, URLs, PDFs and YouTube videos.

## Features

- Supports text
- Supports URLs
- Supports PDFs
- Supports YouTube videos (no support for YouTube Shorts)

## Usage

Launch a OpenAI GPT-4 summary bot that only can be used by your friends and you.

```sh
docker run -d \
    -e LLM_MODEL=gpt-4 \
    -e OPENAI_API_KEY=$OPENAI_API_KEY \
    -e TELEGRAM_TOKEN=$YOUR_TG_TOKEN \
    -e TS_LANG=$YOUR_LANGUAGE \
    -e ALLOWED_USERS=<friend1_id>,<friend2_id>,<your_id> \
    tonypai/summary-gpt-bot:latest
```

Launch a summary bot using Azure OpenAI.

```sh
docker run -d \
    -e AZURE_API_BASE=https://<your_azure_resource_name>.openai.azure.com \
    -e AZURE_API_KEY=$AZURE_API_KEY \
    -e AZURE_API_VERSION=2024-02-15-preview \
    -e LLM_MODEL=azure/<your_deployment_name> \
    -e TELEGRAM_TOKEN=$YOUR_TG_TOKEN \
    -e TS_LANG=$YOUR_LANGUAGE \
    tonypai/summary-gpt-bot:latest
```

LLM Variables

| Environment Variable | Description |
|----------------------|-------------|
| AZURE_API_BASE       | API URL base for AZURE OpenAI API |
| AZURE_API_KEY        | API key for AZURE OpenAI API |
| AZURE_API_VERSION    | API version for AZURE OpenAI API |
| OPENAI_API_KEY       | API key for OpenAI API |

Bot Variables

| Environment Variable | Description |
|----------------------|-------------|
| CHUNK_SIZE           | The maximum token of a chunk when receiving a large input (default: 2100) |
| LLM_MODEL            | LLM Model to use for text summarization (default: chatgpt-4o-latest) |
| TELEGRAM_TOKEN       | Token for Telegram API (required) |
| TS_LANG              | Language of the text to be summarized (default: Taiwanese Mandarin) |
| DDG_REGION           | The region of the duckduckgo search (default: wt-wt) 👉[Regions](https://github.com/deedy5/duckduckgo_search#regions) |
| ALLOWED_USERS        | A list of user IDs allowed to use. Asking @myidbot for Telegram ID (optional) |
