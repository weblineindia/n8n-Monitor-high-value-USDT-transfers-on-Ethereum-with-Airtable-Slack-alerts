# Smart Contract Event Monitor (Web3)

This workflow automatically monitors the Ethereum blockchain, extracts **USDT transfer events**, filters **large-value transactions**, stores them in **Airtable**, and sends a **clean daily summary alert to Slack**.

---

## 1.2 Summary (TL;DR)

This workflow checks the latest Ethereum block on a daily basis and identifies high-value USDT transfers. It fetches on-chain logs using **Alchemy**, extracts sender, receiver, and value details, filters transactions above a defined threshold, stores them in Airtable, and sends a single, concise summary alert to Slack.

You receive:

- **Daily blockchain check (fully automated)**
- **Airtable tracking of all high-value USDT transfers**
- **Slack alert summarizing total count and largest transfer**

Ideal for teams needing simple, automated visibility into large or suspicious crypto movements without manually scanning the blockchain.

---

## ⚡ Quick Start – Implementation Steps

1. Add your **Alchemy Ethereum Mainnet API URL** to both HTTP Request nodes.
2. Connect and configure your **Airtable** base and table.
3. Connect your **Slack** credentials and select the alert channel.
4. Adjust the **value threshold** in the IF node (default: `1,000,000,000`).
5. Activate the workflow — daily monitoring begins immediately.

---

## 📌 What It Does

This workflow automates detection of high-value USDT transfers on Ethereum:

1. Fetches the latest Ethereum block number using Alchemy.
2. Retrieves all **USDT Transfer (ERC-20)** logs from that block.
3. Extracts structured transaction data:
   - Sender address
   - Receiver address
   - Transfer amount
   - Token contract
   - Block number
   - Transaction hash
4. Filters only transactions above a configurable value threshold.
5. Stores each qualifying transaction in Airtable.
6. Generates a daily summary:
   - Total number of high-value transfers
   - Largest single transfer
7. Sends one clean summary alert to Slack.

This prevents alert spam while maintaining full visibility.

---

## 👥 Who’s It For

This workflow is ideal for:

- Crypto analytics teams
- Blockchain monitoring platforms
- Compliance and risk teams
- Web3 product teams
- Developers tracking USDT movements
- Anyone monitoring whale or suspicious transactions

---

## 🛠 Requirements

To run this workflow, you need:

- **n8n instance** (cloud or self-hosted)
- **Alchemy API URL** (Ethereum Mainnet)
- **Airtable account** with Personal Access Token
- **Slack workspace** with API permissions
- Basic familiarity with Ethereum logs and hex data

---

## ⚙️ How It Works & Setup Steps

### How It Works

1. **Daily Trigger** – Workflow runs at a scheduled time.
2. **Get Latest Block** – Fetches the most recent Ethereum block.
3. **Fetch USDT Logs** – Queries ERC-20 `Transfer` events.
4. **Extract Transaction Details** – Converts hex values into readable numbers.
5. **Filter High-Value Transfers** – Keeps only large transactions.
6. **Save to Airtable** – Logs each transaction for tracking.
7. **Generate Summary** – Identifies the largest transfer and total count.
8. **Send Slack Alert** – Posts one clean daily summary.

---

### Setup Steps

1. Import the provided workflow JSON into n8n.
2. Open the **Get Latest Block** and **Fetch Logs** HTTP nodes and paste your **Alchemy API URL**.
3. Confirm the USDT contract address (preconfigured):


4. Connect your **Airtable** account and map these fields:
- Contract
- From Address
- To Address
- Value
- Block Number
- Transaction Hash
5. Connect **Slack API** credentials and select a channel.
6. Adjust the threshold in the **IF** node if required.
7. Activate the workflow.

---

## 🧩 How To Customize Nodes

### Customize Value Threshold

In the **IF** node, you can:

- Increase or decrease the minimum transfer size
- Switch logic for aggressive or conservative whale tracking

---

### Customize Airtable Storage

Add optional fields such as:

- Timestamp
- Token symbol
- USD value
- Transaction status
- Risk or severity level

---

### Customize Slack Alerts

Enhance notifications with:

- Emojis and formatting
- Mentions (`@channel`, `@team`)
- Etherscan links
- Highlighted critical transactions

---

### Customize Web3 Provider

Replace Alchemy with:

- Infura
- QuickNode
- Other RPC providers (public RPCs not recommended)

---

## ➕ Optional Enhancements

You can extend this workflow to:

- Monitor multiple ERC-20 tokens
- Process multiple blocks per run
- Convert token values to USD
- Detect transfers to known or suspicious wallets
- Generate weekly or monthly reports
- Build dashboards using Airtable Interfaces
- Add AI-based anomaly detection

---

## 📈 Use Case Examples

### 1. Whale Tracking
Detect large USDT movements (e.g., >1M or >5M).

### 2. Compliance Monitoring
Maintain an auditable log of high-value transfers.

### 3. Automated Alerts
Receive one clean Slack alert per day.

### 4. On-Chain Analytics
Structured extraction of Ethereum event logs.

### 5. Exchange Flow Monitoring
Track large inflows and outflows to known wallets.

---

## 🧪 Troubleshooting Guide

| Issue | Possible Cause | Solution |
|------|---------------|----------|
| No data in Airtable | No Transfer logs in the latest block | Confirm USDT transfers occurred in that block |
| Transfer value is zero | Hex parsing logic incorrect | Verify extraction and conversion code |
| Slack alert not sent | Invalid Slack credentials or channel ID | Recheck Slack API token and channel |
| Airtable error | Field or table name mismatch | Match Airtable column names exactly |
| HTTP request fails | Invalid Alchemy API URL | Verify API key and endpoint |
| Workflow not running | Trigger disabled | Enable the Daily Trigger node |

---

## 💬 Need Help?

If you need help extending or scaling this workflow — multi-token tracking, dashboards, enhanced alerts, or production hardening — the **WeblineIndia team** can assist with advanced Web3 automation and monitoring solutions.

---
