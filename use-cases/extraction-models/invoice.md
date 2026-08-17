---
description: >-
  Automatically parse invoices and extract structured financial data using the
  Invoice template available in the model Catalog.
icon: file-invoice-dollar
---

# Invoice

Watch our quick demo to see how you can easily create your custom invoice model with Mindee:

{% @supademo/embed url="https://app.supademo.com/demo/cmfci0aiy7nt739ozcvdq9hqa" demoId="cmfci0aiy7nt739ozcvdq9hqa" %}

## Why use Mindee for Invoices?

Invoices can vary widely by supplier, format, and layout. The Invoice model template is designed to handle these differences, so you get consistent and reliable data extraction without custom development.

Common use cases:

* Accounts payable automation
* Expense and cost tracking
* Tax and compliance reporting

## Building your Invoice Model

### Choose "Invoice" in the Catalog

1. Click on "Create your document AI model" in your dashboard, then select **"Invoice".**
2. The Invoice model template comes pre-configured with the standard [#invoice-fields](invoice.md#invoice-fields "mention").
3. Once your Invoice model is created, you can immediately [test](../../models/live-test.md) with your own invoices.

### Adjust Fields with the AI Agent (Optional)

If your workflow requires extra fields (i.e. IBAN, payment terms), you can describe them directly to the AI Agent.

The Agent will guide you through adjusting the [Data Schema](../../extraction-models/data-schema.md) as required, and make the changes on your behalf.

You can also adjust the model directly.

### Several Invoices Within a Single File

If you are receiving multi-page PDFs with several invoices, use a [Split model](https://app.gitbook.com/s/u5bStlX8nv4b9z4GXB2S/split-models) and [chain](../../split-models/extraction-model-chaining.md) it to your invoice model.

The file will first be split into separate documents, then each document will have its data extracted in parallel. The return will include the data from all documents, meaning the processing is done within a single API call.

## Supported Document  Formats

The Invoice model accepts [PDFs](../../integrations/technical-limitations.md#pdf-files) and common [image formats](../../integrations/technical-limitations.md#image-files) (JPG, PNG).

It works reliably with scanned, photographed, and digital invoices. Like all Mindee catalog models, handwriting can be recognized in addition to printed text.

## Invoice Fields

{% include "../../.gitbook/includes/model-fields/invoice.md" %}
