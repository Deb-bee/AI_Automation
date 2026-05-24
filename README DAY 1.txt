Day 1 – Lead Capture Test with Tag Addition (n8n)
Project Overview
This workflow introduces the foundational concept of capturing lead data via a webhook, testing the lead capture mechanism, and adding a custom tag to each incoming lead. The workflow is designed to simulate a basic lead intake system where tags help categorize or prioritize leads for further processing. It includes a JavaScript code node to dynamically add tags and conditional messaging to confirm receipt.

The goal is to understand how to trigger automations from external sources, manipulate lead data programmatically, and provide immediate feedback to the sender.

Workflow Structure
text
Webhook → JavaScript (Add Tag) → Send Message (Optional) → Respond to Webhook
What Was Built
Receive lead information through a webhook endpoint

Execute custom JavaScript to add a tag (e.g., “new-lead”, “test-capture”)

Optionally send a message (true/false based on condition or configuration)

Respond to the webhook with a success or failure status

Log execution results for debugging

This workflow acts as a lightweight lead capture test that can be extended with tagging strategies.

Nodes Used
1. Webhook Node
Purpose
Acts as the entry point for external lead data.

What It Does

Listens for HTTP POST requests containing lead information (e.g., name, email, source)

Triggers the workflow automatically when data is received

Passes the incoming payload to subsequent nodes

Key Learning
Learned how webhooks enable real‑time automation by receiving data from forms, CRMs, or custom applications.

2. Code in JavaScript Node
Purpose
Adds a custom tag to the lead data dynamically.

What It Does

Reads the incoming lead object from the webhook

Adds a new property (e.g., tag: “test-lead”) or appends to an existing tags array

Can implement conditional logic for different tag values based on lead attributes

Returns the enriched lead object for the next steps

Key Learning
Understood how low‑code automation tools allow custom JavaScript to extend functionality when native nodes are insufficient.

3. Send a Message Node
Purpose
Optionally sends an internal notification or message (e.g., to a chat, email, or log).

What It Does

Configured with true / false execution conditions

If enabled, sends a confirmation or alert message (e.g., “New lead captured with tag X”)

Demonstrates conditional branching in workflows

Key Learning
Learned how to control whether certain actions execute based on previous node outputs or manual settings.

4. Respond to Webhook Node
Purpose
Returns a synchronous response to the original webhook caller.

What It Does

Sends a JSON response (e.g., { "status": "success", "message": "Lead captured and tagged" })

Confirms that the workflow completed successfully

Handles errors by returning appropriate error codes and messages

Key Learning
Recognized the importance of providing immediate feedback to API callers in automation systems.

Lessons Learned
Through this project, I learned:

How to set up a webhook trigger in n8n

The role of JavaScript nodes in manipulating and enriching data

How to add custom tags to leads for better organization and routing

The concept of conditional execution (send message true/false)

How to respond synchronously to webhook requests

Basic debugging using execution logs

How simple automation workflows can replace manual lead entry

This project also improved my understanding of:

HTTP request/response cycles

Data transformation between nodes

Event‑driven automation design

Use Cases
This workflow can be applied in various scenarios, including:

Lead Capture Testing – Verify that lead submission forms are correctly sending data.

Tagging for Segmentation – Automatically label leads by source (e.g., “website”, “ad”, “referral”).

Internal Notifications – Alert a team channel when a new test lead arrives.

Onboarding Pipelines – Add a “needs-review” tag for manual follow‑up.

API Mocking – Simulate a lead capture endpoint during development.

Technologies Used
n8n (workflow automation)

Webhooks (HTTP triggers)

JavaScript (custom code node)

JSON data format

Conditional execution logic

Key Takeaway
Day 1 establishes the foundation of automation engineering: receiving external data, transforming it with code, controlling execution flow, and returning meaningful responses. These building blocks are reused in every subsequent automation, from simple lead capture to complex AI‑powered systems.
