# 🚀 Smart CRM Lead Pipeline (n8n Automation)

This project demonstrates a robust automation workflow built using **n8n**. It intelligently captures new leads from Google Sheets, processes and sanitizes the data, and alerts the sales team via Slack based on custom business logic.

## 🛠 Workflow Architecture

The pipeline follows a professional data processing pattern:
1.  **Ingestion:** Real-time monitoring of a Google Sheet for new rows.
2.  **Sanitization:** Using a `Set/Edit Fields` node with JavaScript/Regex to ensure currency/numeric data is clean and typed correctly.
3.  **Logic Gate:** An `IF` node evaluates the deal value against business thresholds (e.g., $1000+).
4.  **Notification:** High-value leads are formatted and pushed to a specific Slack channel.

## 🧩 Nodes Used
- **Google Sheets Trigger:** Polls for new lead entries.
- **Edit Fields (Set):** Normalizes the `DealValue` using:
  `{{ Number($json.DealValue.toString().replace(/[^0-9.-]+/g,"")) }}`
- **IF Node:** Routes data based on numeric conditions.
- **Slack Node:** Sends rich-text notifications.

## 🚀 How to Use
1.  **Import the Workflow:** Download the `workflow.json` from this repo and import it into your n8n instance.
2.  **Configure Credentials:**
    * Connect your **Google Service Account** or OAuth2.
    * Connect your **Slack Bot Token**.
3.  **Setup the Sheet:** Create a Google Sheet with headers: `Timestamp`, `Name`, `Email`, `DealValue`.
4.  **Activate:** Turn the workflow on and watch the leads flow!

## 🛡️ Best Practices Implemented
- **Data Casting:** Ensures string inputs from Sheets don't break numeric comparisons.
- **Selective Output:** Uses `Include Other Input Fields` to maintain data lineage across the workflow.
- **Error Handling:** Designed to stop or route failed conditions gracefully.

---
*Developed as a showcase of Low-code/No-code Engineering.*
