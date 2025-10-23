# Cold-Mail-Automation-Workflow# 📩 

## 🧠 Overview
This project is a **no-code cold email automation system built using n8n**.  
It automates sending **up to 500 personalized emails per day**, directly from your Gmail or SMTP account, using contact data stored in **Google Sheets**.

The workflow was created while learning n8n and demonstrates how to design a complete email campaign automation — **without writing a single line of code**.

---

## ⚙️ Features
- 🔄 **Fully automated workflow** from data fetching to email delivery  
- 📋 **Reads contacts directly from Google Sheets**  
- ✉️ **Sends personalized emails** with dynamic name and message fields  
- 🕓 **Automatic delays (Wait node)** between each send to avoid spam flags  
- 📊 **Logs email status** (sent, failed, etc.) back to Google Sheets  
- 🧱 **No-code setup** — entirely built using n8n’s visual interface  

---

## 🗂️ Files
-  Exported n8n workflow file  
  *(Import the file directly into your n8n instance.)*
- Your Google Sheet containing recipient details (e.g., Name, Email, Company, etc.)

---

## 🚀 Setup Instructions

### 1️⃣ Import Workflow
- Open your **n8n dashboard**.  
- Go to **Workflows → Import from File**.  
- Upload the `cold_mail_automation.json` file.  

---

### 2️⃣ Connect Google Sheets
- Create a Google Sheet with columns like:  
  `Name | Email | Status | Company | Message`  
- Add a few rows of test data.  
- In n8n, connect your **Google Sheets credentials** under the **"Get rows in sheet"** node.  
- Ensure the sheet name and range match your data.

---

### 3️⃣ Configure Workflow Nodes
Here’s how each node works in your workflow (based on the image):

1. **When Clicking “Execute Workflow”**  
   - Manual trigger to start the workflow anytime.

2. **Get Row(s) in Sheet**  
   - Reads all leads (up to 25 or more) from your Google Sheet.

3. **If Node**  
   - Checks for leads that have not been emailed yet (e.g., `Status = pending`).

4. **Loop Over Items**  
   - Iterates through each contact one by one to process and send emails.

5. **Get Row(s) in Sheet1**  
   - Re-fetches the specific row of the current lead for accuracy.

6. **Code Node**  
   - Prepares personalized message content (e.g., replaces `{{Name}}` or `{{Company}}` placeholders).

7. **Merge Node**  
   - Combines personalized message data with recipient details.

8. **Edit Fields Node**  
   - Fine-tunes subject and body formatting before sending.

9. **Send a Message (Gmail Node)**  
   - Sends the email using your Gmail credentials.  
   - You can set `To`, `Subject`, and `Body` fields dynamically from sheet data.

10. **Merge1 Node**  
    - Merges the sent email info with the original row data for tracking.

11. **Append or Update Row in Sheet**  
    - Updates your Google Sheet with the new status (e.g., “Sent”).

12. **Wait Node**  
    - Pauses briefly between each email (e.g., 10–15 seconds) to prevent spam blocking.  
    - Workflow then loops back to the next contact.

---

### 4️⃣ Test the Workflow
- Click **“Execute Workflow”** to run a test.  
- Check the logs and confirm that:
  - Emails are sent correctly.  
  - The Google Sheet updates the `Status` column for each contact.

---

### 5️⃣ Automate Daily Runs (Optional)
- Add a **Cron Node** at the beginning to schedule daily runs automatically (e.g., every morning at 9:00 AM).  
- You can safely scale this up to **500 emails/day** (by adjusting loops and delays).

---

## 🧩 Example Use Cases
- Freelance or startup cold outreach  
- Newsletter or campaign promotions  
- Event or product launch notifications  
- Personalized follow-up sequences  

---

## 🧠 Learning Outcome
This project helped me understand:
- How to design **multi-step no-code automations** in n8n  
- Integrating **Google Sheets + Gmail** APIs visually  
- Dynamic email personalization using **Code + Merge** nodes  
- Managing loops, conditions, and workflow control with **Wait** and **If** nodes  

---

## 👨‍💻 Author
**Anshuman Dutta**  
*VLSI Student | UI/UX Designer | No-Code & Automation Enthusiast | Agentic AI*  
 


---

## ⚠️ Notes
- Use this workflow responsibly.  
- Follow **CAN-SPAM** and **GDPR** regulations when sending bulk emails.  
- For higher limits, use SMTP or email API services like **SendGrid** or **Mailgun**.


