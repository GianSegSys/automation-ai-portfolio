# RSS Summarizer to Discord with n8n, Ollama & Gmail Notification

📄 Description

This self-hosted automation uses n8n and Ollama to summarize new articles from an RSS feed and post them to a Discord channel. The workflow includes internet connectivity checks with retries, and after a successful Discord post, it sends a confirmation email via Gmail.

🧩 Key Features

- Checks internet connectivity (with 3 retries, 10 min apart) before proceeding.
- Fetches the latest articles from an RSS feed.
- Summarizes content using local LLM via Ollama.
- Publishes summaries to a Discord channel via webhook.
- Sends an email confirmation with Gmail after successful post.
- Fully containerized with Docker and docker-compose.

⚙️ Technologies Used

- n8n (self-hosted automation engine)
- Ollama (local LLM runner for models like Llama3)
- Discord Webhooks
- Gmail SMTP integration in n8n
- Docker & Docker Compose
- RSS feeds (any public URL)
- Bash/Command node for connectivity check

🛠 Setup Instructions

- Clone the repo
git clone https://github.com/GianSegSys/automation-ai-portfolio.git
cd automation-ai-portfolio/n8n-workflows/rss-summarizer-discord

- Run containers
docker compose up -d

🧰 Environment Configuration

.env should include:

- DISCORD_WEBHOOK_URL=https://discord.com/api/webhooks/...
- RSS_FEED_URL=https://www.bleepingcomputer.com/feed/
- GMAIL_USER=your@gmail.com
- GMAIL_PASS=yourapppassword
- EMAIL_RECIPIENT=admin@example.com
- OLLAMA_MODEL=llama3

📌 Folder Summary

File/Folder:			Purpose:
rss-summarizer-discord.json	Exported n8n flow
docker-compose.yml		Sets up n8n + Ollama
.env				Secure environment variables
prompts/summarizer.txt		Prompt template for LLM
docs/				Architecture + screenshots