# 🎮 Game News Bot

**Automated gaming news collector, translator, and publisher** — powered by AI, orchestrated with n8n, scheduled with GitHub Actions, and delivered via Telegram.

> Fetch the latest gaming news from **X (Twitter)** and **RSS feeds** → Translate with AI → Publish to Telegram channels — all without human intervention.

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
┌─────────────────────┐ ┌─────────────────┐ ┌─────────────────┐
│ X (Twitter) API │ │ │ │ │
│ - Search Posts │────▶│ n8n │────▶│ AI Translation │
│ - News Lookup │ │ Workflow │ │ (OpenAI, etc.) │
└─────────────────────┘ └─────────────────┘ └─────────────────┘
┌─────────────────────┐ │
│ RSS Feeds │ │
│ - IGN, GameSpot, │──────────────┘
│ PC Gamer, etc. │ │
└─────────────────────┘ ▼
┌─────────────────┐
┌─────────────────────┐ │ Telegram Bot │
│ GitHub Actions │────▶│ (Publisher) │
│ (Scheduler) │ └─────────────────┘
└─────────────────────┘
**How it works:**
1. GitHub Actions triggers the n8n workflow on a schedule
2. n8n fetches news from **X API** (search posts, news lookup) and **RSS feeds**
3. Results are merged, deduplicated, and filtered by keywords
4. Each article is sent to AI for translation
5. Translated content is formatted and published to Telegram channels

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
## 🚧 Project Status

This project is **under active development**. Features are being added and improved continuously.

**Current Status:** Beta / MVP (Minimum Viable Product)
**Next Milestone:** v1.0 Stable Release
