Here's a GitHub project description based on your workflow details.

---

### n8n Workflow: Automated Email Scheduler with Google Sheets

This project contains an n8n workflow that automates sending scheduled emails. It uses a **Google Sheet** as a database and control panel to manage email content, recipients, and send dates, and sends the emails via **Gmail**.

It's a "set-it-and-forget-it" solution for drip campaigns, event reminders, or any scheduled communication. 📧

---
## Features

* **Dynamic Scheduling**: Manage your entire email schedule from a simple Google Sheet.
* **Automated Daily Sending**: The workflow runs automatically to check for and send any emails scheduled for the current day.
* **Status Tracking**: Automatically updates a "status" column in the sheet after an email is sent to prevent duplicates.
* **Easy to Manage**: No code changes are needed to add, edit, or remove emails. Just update the spreadsheet.

---
## How It Works

The workflow follows a simple, logical sequence:

1.  **Fetch Data**: Retrieves all message data from the specified Google Sheet.
2.  **Filter by Status**: Isolates only the rows with a status like `"Waiting for sending"`.
3.  **Filter by Date**: From the pending messages, it selects only those scheduled for the current date.
4.  **Send Email**: Uses the Gmail node to send the email, populating the recipient, subject, and body from the spreadsheet data.
5.  **Update Status**: After a successful send, it updates the message's status in the Google Sheet to `"Sent"`.

---
## Setup & Usage

To use this workflow, you will need:
* An active n8n instance.
* Credentials for Google Sheets and Gmail configured in n8n.

1.  **Prepare your Google Sheet**: Create a sheet with the following columns: `Email`, `Name`, `Subject`, `Content`, `Date`, and `Status`. The `Date` column should use a `YYYY/MM/DD` format.
2.  **Import Workflow**: Download the `.json` file from this repository and import it into your n8n canvas.
3.  **Configure Nodes**:
    * Update the **Retrieve Customer Messages** and **Update Message Status** nodes to point to your Google Sheet and select the correct columns.
    * Configure the **Gmail** node with your credentials.
4.  **Activate**: Set the workflow to **Active** and schedule it to run once daily.
