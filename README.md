# 🚀 LeadFlow AI Lite CRM — Agentic Sales & Automated Follow-Up System

![n8n](https://img.shields.io/badge/n8n-Workflow%20Automation-FF6D5A?style=for-the-badge&logo=n8n&logoColor=white)
![Google Sheets](https://img.shields.io/badge/Google%20Sheets-Database-34A853?style=for-the-badge&logo=google-sheets&logoColor=white)
![Telegram](https://img.shields.io/badge/Telegram-Bot%20API-26A5E4?style=for-the-badge&logo=telegram&logoColor=white)
![AI Agent](https://img.shields.io/badge/AI%20Agent-Tool%20Calling-0052CC?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

---

## 📋 Table of Contents
- [📌 Problem Statement](#-problem-statement)
- [💡 Solution Overview](#-solution-overview)
- [⚙️ System Architecture](#️-system-architecture)
- [🧩 Workflow Modules Breakdown](#-workflow-modules-breakdown)
  - [Module 1: Inbound Conversational AI (Lucia Assistant)](#module-1-inbound-conversational-ai-lucia-assistant)
  - [Module 2: Outbound Scheduled CRM Follow-Up Reminder](#module-2-outbound-scheduled-crm-follow-up-reminder)
- [📊 Database Schema (Google Sheets)](#-database-schema-google-sheets)
- [🖼️ Canvas Screenshots & Proof of Work](#️-canvas-screenshots--proof-of-work)
- [🛠️ Tech Stack & Integrations](#️-tech-stack--integrations)
- [🚀 Setup & Installation Guide](#-setup--installation-guide)
- [🔧 Troubleshooting & Common Issues](#-troubleshooting--common-issues)
- [📁 Repository Structure](#-repository-structure)
- [🔒 Security & Privacy Notice](#-security--privacy-notice)

---

## 📌 Problem Statement
Micro, Small, and Medium Enterprises (MSMEs) and fast-scaling retail brands face two critical sales bottlenecks:

1. **High Inquiry Volume & Slow Response Times:** Handling customer questions regarding fragrance notes, product stock, and pricing manually leads to delayed replies and lost buyers.
2. **Neglected Lead Follow-Ups:** Prospective customers logged into spreadsheets are rarely re-engaged in a systematic manner, leaving high-intent sales opportunities behind.

---

## 💡 Solution Overview
**LeadFlow AI Lite CRM** is an end-to-end sales automation engine built on **n8n**. It unifies inbound AI customer service and outbound database reminders into a single, scalable ecosystem:

- **Inbound AI Sales Agent (`Lucia Assistant`):** An intelligent Telegram bot leveraging LLM tool-calling capabilities to provide perfume consultation (brands like Mykonos, Velixir, Octarine), query live stock from Google Sheets (`read_inventory`), and record customer leads (`append_lead`).
- **Outbound CRM Follow-Up Engine:** A background cron trigger executing daily at **18:00 WIB** (`Asia/Jakarta`) to filter leads due for re-engagement, notify the store admin via Telegram, and update status timestamps in real time.

---

## ⚙️ System Architecture

```text
                                 [ CUSTOMER ]
                                      │
                                      ▼
                           [ Telegram Channel ]
                                      │
                                      ▼
                        ┌──────────────────────────┐
                        │  Lucia AI Assistant Bot  │
                        │   (Tool Calling Agent)   │
                        └─────────────┬────────────┘
                                      │
                 ┌────────────────────┴────────────────────┐
                 ▼                                         ▼
     [ read_inventory Tool ]                    [ append_lead Tool ]
                 │                                         │
                 └────────────────────┬────────────────────┘
                                      ▼
                           [ Google Sheets CRM ]
                                      ▲
                                      │
                          (Scheduled Daily Check)
                                      │
                        ┌─────────────┴────────────┐
                        │ CRM Follow-Up Reminder   │
                        │    (Cron @ 18:00 WIB)    │
                        └─────────────┬────────────┘
                                      │
                                      ▼
                            [ Admin Notification ]
