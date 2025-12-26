# 🛒 Cart Abandonment Recovery Automation (n8n)

An **end-to-end Cart Abandonment Recovery Automation** built using **n8n**, designed to intelligently detect abandoned WooCommerce carts, segment customers, schedule optimized follow-ups, send automated reminders, update CRM records, notify internal teams, and log recovery outcomes.

This workflow enables **data-driven, timed, and personalized recovery actions** with minimal manual intervention.
<img width="2250" height="553" alt="image" src="https://github.com/user-attachments/assets/8effe551-ede1-4df4-8c4f-25cfc7ec777b" />

---

## 📌 Key Features

* ⏱️ Scheduled abandoned cart detection (every 2 hours)
* 🧠 Intelligent cart analysis & customer segmentation
* 🎯 Dynamic recovery strategy & discount allocation
* ⌛ Optimized follow-up timing with wait conditions
* 📧 Automated multi-stage email reminders
* 📊 CRM updates and recovery tracking
* 🔔 Internal Slack notifications
* 🧾 Centralized logging in Google Sheets

---

## 🧩 Workflow Architecture Overview

```
Schedule Trigger
   ↓
Fetch Pending WooCommerce Orders
   ↓
Analyze Cart & Customer Data
   ↓
Enhanced Segmentation (CRM-based)
   ↓
Determine Follow-up Timing
   ↓
Wait → Recheck Order Status
   ↓
Reminder Emails + CRM Update + Slack Alert
   ↓
Final Status Check (After 24h)
   ↓
Log Recovery Outcome
```

---

## 🔄 Detailed Workflow Breakdown

### 1️⃣ Scheduled Cart Monitoring

* **Trigger**: Runs every **2 hours**
* **Node**: `Schedule Cart Check`
* Ensures continuous monitoring of abandoned carts without manual effort

---

### 2️⃣ Abandoned Cart Detection

* **Integration**: WooCommerce REST API
* **Criteria**:

  * Order status = `pending`
  * Created/modified within the last 2 hours
* **Node**: `Get Abandoned Carts`

---

### 3️⃣ Cart & Customer Analysis

* **Node**: `Analyze Cart Data` (Code Node – JavaScript)
* Calculates:

  * Total cart value
  * Number of items
  * Product categories
* Determines:

  * New vs Returning customer
  * Recovery strategy:

    * `simple_reminder`
    * `offer_discount`
    * `urgency_message`
* Assigns discount dynamically (5%, 10%, etc.)

---

### 4️⃣ CRM-Based Enhanced Segmentation

* **Node**: `Get Customer Profile`
* Fetches customer order history
* **Node**: `Enhanced Segmentation`
* Upgrades segmentation to:

  * `returning`
  * `loyal`
* Adjusts:

  * Discount percentage
  * Messaging strategy
  * Priority level

---

### 5️⃣ Follow-up Timing Optimization

* **Node**: `Calculate Follow-up Timing`
* Delay logic:

  * Urgency → 30 mins
  * Discount → 60 mins
  * Reminder → 120 mins
* **Node**: `Wait for Optimal Timing`

---

### 6️⃣ Order Re-validation

* **Node**: `Check Order Status`
* Confirms whether the cart is still abandoned before sending reminders
* Prevents unnecessary emails

---

### 7️⃣ Reminder & Notifications

If cart is still pending:

* 📧 **Email Reminder** via Gmail
* 🔔 **Slack Notification** to internal team
* 🧠 **CRM Update** in HubSpot

---

### 8️⃣ Follow-up After 24 Hours

* **Node**: `Wait 24h for Follow-up`
* Rechecks order completion
* Sends additional reminders if needed

---

### 9️⃣ Final Logging & Reporting

* **Google Sheets Logging**:

  * Cart details
  * Customer segment
  * Recovery strategy
  * Success or failure
* Enables reporting & analytics

---

## 🧪 Technologies & Tools Used

### 🔧 Core Automation

* **n8n** – Workflow orchestration & automation engine

### 🛒 E-commerce

* **WooCommerce REST API**

  * Fetch orders
  * Check order status
  * Cart recovery links

### 📧 Communication

* **Gmail API**

  * Automated reminder emails
* **Slack API**

  * Internal team notifications

### 🧠 CRM

* **HubSpot API**

  * Customer profile updates
  * Engagement tracking

### 📊 Data Logging

* **Google Sheets API**

  * Centralized recovery tracking

### 🧩 Scripting

* **JavaScript (n8n Code Nodes)**

  * Cart analytics
  * Customer segmentation
  * Dynamic decision logic

---

## 🔐 Credentials Required

| Service       | Auth Type       |
| ------------- | --------------- |
| WooCommerce   | HTTP Basic Auth |
| Gmail         | OAuth 2.0       |
| HubSpot       | OAuth 2.0       |
| Slack         | OAuth 2.0       |
| Google Sheets | OAuth 2.0       |

---

## 🚀 Use Cases

* E-commerce cart recovery automation
* Customer retention workflows
* CRM-driven personalized marketing
* Sales funnel optimization
* Internal sales/ops visibility

---

## 📈 Benefits

* Reduces manual follow-ups
* Prevents lost revenue from abandoned carts
* Personalized recovery increases conversion rate
* Fully auditable & scalable workflow
* Plug-and-play with existing WooCommerce stores

---

## 🧠 Future Enhancements (Optional)

* WhatsApp/SMS reminders
* AI-generated personalized email content
* A/B testing recovery strategies
* Revenue attribution dashboards
* LLM-based customer intent scoring

---

## 🧾 License

MIT 

