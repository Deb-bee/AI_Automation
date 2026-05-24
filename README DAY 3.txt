Day 3 – Duplicate Detection Logic with Tag Addition (n8n)
Project Overview
This workflow focuses on preventing duplicate leads from entering a Google Sheet. Incoming lead data is first compared against existing records using a “Get row(s) in sheet” node. A JavaScript code node then applies duplicate detection logic, adds a “duplicate” or “new” tag accordingly, and routes the lead appropriately. Valid (non‑duplicate) leads are appended to the sheet and a success message is sent; duplicates are flagged and a different message is sent.

The goal is to maintain clean, unique lead databases – a critical requirement for CRM systems, email marketing, and sales automation.

Workflow Structure
text
Webhook → Get Row(s) in Sheet → JavaScript (Duplicate Detection + Add Tag) → IF / Switch Node
                                      ├── New Lead → Append to Sheet → Send Success Message → Execute Workflow (optional)
                                      └── Duplicate Lead → Send Duplicate Message → Execute Workflow (optional)
What Was Built
Receive lead data (e.g., email or phone) via webhook

Read existing rows from a Google Sheet to check for duplicates

Use JavaScript to compare incoming lead against existing records

Add a tag: “duplicate” or “new-lead”

Route the lead based on detection result

Append only new leads to the sheet

Send appropriate messages for each case

Execute subsequent workflow steps (e.g., logging, CRM sync)

This workflow simulates a production‑grade lead deduplication system.

Nodes Used
1. Webhook Node
Purpose
Receives the new lead data.

What It Does

Accepts JSON payloads containing lead fields (email, name, phone, etc.)

Triggers the automation for every incoming request

Passes data to the next node

Key Learning
Reinforced the role of webhooks as API endpoints for real‑time data ingestion.

2. Get Row(s) in Sheet Node
Purpose
Reads existing leads from Google Sheets to enable duplicate checking.

What It Does

Connects to a specified Google Sheet and worksheet

Retrieves all rows or filters by a key column (e.g., email)

Returns an array of existing records

May use “read: sheet” configuration as seen in the workflow

Key Learning
Learned how to query external data sources (Google Sheets) and use that data within a workflow – a fundamental pattern for data validation and enrichment.

3. Code in JavaScript Node
Purpose
Performs duplicate detection logic and adds a tag.

What It Does

Receives both the incoming lead (from webhook) and the existing rows (from Google Sheets)

Iterates through existing records to check for matches (e.g., same email or phone)

Sets a variable isDuplicate = true/false

Adds a property tag: isDuplicate ? “duplicate” : “new-lead”

Returns the enriched lead object for downstream nodes

Key Learning
Understood how to implement custom deduplication logic that can handle case‑insensitive comparisons, multiple key fields, or fuzzy matching – capabilities beyond standard nodes.

4. Conditional Routing (IF / Switch Node)
Purpose
Directs the workflow based on the duplicate detection result.

What It Does

Evaluates the isDuplicate flag or the tag value

TRUE path (New Lead) – proceeds to Google Sheets append node

FALSE path (Duplicate Lead) – proceeds to send duplicate message node

Can be implemented as an IF node or a Switch node with two branches

Key Learning
Learned how automation workflows make decisions, similar to if-else statements in programming.

5. Append Row in Google Sheets Node
Purpose
Stores only new, non‑duplicate leads.

What It Does

Maps incoming lead fields to sheet columns

Adds a new row at the bottom of the sheet

May also include the tag (“new-lead”) as an extra column

Prevents duplicate entries from being written

Key Learning
Reinforced the value of conditional writing – only valid/unique data reaches the database.

6. Send a Message Node (Two Instances)
Purpose
Notifies the appropriate channel about the outcome.

What It Does

New Lead message: “✅ New lead added: {name}”

Duplicate message: “⚠️ Duplicate lead detected: {email} – skipped”

Can send to chat apps (Slack, Telegram), email, or internal logs

Key Learning
Learned how to provide different feedback based on workflow decisions, improving observability and user experience.

7. Execute Workflow Node (Optional)
Purpose
Triggers another n8n workflow for further processing (e.g., CRM sync, welcome email).

What It Does

Calls a separate workflow with the lead data

Enables modular automation design

Waits for or ignores the child workflow’s response

Key Learning
Introduced the concept of workflow chaining and modular automation architecture.

Lessons Learned
Through this project, I learned:

How to detect duplicates by comparing incoming data with stored records

The importance of reading from a data source (Google Sheets) before writing

How to implement custom duplicate detection logic using JavaScript

The power of conditional routing (IF node) to create separate branches

How to tag leads based on validation results

Best practices for preventing data pollution in CRMs and databases

How to send contextual messages depending on workflow outcomes

The value of logging and clearing executions for debugging

This project also improved my understanding of:

Data integrity and idempotency in automation

Read‑before‑write patterns

Real‑time data validation

Building production‑ready lead management systems

Use Cases
This workflow can be applied in many real‑world scenarios:

CRM Lead Deduplication – Prevent duplicate contact records from sales forms.

Event Registration – Ensure each email registers only once.

Email Marketing – Avoid adding the same subscriber to multiple lists.

Support Ticket Systems – Detect duplicate issue submissions.

Inventory Management – Prevent duplicate SKU entries.

User Signup Flows – Check if an email already exists before creating an account.

Technologies Used
n8n (workflow automation)

Webhooks

Google Sheets (read & append operations)

JavaScript (custom logic)

Conditional branching (IF / Switch nodes)

JSON data handling

Workflow execution chaining

Key Takeaway
Day 3 introduces a critical data quality pattern: read before write. By checking existing records before inserting new ones, automation workflows can maintain clean, reliable datasets. This duplicate detection logic is a core component of any serious lead management system and demonstrates how low‑code tools can implement sophisticated validation rules that would otherwise require custom backend code
