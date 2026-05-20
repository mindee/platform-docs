---
description: >-
  Use our pre-trained Receipt model or adjust with the fields you need with
  Mindee V2.
icon: receipt
---

# Receipt

Here is a quick demo of Mindee V2's Receipt model:

{% @supademo/embed url="https://app.supademo.com/demo/cmiytadiq07vk14g4techyr3b" demoId="cmiytadiq07vk14g4techyr3b" %}

## Why Use Mindee for Receipts?

Receipts vary immensely in format, country, language, and quality. Mindee simplifies extraction and ensures high reliability by enabling you to:

* Handle global formats: Our model is trained on receipts from over 50 countries, automatically extracting data points regardless of local layout or language.
* Process poor quality inputs: Robustly extracts data from scanned documents, mobile photos, and even handwritten text on certain fields.
* Capture detailed line items: Accurately extract complex, nested data like individual line items, quantities, and prices for granular expense tracking.
* Get structured output with zero configuration: Start instantly with a pre-trained model that extracts standard fields like total amount, date, vendor name, and expense category.

## Two Ways to Start Using the Receipt Model

Mindee offers two paths to start extracting data from receipts:

### 1. Choose "Receipt" in the Catalog (Recommended)

* Click on "Create your document AI model" in your dashboard, then select **"Receipt".**
* The Receipt model template comes pre-configured with standard [#receipt-fields](receipt.md#receipt-fields "mention").
* Once your Invoice model is created, you can immediately [test](../../models/live-test.md) with your own invoices.
* Optionally, you can adjust the model's [Data Schema](../../extraction-models/data-schema.md) if you need to modify fields.

### **2. Customize the Model via Data Schema**

You can instantly tailor the pre-trained model to your exact needs. By navigating to the Data Schema interface, you can:

* Add new fields that are unique to your documents (e.g., internal identifiers, specific customer IDs).
* Delete existing fields that are not relevant to your use case.
* Refine the extraction by modifying field types or adding custom instructions for the AI assistant.

## Receipt Fields

{% include "../../.gitbook/includes/model-fields/receipt.md" %}
