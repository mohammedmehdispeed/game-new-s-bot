# 🎮 Game News Bot

> 🚧 **Work in Progress** — This project is under active development. Features are being added and improved regularly. Some components may be incomplete or subject to change.

**Current Status:** Beta (v0.5.0)  
**Last Updated:** July 2026  
**Next Milestone:** v1.0 Stable Release

---

**Automated gaming news collector, translator, and publisher** — powered by AI, orchestrated with n8n, scheduled with GitHub Actions, and delivered via Telegram.

> Fetch the latest gaming news from **X (Twitter)** and **RSS feeds** → Translate with AI → Publish to Telegram channels — all without human intervention.

---

## 📊 Project Status Overview

| Component | Status | Notes |
|-----------|--------|-------|
| X (Twitter) API Integration | ✅ Complete | Fetching gaming news via search API |
| RSS Feed Integration | ✅ Complete | Multiple gaming news sources |
| AI Translation | ✅ Complete | OpenAI GPT integration |
| Telegram Publishing | ✅ Complete | Channel and group support |
| GitHub Actions Scheduling | ✅ Complete | Hourly automated runs |
| **Multi-Language Support** | 🚧 In Progress | Adding support for 5+ languages |
| **Discord Integration** | 📅 Planned | Q3 2026 |
| **Web Dashboard** | 📅 Planned | Q4 2026 |
| **Mobile App** | 💡 Idea | Future consideration |

---

## 🚀 Features

- ✅ **Fully Automated** — Runs on a schedule with zero manual effort
- 🎯 **Gaming-Focused** — Curated sources for video game news, updates, and releases
- 🐦 **X (Twitter) Integration** — Fetch news directly from gaming journalists, studios, and official accounts
- 📡 **RSS Support** — Traditional RSS feeds as a secondary news source
- 🌍 **AI-Powered Translation** — Translate news to your preferred language (OpenAI GPT, Google Translate, DeepL)
- 🤖 **Telegram Integration** — Publish to gaming communities, channels, or groups
- ⏱️ **Scheduled Execution** — GitHub Actions runs the workflow periodically (e.g., every 2 hours)
- 🔔 **Real-Time Alerts** — Get notified about major game announcements, patch notes, and releases
- 📊 **Logging & Monitoring** — Track what was posted and when
- 🔍 **Smart Filtering** — Filter by specific game titles, keywords, or exclude unwanted content

---

## 🏗️ Architecture Overview
┌─────────────────────────────────────────────────────────────────────────────┐
│ │
│ ┌─────────────────────┐ ┌─────────────────┐ ┌─────────────────┐ │
│ │ X (Twitter) API │ │ │ │ │ │
│ │ - Search Posts │────▶│ n8n │────▶│ AI Translation │ │
│ │ - News Lookup │ │ Workflow │ │ (OpenAI, etc.) │ │
│ └─────────────────────┘ └─────────────────┘ └─────────────────┘ │
│ ┌─────────────────────┐ │ │
│ │ RSS Feeds │ │ │
│ │ - IGN │──────────────┘ │
│ │ - GameSpot │ │
│ │ - PC Gamer │ │
│ │ - Polygon │ │
│ └─────────────────────┘ │ │
│ ▼ │
│ ┌─────────────────┐ │
│ ┌─────────────────────┐ │ │ │
│ │ GitHub Actions │────▶│ Telegram Bot │ │
│ │ (Scheduler) │ │ (Publisher) │ │
│ └─────────────────────┘ └─────────────────┘ │
│ │
└─────────────────────────────────────────────────────────────────────────────┘
### How it works:

1. **GitHub Actions** triggers the n8n workflow on a schedule (e.g., every 2 hours)
2. **n8n** fetches news from:
   - **X API** (search posts, news lookup)
   - **RSS feeds** (IGN, GameSpot, PC Gamer, etc.)
3. Results are **merged**, **deduplicated**, and **filtered** by keywords
4. Each article is sent to **AI** for translation
5. Translated content is **formatted** and **published** to Telegram channels

---

## 🛠️ Technologies Used

| Component | Technology |
|-----------|------------|
| **Workflow Automation** | n8n (self-hosted or cloud) |
| **Scheduling** | GitHub Actions (cron jobs) |
| **Bot Platform** | Telegram Bot API |
| **AI Translation** | OpenAI GPT / Google Cloud Translation / DeepL |
| **News Fetching (X)** | X API v2 (Search Posts, News Lookup) |
| **News Fetching (RSS)** | RSS feeds, HTTP requests |
| **Scripting** | Python / JavaScript (helper scripts) |
| **Version Control** | Git + GitHub |

---

## 📋 Prerequisites

Before you start, make sure you have:

- [ ] A **Telegram Bot Token** (create via [@BotFather](https://t.me/botfather))
- [ ] A **Telegram channel** or group for publishing gaming news
- [ ] An **n8n instance** (self-hosted or n8n.cloud)
- [ ] An **AI Translation API Key** (OpenAI / Google / DeepL)
- [ ] **X Developer Account** with API credentials (Bearer Token)
- [ ] A **GitHub repository** with Actions enabled
- [ ] **Node.js 18+** (if self-hosting n8n)

---

## 🐦 X (Twitter) API Setup

### 1. Get X API Credentials

1. Go to [developer.x.com](https://developer.x.com)
2. Sign up for a developer account (Free tier available)
3. Create a new project and app
4. Generate a **Bearer Token** from the "Keys and Tokens" section

### 2. X API Limits & Costs

| Plan | Search Requests | News Lookup | Cost |
|------|----------------|-------------|------|
| **Free** | 10 requests/day | Not available | Free |
| **Basic** | 500 requests/month | Not available | ~$100/month |
| **Pro** | 1,000 requests/month | Yes | ~$200/month |
| **Enterprise** | Custom | Yes | Custom |

> 💡 **Recommendation**: Start with the Free tier for testing. If you need more, upgrade to Basic or Pro.

### 3. Recommended Search Queries for Gaming News

| Query Type | Example |
|------------|---------|
| **General Gaming News** | `(gaming OR "video games" OR "game news") has:links lang:en -is:retweet -is:reply` |
| **Specific Games** | `("GTA 6" OR "Grand Theft Auto" OR "Elder Scrolls" OR "Final Fantasy") has:links` |
| **From Official Accounts** | `from:IGN OR from:GameSpot OR from:PCGamer OR from:PlayStation` |
| **Gaming Hashtags** | `#gamingnews OR #gameannouncement OR #gamedev has:links` |
| **Trailers & Videos** | `(gameplay OR trailer OR announcement) has:video_link has:links` |

---

## 📡 RSS Feeds (Secondary Source)

You can also add traditional RSS feeds as a backup or additional source:

| Source | RSS URL |
|--------|---------|
| **IGN** | `https://feeds.feedburner.com/ign/news` |
| **GameSpot** | `https://www.gamespot.com/feeds/news/` |
| **PC Gamer** | `https://www.pcgamer.com/rss/` |
| **Destructoid** | `https://www.destructoid.com/feed/` |
| **Eurogamer** | `https://www.eurogamer.net/feed` |
| **Kotaku** | `https://kotaku.com/feed` |
| **Polygon** | `https://www.polygon.com/rss/index.xml` |
| **Rock Paper Shotgun** | `https://www.rockpapershotgun.com/feed` |

---

## ⚙️ Installation

### 1. Clone the repository
```bash
git clone https://github.com/yourusername/game-news-bot.git
cd game-news-bot
```

### 2. Install dependencies (if using helper scripts)
```bash
npm install
# or
pip install -r requirements.txt
```

### 3. Configure environment variables
Create a `.env` file in the root directory and add the following configuration:
<details>
<summary>📋 Click to expand environment variables</summary>

```env
# Telegram
TELEGRAM_BOT_TOKEN=your_bot_token_here
TELEGRAM_CHANNEL_ID=@your_gaming_channel

# AI Translation
OPENAI_API_KEY=your_openai_key_here
TRANSLATION_TARGET_LANGUAGE=English

# X (Twitter) API
X_BEARER_TOKEN=your_x_bearer_token_here
X_SEARCH_QUERY=(gaming OR "video games" OR "game news") has:links lang:en -is:retweet -is:reply

# RSS Feeds
RSS_FEEDS=https://feeds.feedburner.com/ign/news,https://www.gamespot.com/feeds/news/

# n8n
N8N_WEBHOOK_URL=https://your-n8n-instance.com/webhook/your-workflow

# Optional
GAME_FILTER=GTA,Cyberpunk,Starfield
EXCLUDE_KEYWORDS=spam,advertisement
```
</details>

> ⚠️ **Important**: Never commit your `.env` file to version control. Add it to `.gitignore`.

### 4. Import the n8n workflow
1. Open your n8n instance
2. Import the workflow from `/workflows/game-news-bot.json`
3. Configure the **X API HTTP Request** node with your Bearer Token
4. Configure the **RSS HTTP Request** nodes with your feed URLs
5. Set up the **Telegram** node with your bot token
6. Activate the workflow
