---
description: >-
  With Mindee, you can instantly parse receipts and extract all the key details
  using the pre-trained Receipt model available in the Catalog.
noIndex: true
icon: receipt
---

# Receipt

## Why use Mindee for receipts?

Receipts come in all shapes and sizes: printed on paper, emailed as PDFs, or captured with a phone. They can vary by merchant, language, and format. The Receipt model is designed to handle these variations out of the box, removing the need for custom training.

Common use cases:

* Expense automation
* Business travel management
* Reimbursements and accounting workflows

***

## What can be extracted from receipts?

Here are some of the most common fields that our users need:

| Field             | Description                                      |
| ----------------- | ------------------------------------------------ |
| Invoice Number    | Reference number on the receipt                  |
| Date              | Transaction date                                 |
| Supplier Name     | Merchant or business issuing the receipt         |
| Customer Name     | Name of the customer (if present on the receipt) |
| Total (excl. VAT) | Subtotal amount before tax                       |
| VAT               | Value-added tax extracted from the document      |
| Total (incl. VAT) | Final total including tax                        |
| Due Date          | Payment due date (if specified)                  |
| Currency          | Currency used (e.g. EUR, USD)                    |

Keep in mind that this list not exhaustive: users can choose additional fields on the pre-trained model and add their own fields while reviewing the data schema.

## Two Ways to Start Building your Receipt Model

### 1. Choose “Receipt” in the Catalog (Recommended)

* Open the **Document Catalog** in your dashboard and select **“Receipt.”**
* The model comes preconfigured with the standard financial fields listed above.
* You can use it immediately, or refine the schema in **Data Schema** if you need additional information.
* Once added, you can test the model live with your own receipts.

### 2. Build a Custom Receipt Model with the AI Agent

* If your workflow requires non-standard fields (e.g. loyalty card number, tip amount, or store ID), you can describe them directly to the AI Agent.
* Optionally upload a sample receipt for clarity.
* The Agent will generate a tailored model that extends beyond the built-in Receipt parser.

## Document format support

The Receipt model accepts PDFs and common image formats (JPG, PNG). It works reliably with scanned, photographed, and digital receipts.

***
