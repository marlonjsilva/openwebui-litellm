# Open WebUI with LiteLLM Setup

> This project is based on [openwebui-litellm](https://github.com/chrispangg/openwebui-litellm) with small modifications.

This project sets up an Open WebUI interface with LiteLLM as a backend proxy for various AI models. It uses Podman Compose to orchestrate the services.

## Prerequisites

-   Podman and Podman Compose installed on your system
-   API keys for the AI models you want to use
-   AWS S3 Bucket to store logs
-   AWS Credentials to access Bedrock Services and S3 Bucket

## Configuration

1. Create a `.env` file in the project root with the following content:

    ```ymal
    # LiteLLM Configs
    MASTER_KEY='' #required
    # LiteLLM Model Providers Configs
    DEEPSEEK_API_KEY=''
    OPENAI_API_KEY=''
    AWS_ACCESS_KEY_ID=''
    AWS_SECRET_ACCESS_KEY=''
    AWS_REGION_NAME=''
    # LiteLLM S3 Bucket Logs
    AWS_S3_BUCKET_NAME=''
    # Postgress Configs
    POSTGRES_USER=''
    POSTGRES_PASSWORD=''
    POSTGRES_DB=''
    ```

-   Add your master key for LiteLLM
-   Add your API Keys
-   Add your AWS Credentials
-   Add your S3 Bucket name
-   Configure your POSTGRESS database

2. Ensure the `config.yml` file is present in the project root. This file configures the available models for LiteLLM. Feel free to add more models here!

## Usage

1. Start the services:

    ```bash
    podman compose --env-file .env up -d
    ```

2. Access the Open WebUI interface at `http://localhost:3000`
   
3. Access LiteLLM OpenAPI page at `http://localhost:4000`

## Services

-   **Open WebUI**: Runs on port 3000, provides the user interface.
-   **LiteLLM**: Runs on port 4000, acts as a proxy for various AI models.

## Available Models

The following models are configured in `config.yml`:

-   deepseek-coder (DeepSeek)
-   deepseek-chat (DeepSeek)
-   gpt-4.1 (OpenAI)
-   gpt-4o (OpenAI)
-   gpt-4o-mini (OpenAI)
-   claude-4-5-sonnet (AWS Bedrock)
-   claude-3-7-sonnet (AWS Bedrock)
-   claude-3-5-sonnet (AWS Bedrock)
-   deepseek.r1-v1 (AWS Bedrock)
-   deepseek.v3-v1 (AWS Bedrock)
-   llama4-scout-17b (AWS Bedrock)
-   llama4-maverick-17b (AWS Bedrock)
-   llama3-1-8b (AWS Bedrock)
-   llama3-3-70b (AWS Bedrock)
-   nova-micro (AWS Bedrock)
-   nova-premier (AWS Bedrock)
-   nova-pro (AWS Bedrock)
-   palmyra-x4 (AWS Bedrock)
-   palmyra-x5 (AWS Bedrock)

## Available Embeddings

The following embeddings are configured in `config.yml`:

-   titan-embed-text-v2 (AWS Bedrock)
-   embed-english-v3 (AWS Bedrock)
-   embed-multilingual-v3 (AWS Bedrock)
