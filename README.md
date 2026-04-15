# Eco-Sort AI Agent 🌍

**Eco-Sort AI** is an intelligent automation system designed to simplify waste management. It leverages **Google Gemini** as its decision engine to analyze waste types, logs interaction data into **Google Sheets**, and provides a seamless user interface via **WhatsApp**. 

The project is built to run on a local machine using **Docker** and is made globally accessible through an **ngrok** secure tunnel.

---

## 🛠️ Technical Configuration

### 1. Docker Environment Variables
To ensure the agent functions correctly with your ngrok tunnel and local storage, configure your container with the following:

| Variable | Value |
| :--- | :--- |
| **N8N_EDITOR_BASE_URL** | `https://lowell-water-ernest.ngrok-free.dev` |
| **WEBHOOK_URL** | `https://lowell-water-ernest.ngrok-free.dev` |
| **N8N_COMMUNITY_PACKAGES_ALLOW_TOOL_USAGE** | `true` |
| **N8N_DEFAULT_BINARY_DATA_MODE** | `filesystem` |
| **NODE_VERSION** | `24.13.1` |

### 2. Hardware & Network Setup
* **Volume Mapping:** `/home/node/.n8n` is mapped to a persistent local directory to store workflows and credentials securely.
* **Port Forwarding:** `5678:5678`
* **Tunneling:** Local traffic is routed via **ngrok**. Start the tunnel using: `ngrok http 5678`.

---

## 🔑 API Integration Guide

This agent requires three primary integrations to be fully operational:

### **Google Gemini (AI Engine)**
* API keys are generated via **Google AI Studio**.
* Responsible for identifying waste categories, environmental impacts, and suggesting the nearest recycling centers.

### **Google Sheets (Database)**
* Requires Sheets and Drive APIs enabled in the **Google Cloud Console**.
* Serves as the centralized repository for all user inputs and AI analysis.

### **WhatsApp Cloud API (User Interface)**
* Managed via **Meta for Developers**.
* **Requirement:** The Webhook callback URL in the Meta Dashboard must point to the active ngrok address.

---

## 📊 Database Schema & Template

The system utilizes a two-sheet structure within a single spreadsheet to manage data flow.

### **Spreadsheet Template**
To use this project, you can create your own copy of the database structure here:
🔗 **[Click here to Create a Copy of the Google Sheets Template](https://docs.google.com/spreadsheets/d/1y0oeqj_zl_lTucX9vUrR1m48Ma6HuEBsyLc72At-OLo/edit?usp=sharing)**

### **Sheet Structure:**
1. **Sheet 1 (User Input):** Logs raw data (`Name`, `Whatsapp Number`, `Location`, `Waste Item`, `Timestamp`).
2. **Sheet 2 (Output):** Stores the finalized AI analysis (`User Name`, `Identified Item`, `Waste Category`, `Environmental Impact`, `Nearest Center`, `Time Stamp`).

---

## 🚀 How to Deploy

### Option 1: Local Host (Current Setup)
1. Ensure **Docker Desktop** and **ngrok** are active on the host machine.
2. Import the `Eco-Sort_AI.json` file into your n8n instance.
3. Authenticate Gemini, Sheets, and WhatsApp credentials in the respective nodes.
4. Set the workflow to **Active** to begin processing live requests.

### Option 2: n8n Cloud
1. Import the `Eco-Sort_AI.json` file to a managed n8n Cloud instance.
2. *Note:* When using Cloud hosting, local Docker variables and ngrok tunneling are not required.

---

## 🌟 Core Features
* ✅ **Real-time Classification:** Instant, high-precision waste sorting powered by Gemini AI.
* ✅ **Automated Logging:** Hands-free data entry into Google Sheets for tracking.
* ✅ **Impact Analysis:** Provides users with the environmental context of their waste items.
* ✅ **Local Data Privacy:** Binary data is processed and stored on a persistent local filesystem.
* ✅ **Universal Access:** WhatsApp integration ensures ease of use for end-users.

---

<p align="center">
  <b>Designed for a Sustainable Future ♻️</b>
</p>
