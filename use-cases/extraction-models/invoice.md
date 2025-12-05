---
description: >-
  With Mindee, you can automatically parse invoices and extract structured
  financial data using the pre-trained Invoice model available in the Catalog.
icon: file-invoice-dollar
---

# Invoice

Watch our quick demo to see how you can easily set up your custom invoice model with Mindee:

{% @supademo/embed url="https://app.supademo.com/demo/cmfci0aiy7nt739ozcvdq9hqa" demoId="cmfci0aiy7nt739ozcvdq9hqa" %}

## Why use Mindee for Invoices?

Invoices can vary widely by supplier, format, and layout. The Invoice model is designed to handle these differences, so you get consistent and reliable data extraction without custom development.

Common use cases:

* Accounts payable automation
* Expense and cost tracking
* Tax and compliance reporting

## Two Ways to Start Building your Invoice Model

### 1. Choose “Invoice” in the Catalog (Recommended)

* Open the **Document Catalog** in your dashboard and select **“Invoice.”**
* The model comes pre-configured with the standard financial fields listed above.
* You can start using it right away, or adjust the schema in **Data Schema** if you need additional fields.
* Once selected, you can immediately test the model with your own invoices.

### 2. Build a Custom Invoice Model with the AI Agent

* If your workflow requires extra fields (e.g. purchase order number, IBAN, payment terms), you can describe them directly to the AI Agent.
* Optionally upload a sample invoice for context.
* The Agent will generate a tailored schema that extends beyond the built-in Invoice parser.

You can use this invoice sample if you want to try and do a live test yourself:

<figure><img src="../../.gitbook/assets/invoice-sample.jpg" alt="a fake invoice from Turnpike Designs" width="533"><figcaption></figcaption></figure>

## Document format support

The Invoice model accepts PDFs and common image formats (JPG, PNG). It works reliably with scanned, photographed, and digital invoices.

## Invoice Fields

{% include "../../.gitbook/includes/model-fields/invoice.md" %}
