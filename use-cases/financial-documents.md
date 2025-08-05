---
hidden: true
noIndex: true
icon: coins
---

# Financial documents

Mindee allows you to process a wide variety of financial documents using an AI agent that adapts to your specific needs. Whether you're working with invoices, bank statements, receipts, or account summaries, you can define exactly which fields you want to extract: no pre-training, templates, or fixed models required.

## Why Use Mindee for Financial Documents?

Financial documents come in all shapes and formats, with layouts that vary significantly across countries, industries, and even vendors. Mindee’s AI agent helps you:

* 🧠 Build custom extraction logic based on your documents
* ✍️ Prompt the agent with the fields you need (e.g. “Extract invoice number, total amount, and due date”)
* 📄 Upload example documents to help the agent learn your document structure
* ⚡ Skip complex rule-based templates or manual data entry

## Common Use Cases

You can use Mindee to extract structured data from:

* Invoices (supplier/customer name, totals, tax lines, due dates, etc.)
* Bank statements (account holder, IBAN, balances)
* Payment confirmations and receipts
* Account summaries or balance sheets
* Custom internal financial reports

### Example Fields You Can Extract

Depending on your document type, here are example fields our users often request:

| Document Type  | Possible Fields                                                                                                                |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Invoice        | Invoice number, date, supplier name, customer name, total (excl. VAT), VAT, total (incl. VAT), due date, currency              |
| Bank Statement | Account holder, IBAN, statement date/statement end date, opening/closing balance, transaction list (date, label, amount, type) |
| Receipt        | Merchant name, transaction date, payment method, item lines, subtotal, tax, total amount                                       |
| Balance Sheet  | Company name, statement date/statement end date, assets, liabilities, net equity                                               |

## Two Ways to Start

### 1. You Know the Fields You Want

* Prompt the agent with something like:\
  &#xNAN;_“Extract the invoice date, supplier name, total amount including VAT, and payment due date from these financial documents.”_
* Upload a sample PDF to guide the agent if needed
* Get your own custom document parser in seconds

### 2. You Don’t Know the Fields You Need Yet

* Upload a few sample documents to the Mindee app
* Ask the agent: _“What fields can you extract from this?”_
* Review the output and refine the prompt to match your use case

This path is ideal when you’re still exploring your data model or working with a new document type.

## Supported Formats

* 📄 **PDF files** — single-page or multi-page
* 🖼️ **Images** — JPG, PNG, TIFF, and more
