---
description: Automatically extract the raw text from each page of a document using OCR.
icon: text
---

# Raw OCR Model Overview

## Use Cases

When the entire text of a document needs to be extracted, along with position information for each word.

{% hint style="info" %}
**We use the term "OCR" literally, as the acronym for "Optical Character Recognition".**

Meaning the exact text is returned as raw data, not parsed into structured data as fields.

Most users looking to "OCR a document" are probably looking for the [Extraction model](https://app.gitbook.com/s/u5bStlX8nv4b9z4GXB2S/extraction-models).
{% endhint %}

A file sent to the Raw OCR Model may have any number of pages, [within limits](../integrations/technical-limitations.md#file-limits).

## Create a Raw OCR Model

Raw OCR models are always custom, there are no templates available in the Catalog.

Each OCR model gets its own unique model ID when you create it.

1. To create a OCR model, click on **Models**, and then click on **Create your document AI model**.
2. Scroll to the **Document Utilities** section, click on **OCR.**\
   This step will also generate the model's unique ID.
3. You can now use the **Live Test** tab to process documents.<br>

Your OCR model is now available in your **Models** tab:

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

Here is a step-by-step tutorial that shows you how to properly create an OCR utility:

{% @supademo/embed url="https://app.supademo.com/demo/cmlrrputf0pnh1189ay3tsdkt" demoId="cmlrrputf0pnh1189ay3tsdkt" %}

## Integration

Once your OCR model is created and tested, integration documentation is provided in the "Documentation" page, or here: [ocr-quick-start.md](sdk-integration/ocr-quick-start.md "mention")
