# AI Invoice Processing Agent

An Agentic AI-powered invoice processing workflow built with **n8n, Google Gemini, Gmail, Google Drive, and Google Sheets**.

The system automates invoice intake, document extraction, validation, duplicate detection, purchase-order matching, decision-making, logging, and email notifications while keeping human review in the loop for exceptions.

---

## 1. Project Overview

Manual invoice processing often requires employees to:

- Receive invoices through email
- Download invoice attachments
- Read and extract invoice information
- Validate invoice amounts
- Check purchase orders
- Detect duplicate invoices
- Decide whether an invoice can be processed
- Record the result
- Notify the responsible person when an exception occurs

These activities can be repetitive and may introduce data-entry errors, duplicate processing, mismatches, and processing delays.

This project demonstrates how **Agentic AI and workflow automation** can automate the invoice-processing pipeline while using deterministic business rules for important validation and decision-making.

---

## 2. Project Objective

The objective of this project is to build an automated invoice-processing agent that:

1. Receives invoice emails through Gmail.
2. Retrieves invoice attachments.
3. Stores the original invoice in Google Drive.
4. Extracts text from PDF invoices.
5. Uses Google Gemini to extract structured invoice information.
6. Validates the extracted invoice data.
7. Detects duplicate invoices.
8. Retrieves the corresponding Purchase Order (PO).
9. Validates vendor, amount, and currency.
10. Applies deterministic business rules.
11. Approves valid invoices.
12. Routes exceptions to human review.
13. Logs the processing result in Google Sheets.
14. Sends an automated email notification.

---

## 3. Why Agentic AI?

The workflow combines **AI-based document understanding** with **deterministic workflow automation**.

The AI component is responsible for understanding unstructured invoice text and converting it into structured information.

The deterministic n8n workflow is responsible for:

- Data validation
- Duplicate detection
- PO matching
- Vendor matching
- Amount matching
- Currency matching
- PO status checking
- Final decision-making
- Human escalation
- Logging
- Notifications

### Core Design Principle

> The LLM is responsible for extracting structured information from unstructured invoice documents, while deterministic n8n business rules are responsible for validation, PO matching, duplicate detection, and the final processing decision.

This approach improves transparency and reduces the risk of allowing the LLM to make uncontrolled business decisions.

---

## 4. System Architecture

```text
                    ┌──────────────────────┐
                    │      Gmail Inbox      │
                    │   Invoice PDF Email   │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │ Invoice Email Trigger│
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │ Retrieve Invoice Email│
                    └──────────┬───────────┘
                               │
                 ┌─────────────┴─────────────┐
                 │                           │
                 ▼                           ▼
       ┌──────────────────┐       ┌────────────────────┐
       │ Store Original   │       │ Extract Invoice    │
       │ Invoice          │       │ Text               │
       │ Google Drive     │       │ PDF Extraction     │
       └──────────────────┘       └─────────┬──────────┘
                                            │
                                            ▼
                                  ┌────────────────────┐
                                  │ AI Invoice Data    │
                                  │ Extraction         │
                                  │ Google Gemini      │
                                  └─────────┬──────────┘
                                            │
                                            ▼
                                  ┌────────────────────┐
                                  │ Invoice Data       │
                                  │ Validation         │
                                  └─────────┬──────────┘
                                            │
                                            ▼
                                  ┌────────────────────┐
                                  │ Duplicate Invoice  │
                                  │ Detection          │
                                  └─────────┬──────────┘
                                            │
                                            ▼
                                  ┌────────────────────┐
                                  │ Retrieve PO        │
                                  │ Details            │
                                  └─────────┬──────────┘
                                            │
                                            ▼
                                  ┌────────────────────┐
                                  │ PO & Vendor        │
                                  │ Validation         │
                                  └─────────┬──────────┘
                                            │
                                            ▼
                                  ┌────────────────────┐
                                  │ Invoice Decision   │
                                  │ Engine             │
                                  └─────────┬──────────┘
                                            │
                                            ▼
                                  ┌────────────────────┐
                                  │ Log Invoice Result │
                                  │ Google Sheets      │
                                  └─────────┬──────────┘
                                            │
                                            ▼
                                  ┌────────────────────┐
                                  │ Route Invoice      │
                                  │ Decision           │
                                  └───────┬────┬───────┘
                                          │    │
                              HUMAN REVIEW│    │APPROVED/
                              /EXCEPTION  │    │REJECTED
                                          ▼    ▼
                                ┌────────────┐ ┌─────────────────┐
                                │ Human      │ │ Processing      │
                                │ Review     │ │ Notification    │
                                │ Alert      │ │ Gmail           │
                                └────────────┘ └─────────────────┘
