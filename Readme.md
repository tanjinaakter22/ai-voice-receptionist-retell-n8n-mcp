
# 🎙️ AI Voice Receptionist & Automated Booking System
### Powered by Retell AI + n8n MCP + Google Sheets

An intelligent **AI Voice Receptionist and Appointment Booking System** designed for a luxury Spa & Salon business.

This project uses **Retell AI** and **n8n Model Context Protocol (MCP)** to automate customer interactions, answer service-related questions, check staff availability, book appointments, capture potential leads, and manage customer conversations in real time.

The AI receptionist, named **Cimo**, provides a natural and professional customer experience while reducing manual receptionist workload.

---

## 🌟 Project Highlights

- 🤖 **AI-Powered Voice Receptionist** – Handles inbound customer calls through natural, human-like conversations.
- 💬 **Smart Customer Support** – Answers questions about salon services, treatments, durations, and pricing.
- 📅 **Automated Appointment Booking** – Collects customer details and books appointments automatically.
- 👩‍💼 **Staff Availability Checking** – Checks available staff and time slots before confirming appointments.
- 📊 **Live Database Integration** – Reads and writes customer information using Google Sheets.
- 🧲 **Lead Capture Automation** – Stores potential customer information for future follow-ups.
- 🔄 **Human Handoff** – Logs complex requests and complaints that require human assistance.
- 📝 **Conversation Logging** – Saves call summaries, customer intent, and call outcomes.

---

## 🏗️ System Architecture

The system connects the customer, Retell AI voice agent, n8n MCP server, and Google Sheets database.

```text
┌────────────────────────────┐
│       📞 Customer          │
│       Inbound Call         │
└─────────────┬──────────────┘
              │
              ▼
┌────────────────────────────┐
│       🤖 Retell AI         │
│    Voice Agent: Cimo       │
│                            │
│  Natural Conversations     │
│  Customer Interaction      │
└─────────────┬──────────────┘
              │
              ▼
┌────────────────────────────┐
│       ⚙️ n8n MCP Server    │
│                            │
│   MCP Server Trigger       │
│   6 Specialized Tools      │
└─────────────┬──────────────┘
              │
              ▼
┌────────────────────────────┐
│      📊 Google Sheets      │
│                            │
│  Services & Pricing        │
│  Staff Availability        │
│  Appointments              │
│  Leads & Call Logs         │
└────────────────────────────┘
```

### 🔄 How It Works

1. 📞 A customer calls the salon.
2. 🤖 Retell AI's voice agent, Cimo, answers the call.
3. 💬 The customer asks about services, prices, or appointments.
4. ⚙️ Retell AI communicates with n8n through the MCP connection.
5. 📊 n8n accesses Google Sheets through specialized tools.
6. 📅 The system checks staff availability and processes booking requests.
7. ✅ Confirmed appointments are saved automatically.
8. 📝 Customer interactions and call summaries are logged.

---

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| 🤖 Retell AI | AI Voice Agent & Customer Conversations |
| ⚙️ n8n | Workflow Automation & MCP Server |
| 🔌 Model Context Protocol (MCP) | Connects the AI agent with external tools |
| 📊 Google Sheets | Live Database & Data Management |
| 📞 Twilio (Optional) | Phone Number & Inbound Call Integration |

---

## 🔧 Configured MCP Tools

The n8n MCP Server exposes six specialized tools to the Retell AI agent.

| MCP Tool | Operation | Function |
|---|---|---|
| 🔍 Search Service | Read | Retrieves salon services, descriptions, and pricing |
| 👩‍💼 Staff Availability | Read | Checks staff schedules and available time slots |
| 📅 Appointments | Append | Saves confirmed appointment details |
| 🧲 Leads | Append | Captures potential customer inquiries |
| 🙋 Human Handoff | Append | Logs requests requiring human assistance |
| 📝 Conversation Log | Append | Records call summaries and outcomes |

---

## 📊 Google Sheets Database Structure

The system uses a Google Sheets database named:

**AI Salon & Spa Database**

It contains six dedicated worksheets:

| Worksheet | Description |
|---|---|
| 🧴 `search_service` | Salon services, descriptions, duration, and pricing |
| 📅 `Appointments` | Customer bookings and appointment details |
| 🧲 `Leads` | Potential customer information |
| 👩‍💼 `Staff_Availability` | Staff schedules and availability |
| 🙋 `Human_Handoff` | Escalation requests and callback information |
| 📝 `Conversation_Log` | Call summaries, customer intent, and outcomes |

---

## ✨ Key Automation Features

### 1. 🤖 Intelligent Voice Interaction
Cimo handles customer conversations naturally and provides information about salon services and pricing.

### 2. 📅 Automated Appointment Management
The system collects:
- Customer Name
- Phone Number
- Requested Service
- Preferred Date
- Preferred Time
- Preferred Staff

It checks availability and confirms booking details with the customer before saving the appointment.

### 3. 🆔 Automated Appointment ID Generation
Generates structured appointment IDs.

Example:

`APT-20261118-JAIMA-1500`

### 4. 🧲 Automated Lead Capture
If a customer does not book immediately, their contact details and service interests can be stored for future follow-up.

### 5. 🙋 Human Escalation
Complex questions, complaints, or special requests can be logged for human staff intervention.

### 6. 📋 Automated Call Logging
Stores call summaries and outcomes to support customer management and business analytics.

---

## 🚀 Setup & Installation

### Step 1: Import n8n Workflow

1. Open your n8n instance.
2. Import the `workflow.json` file.
3. Configure Google Sheets OAuth2 credentials.
4. Connect the credentials to all relevant Google Sheets nodes.
5. Verify the MCP Server Trigger configuration.
6. Publish the workflow and copy the production MCP URL.

### Step 2: Configure Retell AI

1. Open the [Retell AI Dashboard](https://dashboard.retellai.com/).
2. Create a new Single-Prompt Voice Agent.
3. Configure the voice agent named `Cimo`.
4. Add the system instructions from `prompt.txt`.
5. Navigate to the MCP configuration section.
6. Connect the n8n MCP production URL.
7. Enable the required MCP tools.
8. Test the connection and tool execution.

### Step 3: Connect Phone Integration (Optional)

For real inbound phone calls:

- Configure a supported phone number.
- Integrate Twilio or another supported telephony provider.
- Connect the phone number to the Retell AI agent.
- Test inbound calling and appointment booking.

---

## 📁 Repository Structure

```text
ai-voice-receptionist-retell-n8n-mcp/
│
├── 📄 README.md
├── ⚙️ workflow.json
├── 📝 prompt.txt
│
└── 📂 assets/
    ├── architecture.png
    ├── n8n-workflow.png
    ├── google-sheets-database.png
    └── demo-preview.png
```

---

## 🧪 Testing & Demo

The system can be tested using the Retell AI Test Audio interface.

### Example Test Scenarios

| Test | Expected Result |
|---|---|
| Ask about facial treatments | Retrieves service information |
| Ask about service pricing | Provides database-based pricing |
| Request an appointment | Collects booking details |
| Ask for a specific stylist | Checks staff availability |
| Confirm a booking | Saves appointment in Google Sheets |
| Make an inquiry without booking | Captures potential lead |
| Request human assistance | Logs a handoff request |

### 🎥 Demo Preview

Screenshots and demonstration materials will be available in the `assets/` folder.


## 📸 Project Screenshots

### ⚙️ n8n Workflow Architecture
<img width="1366" height="768" alt="Screenshot (8)" src="https://github.com/user-attachments/assets/f3aa1567-56b6-4ddf-9545-3a51a8306aa8" />


### 🤖 Retell AI Voice Agent
<img width="1280" height="719" alt="image_2026-11-16_10-52-56" src="https://github.com/user-attachments/assets/c669477e-a90f-4e50-a280-4acc000793f1" />


### 🔌 MCP Tools Configuration
<img width="1366" height="768" alt="Screenshot (9)" src="https://github.com/user-attachments/assets/7f272789-bc9e-4c2b-8fd9-2c14afc1902b" />
![MCP Tools](assets/mcp-tools.png)

### 📊 Google Sheets Database
<img width="1366" height="768" alt="Screenshot (10)" src="https://github.com/user-attachments/assets/5fb94d22-8fa2-4210-b13a-17cd556f16ff" />


### 📅 Automated Appointment Booking
<img width="1366" height="768" alt="Screenshot (7)" src="https://github.com/user-attachments/assets/df9ec029-0324-4258-992c-28f34c98c1f8" />



## 💼 Business Value

This automation system helps Spa & Salon businesses:

- ⏰ Reduce manual receptionist workload.
- 📞 Handle customer inquiries efficiently.
- 📅 Simplify appointment scheduling.
- 📊 Maintain organized customer records.
- 🎯 Capture potential customers automatically.
- 🚀 Improve customer service and operational efficiency.

---

## 👩‍💻 Developed By

**Tanjina Akter**  
AI Automation Specialist

🔗 **LinkedIn:** https://www.linkedin.com/in/tanjina-akter-0727563a9/

💻 **GitHub:** https://github.com/tanjinaakter22

---

### ⭐ Support & Connect

If you find this project interesting, feel free to explore the repository and connect with me!

**Building smarter business solutions through AI and automation. 🚀**
