# 📈 Financial Tracking AI Multi-Agent System

Note: This repository showcases the architecture and implementation concepts developed during my AI/ML Engineering Internship. Some proprietary business logic and sensitive credentials have been sanitized or omitted for confidentiality.

## 🚀 Overview

- This project is a scalable, end-to-end AI Multi-Agent System designed to automate financial workflows, simulate stock trading strategies, and provide real-time market intelligence. Built with production-readiness in mind, the system leverages Google ADK for multi-agent coordination, served by a high-performance FastAPI backend, and deployed via Docker.

- End-users interact with the system seamlessly through a conversational Telegram Bot UI.

## ✨ Key Features

- **Intelligent Multi-Agent Coordination**: Utilizes Google ADK to deploy specialized agents for stock scheduling, buy/sell simulations, and real-time company data retrieval (web scraping).

- **Low-Latency API Service**: Powered by FastAPI to handle asynchronous requests between the Telegram frontend and the heavy-lifting AI agents.

- **Robust Data Pipeline**:

- **PostgreSQL**: Serves as the primary source of truth for structured financial data, user sessions, and transaction logs.

- **Redis**: Implemented as a caching layer to drastically reduce latency for frequently queried stock data.

- **Conversational UX**: Integrated with the Telegram Bot API to provide an intuitive, chat-based interface for complex financial queries.

- **Fully Containerized**: The entire application stack (API, DB, Cache, Bot) is containerized using Docker & Docker Compose for consistent, one-click deployments.

## 🏗️ System Architecture

- **Client Layer**: User sends a query via the Telegram Bot.

- **API Gateway (FastAPI)**: Receives the payload, validates it, and checks Redis for cached responses.

- **Agent Orchestration (Google ADK)**: If no cache exists, the request is routed to the appropriate AI Agent (e.g., Scraping Agent, Trading Simulator Agent).

- **Data Persistence**: Agents read/write long-term structured data to PostgreSQL.

- **Response**: The formulated financial insight is sent back through FastAPI to the user's Telegram chat.

## 💻 Tech Stack

- **Core AI & Logic**: Python, Google ADK, Web Scraping (BeautifulSoup/Selenium)

- **Backend Framework**: FastAPI, Uvicorn

- **Databases**: PostgreSQL (Relational Data), Redis (Caching)

- **Deployment & DevOps**: Docker, Docker Compose

- **Integrations**: Telegram Bot API

## 🛠️ Local Setup & Deployment

The application is designed to be easily spun up using Docker Compose.

**- Prerequisites:**

Docker & Docker Compose installed

A valid Telegram Bot Token from BotFather

**- Installation:**

**1. Clone the repository:**

```bash
git clone https://github.com/YuInH/Financial-MultiAgent-System.git
cd Financial-MultiAgent-System
```

**2. Configure Environment Variables: Create a .env file in the root directory and add your credentials:**

```python
TELEGRAM_BOT_TOKEN=your_token_here
POSTGRES_USER=admin
POSTGRES_PASSWORD=securepassword
POSTGRES_DB=finance_db
REDIS_URL=redis://redis:6379/0`
```

**3. Build and Run with Docker Compose:**

```bash
docker-compose up -d --build
```

**4. Verify the Services:**

**FastAPI Swagger UI**: `http://localhost:8000/docs`

The Telegram bot will now be active and listening for messages!

## 📈 Future Improvements (Roadmap)

**Implement Kafka**: Handling high-throughput, real-time stock ticker streams.

**Add Grafana/Prometheus:** Tracking API latency and agent execution times.

**Integrate CI/CD pipelines via GitHub Actions:** Automated testing.
