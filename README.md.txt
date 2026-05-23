# Day 2 – Lead Validation Workflow with n8n

## Project Overview

This project is a Lead Validation Workflow built with n8n. The workflow receives incoming lead information through a webhook, validates the submitted data, and stores only valid entries in Google Sheets. Invalid submissions are rejected with an appropriate response message.

The goal of this workflow is to simulate a real-world lead intake system used by businesses to maintain clean and reliable customer data.

---

# Workflow Structure

```text
Webhook → Validate Lead Data → IF Node
                                      ├── Valid Data → Google Sheets → Success Response
                                      └── Invalid Data → Error Response
```

---

# What Was Built

This workflow was designed to:

* Receive lead data through a webhook endpoint
* Validate submitted information
* Check if required fields are correctly filled
* Separate valid and invalid submissions
* Store valid leads in Google Sheets
* Return success or error responses automatically

The workflow acts like a lightweight backend system for handling incoming customer or client leads.

---

# Nodes Used

## 1. Webhook Node

### Purpose

Acts as the entry point of the workflow.

### What It Does

* Receives incoming lead data via HTTP POST requests
* Accepts JSON payloads from forms, APIs, websites, or Postman
* Triggers the automation workflow

### Key Learning

Learned how webhooks function as API endpoints in automation systems.

---

## 2. Validate Lead Data Node

### Purpose

Validates incoming lead information before processing.

### What It Does

* Checks if required fields exist
* Validates email format
* Ensures submitted values are acceptable
* Prevents invalid or incomplete data from moving forward

### Key Learning

Understood the importance of data validation in preventing poor-quality records and broken automations.

---

## 3. IF Node

### Purpose

Introduces conditional logic into the workflow.

### What It Does

* Separates valid submissions from invalid submissions
* Routes data dynamically based on validation results

### Output Paths

* **TRUE Path:** Valid data continues to Google Sheets
* **FALSE Path:** Invalid data receives an error response

### Key Learning

Learned how automation workflows make decisions similarly to programming logic.

---

## 4. Append Row in Google Sheets Node

### Purpose

Stores validated lead information.

### What It Does

* Connects n8n to Google Sheets
* Automatically appends valid lead records
* Creates a structured lead database

### Key Learning

Learned how automation eliminates manual data entry and improves workflow efficiency.

---

## 5. Respond to Webhook Node (Success Response)

### Purpose

Returns a success message for valid submissions.

### What It Does

* Sends confirmation back to the sender
* Confirms that the lead was processed successfully

### Key Learning

Learned the importance of response handling in APIs and automation systems.

---

## 6. Respond to Webhook Node (Error Response)

### Purpose

Handles invalid submissions.

### What It Does

* Returns an error response when validation fails
* Explains why the submission was rejected

### Key Learning

Learned how workflows should properly manage failures and exceptions.

---

# Lessons Learned

Through this project, I learned:

* How workflow automation systems are structured
* How webhooks work as backend API endpoints
* The importance of validating incoming data
* How conditional logic works in automation
* How to connect n8n with Google Sheets
* How APIs send responses after processing requests
* How businesses automate lead management systems

This project also improved my understanding of:

* JSON data handling
* Backend workflow design
* Automation logic
* Data processing pipelines

---

# Use Cases

This workflow can be applied in several real-world scenarios, including:

## Lead Capture Systems

Automatically validate and store leads from websites and landing pages.

## CRM Data Cleaning

Prevent invalid or incomplete customer records from entering databases.

## Client Intake Forms

Validate client submissions before onboarding.

## Sales Automation

Filter and organize qualified leads for sales teams.

## Event Registration Systems

Ensure users submit accurate registration information.

## Business Process Automation

Reduce manual administrative work and improve efficiency.

---

# Technologies Used

* n8n
* Webhooks
* Google Sheets
* JSON
* HTTP Requests
* Conditional Logic

---

# Key Takeaway

This project introduced the core concepts of automation engineering:

* Receiving data
* Validating information
* Making logical decisions
* Storing records
* Returning responses

These are foundational concepts used in backend systems, workflow automation, AI integrations, and enterprise applications.
