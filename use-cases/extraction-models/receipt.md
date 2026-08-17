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

## Building Your Receipt Model

### Choose "Receipt" in the Catalog

1. Click on "Create your document AI model" in your dashboard, then select **"Receipt".**
2. The Receipt model template comes pre-configured with standard [#receipt-fields](receipt.md#receipt-fields "mention").
3. Once your Invoice model is created, you can immediately [test](../../models/live-test.md) with your own invoices.

### Adjust Fields with the AI Agent (Optional)

If your workflow requires extra fields (i.e. internal identifiers, specific customer IDs), you can describe them directly to the AI Agent.

The Agent will guide you through adjusting the [Data Schema](../../extraction-models/data-schema.md) as required, and make the changes on your behalf.

You can also adjust the model directly.

### Several Receipts On a Single Image

In some cases several receipts are on the same image, for example when your users photograph all the receipts of the day on the hotel table. If you are receiving images with several receipts, use a [Crop model](../../crop-models/crop.md) and [chain](../../crop-models/extraction-model-chaining.md) it to your receipt model.

The image will first be cropped into separate documents, then each documents will have its data extracted in parallel. The return will include the data from all documents, meaning the processing is done within a single API call.

## Receipt Fields

{% include "../../.gitbook/includes/model-fields/receipt.md" %}
