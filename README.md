**Smart Contract Event Monitor (Web3)**
=========================================================================================

This workflow automatically monitors the Ethereum blockchain, extracts USDT transfer events, filters large-value transactions, stores them in Airtable, and sends a clean daily summary alert to Slack.

**1.2 Summary (TL;DR)**
-----------------------

This workflow checks the latest Ethereum block every day and identifies high-value USDT transfers. It fetches on-chain logs using Alchemy, extracts sender/receiver/value details, filters transactions above a threshold, stores them in Airtable, and finally sends a single clear summary alert to Slack.

You receive:

*   **Daily blockchain check (automated)**
    
*   **Airtable tracking of all high-value USDT transfers**
    
*   **A Slack alert summarizing the count + the largest transfer**
    

Ideal for teams wanting simple, automated visibility of suspicious or large crypto movements without manually scanning the blockchain.

### **Quick Start – Implementation Steps**

1.  Add your **Alchemy Ethereum Mainnet API URL** in both HTTP nodes.
    
2.  Connect and configure your **Airtable** base & table.
    
3.  Connect your **Slack** credentials and set the channel for alerts.
    
4.  Adjust the **value threshold** in the IF node (default: 1,000,000,000).
    
5.  Activate the workflow — daily monitoring begins instantly.
    

**1.3 What It Does**
--------------------

This workflow automates detection of high-value USDT transfers on Ethereum:

1.  Fetches the latest block number using Alchemy.
    
2.  Retrieves all USDT Transfer logs from that block.
    
3.  Extracts structured data:
    
    *   Sender
        
    *   Receiver
        
    *   Amount
        
    *   Contract
        
    *   Block number
        
    *   Transaction hash
        
4.  Filters only transactions above a configurable threshold.
    
5.  Saves each high-value transaction into Airtable for record-keeping.
    
6.  Generates a summary including:
    
    *   Total number of high-value transfers
        
    *   The single largest transfer
        
7.  Sends one clean alert message to Slack.
    

This ensures visibility of suspicious or large fund movements with no repeated alerts.

**1.4 Who’s It For**
--------------------

This workflow is ideal for:

*   Crypto analytics teams
    
*   Blockchain monitoring platforms
    
*   Compliance teams tracking high-value activity
    
*   Web3 product teams
    
*   Developers needing automated USDT transfer tracking
    
*   Anyone monitoring whale movements / suspicious transactions
    

**1.5 Requirements to Use This Workflow**
-----------------------------------------

To run this workflow, you need:

*   **n8n instance** (cloud or self-hosted)
    
*   **Alchemy API URL** (Ethereum Mainnet)
    
*   **Airtable base** + Personal Access Token
    
*   **Slack workspace** with API permissions
    
*   Basic understanding of Ethereum logs, hex values & JSON data
    

**1.6 How It Works & Setup Steps**
----------------------------------

### **How It Works**

1.  **Daily Check** – Workflow runs automatically at your set time.
    
2.  **Get Latest Block Number** – Fetches newest Ethereum block from Alchemy.
    
3.  **Fetch USDT Logs** – Queries all Transfer events (ERC-20 standard).
    
4.  **Extract Transaction Details** – Converts hex → readable data.
    
5.  **Filter High-Value Transactions** – Keeps only large value transfers.
    
6.  **Save to Airtable** – Adds each transfer record to your database.
    
7.  **Generate Summary** – Finds the largest transfer & total count.
    
8.  **Send Slack Alert** – Notifies your team with one clean summary.
    

### **Setup Steps**

1.  Import the provided n8n JSON file.
    
2.  Open the **Get Latest Block** and **Fetch Logs** HTTP nodes → add your **Alchemy API URL**.
    
3.  Ensure USDT contract address (already included):0xdAC17F958D2ee523a2206206994597C13D831ec7
    
4.  Connect your **Airtable** account and map:
    
    *   Contract
        
    *   From Address
        
    *   To Address
        
    *   Value
        
    *   Block Number
        
    *   txHash
        
5.  Connect **Slack API** credentials and choose your channel.
    
6.  Change the threshold limit in the IF node if needed (default: 1B).
    
7.  Activate the workflow — done!
    

**1.7 How To Customize Nodes**
------------------------------

### **Customize Value Threshold**

Modify the **IF** node:

*   Increase or decrease the minimum transfer value
    
*   Change logic to smaller or larger whale-tracking
    

### **Customize Airtable Storage**

You can add fields like:

*   Timestamp
    
*   Token symbol
    
*   USD price (using price API)
    
*   Transaction status
    
*   Risk classification
    

### **Customize Slack Alerts**

You may add:

*   Emojis
    
*   Mentions (@channel, @team)
    
*   Links to Etherscan
    
*   Highlighted blocks for critical transfers
    

### **Customize Web3 Provider**

Replace Alchemy with:

*   Infura
    
*   QuickNode
    
*   Public RPC (not recommended for reliability)
    

**1.8 Add-Ons (Optional Enhancements)**
---------------------------------------

You can extend this workflow to:

*   Track multiple ERC-20 tokens
    
*   Process several blocks instead of just the latest
    
*   Add price conversion (USDT → USD value)
    
*   Detect transfers to suspicious wallets
    
*   Generate daily or weekly summary reports in Slack
    
*   Create a dashboard using Airtable Interfaces
    
*   Add OpenAI-based insights (large spike, suspicious pattern, etc.)
    

**1.9 Use Case Examples**
-------------------------

### **1\. Whale Tracking**

Detect large USDT movements (>1M or >5M).

### **2\. Compliance Monitoring**

Log high-value transfers in Airtable for audits.

### **3\. Real-Time Alerts**

Slack alerts tell your team instantly about big movements.

### **4\. On-Chain Analytics**

Automate structured extraction of Ethereum logs.

### **5\. Exchange Monitoring**

Detect large inflows/outflows to known addresses.

**1.10 Troubleshooting Guide**
------------------------------

IssuePossible CauseSolutionNo data in AirtableLogs returned emptyEnsure USDT transfer events exist in that blockValues are “zero”Hex parsing failedCheck extract-code logicSlack alert not sentInvalid credentialsUpdate Slack API keyAirtable errorWrong field namesMatch Airtable column names exactlyHTTP request failsWrong RPC URLRe-check Alchemy API keyWorkflow not runningSchedule disabledEnable "Daily Check" node

**1.11 Need Help?**
-------------------

If you need help customizing or extending this workflow — adding multi-token monitoring, setting up dashboards, improving alerts, or scaling this for production — the **WeblineIndia team** can assist you with advanced automation.