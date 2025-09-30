# Project Fenix

AI-powered SaaS platform for automated customer service and booking management.

## Overview

Multi-tenant chatbot system with personality-based AI agents, real-time booking engine, and Discord-based management interface. Built for scalable deployment to Italian SMBs.

## Technical Stack

- **Backend**: Node.js, Supabase (PostgreSQL), Discord.js
- **AI Engine**: Google Gemini 1.5 Flash
- **Customer Interface**: Telegram Bot API (testing), WhatsApp Business API (planned)

## Architecture

Discord Admin Interface → Supabase Database ← AI Agent ← Customer (Telegram/WhatsApp)

**Key Design Decisions:**
- Template-based personality system eliminates per-client prompt engineering
- In-memory conversation state for MVP (20-30 concurrent businesses)
- Parallel data fetching for performance optimization
- Modular command routing for maintainability

## Project Structure

discord-bot/
├── index.js              # Application bootstrap
├── admin-commands.js     # Admin management (9 commands)
├── user-commands.js      # Business owner commands (5 commands)
├── simplified_agent.js   # AI conversation engine + booking logic
├── prompts.js            # Personality templates
├── database.js           # Supabase data access layer
├── telegram_bot.js       # Customer interface
└── test_agent.js         # Test suite

## Features

**For Administrators:**
- Client onboarding via Discord slash commands
- Template-based personality configuration (5 presets)
- Real-time business configuration management

**For Business Owners:**
- Self-service hours, services, and contact management
- Zero technical knowledge required

**For End Customers:**
- Natural language booking conversations
- Automated availability checking
- Multi-step appointment flow with confirmation

## Scalability Path

- **Current**: 20-30 businesses, in-memory state
- **Next Phase**: Redis for state persistence, 100+ businesses
- **Production**: Horizontal scaling with load balancing

## Setup

cd discord-bot
npm install
cp .env.example ../.env
# Configure environment variables
node index.js

## Status

Private MVP - Active Development
