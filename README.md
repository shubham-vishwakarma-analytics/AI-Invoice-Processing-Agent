# AI Invoice Processing Agent

> An Agentic AI-powered invoice processing workflow that automates invoice intake, AI-based data extraction, validation, duplicate detection, Purchase Order matching, decision-making, logging, and exception handling using n8n, Google Gemini and Google Workspace.

---

## 📌 Project Overview

The **AI Invoice Processing Agent** is an Agentic AI-based business process automation project developed as part of the **ALabs Internship — Project 3: Building AI Agents for Business Process Automation**.

The system automates the invoice processing lifecycle from receiving an invoice through Gmail to generating a final processing decision.

The workflow combines:

- Workflow automation
- Large Language Model (LLM)-based information extraction
- Deterministic business rules
- Google Workspace integrations
- Human-in-the-Loop exception handling

The LLM is responsible for extracting structured information from unstructured invoice documents, while deterministic business rules control validation, Purchase Order matching, duplicate detection, and the final processing decision.

---

## 🎯 Project Objective

The primary objective is to build an automated invoice processing workflow that:

- Receives invoice PDFs through Gmail
- Extracts structured invoice information using Google Gemini
- Validates invoice data
- Detects duplicate invoices
- Matches invoices with Purchase Orders
- Validates vendor, amount and currency information
- Applies deterministic business rules
- Generates an invoice processing decision
- Logs processing results
- Stores original invoice documents
- Sends automated notifications
- Routes exceptions to human reviewers

---

## 🏢 Business Problem

Invoice processing can involve several repetitive manual activities:

1. Receiving invoices through email
2. Opening invoice documents
3. Reading invoice information
4. Manually extracting data
5. Validating invoice amounts
6. Checking Purchase Orders
7. Detecting duplicate invoices
8. Approving or reviewing invoices
9. Maintaining processing records
10. Notifying stakeholders

### Key Challenges

- Manual data-entry effort
- Extraction and validation errors
- Duplicate invoice processing
- Invoice and PO mismatches
- Delayed exception handling
- Lack of centralized processing records

The project addresses these challenges by automating repetitive processing steps while keeping deterministic controls and human review for exceptions.

---

## 🤖 Why Agentic AI?

The workflow follows an agent-like process:

```text
Trigger
   ↓
Understand
   ↓
Extract Information
   ↓
Retrieve Business Data
   ↓
Validate
   ↓
Apply Rules
   ↓
Decide
   ↓
Act
   ↓
Escalate When Required
