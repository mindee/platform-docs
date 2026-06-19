---
description: Automatically extract the raw text from each page of a document using OCR.
icon: text
---

# Raw Text Model Overview

## Use Cases

When the entire text of a document needs to be extracted, along with position information for each word.

We use the term "OCR" literally, as the acronym for "Optical Character Recognition".

Meaning the exact text is returned as raw data, not parsed into structured data as fields.

{% hint style="info" %}
**Most users looking for a generic "Mindee OCR" or to "OCR a document" are likely looking for Extraction: c**onsult the [Extraction model documentation](https://app.gitbook.com/s/u5bStlX8nv4b9z4GXB2S/extraction-models).
{% endhint %}

A file sent to the Raw Text OCR Model may have any number of pages, [within limits](../integrations/technical-limitations.md#file-limits).

### Difference Between Raw Text _Model_ and Raw Text _Option_

The [Extraction model](https://app.gitbook.com/s/u5bStlX8nv4b9z4GXB2S/extraction-models) has the [Raw Text optional feature](../extraction-models/optional-features/raw-text-full-ocr.md) that can be used in similar uses cases, depending on your needs.

**Raw Text option:** returns the entire text for each page as a single string.

**Raw Text model:** in addition to the single string per page, also returns each word on the page. Each word has position information and text content.

### Language Support

Almost all languages are fully supported, since only the writing system is involved in detection.

In other words, as long as the system can recognize the glyphs (letters in an alphabet), the text will be extracted.

It's much easier and shorter to list what is **not** supported:

* Ancient languages with no equivalent modern writing system such as cuneiform, Egyptian hieroglyphs, ancient Maya, etc.
* Modern languages with uncommon writing systems such as Blackfoot, Cherokee, Inuktitut, etc.

## Create a Raw Text OCR Model

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
