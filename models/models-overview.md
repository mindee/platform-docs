---
description: >-
  Understand the core concepts of Mindee models, the different types available,
  and how to use them.
icon: print-magnifying-glass
---

# Models Overview

## What is a Model?

A **Model** in the Mindee platform is a configurable and reusable engine designed to process documents. In technical terms, a model is a set of parameters and complex prediction algorithms that perform an inference on files uploaded to Mindee.

Various types of models are available, from simple text recognition to data extraction and classification.

All models use Optical Character Recognition (OCR) to extract textual information. Most models also incorporate visual information to better understand the structure of the document. Both approaches are combined using sophisticated data processing techniques.

Models allow you to automate the process of turning unstructured document images into actionable, structured data. They can be tailored to different document types and business needs, ensuring that only the most relevant information is captured for your workflows.

Each Model contains a dedicated set of tools:

* Configuration: a model is defined by its configuration, that sets the way it should extract data from documents or analyze files. Configuration depends on the model type.
* Settings: overall settings of the model such as processing zone, storage policy, ownership transfer, etc.

## The Models Page

On the Models page, you can view, search, and manage all your models.

Each model is represented as a card showing its name, a preview (if available), and a summary of the main fields it extracts.

All models listed on the Models page are [testable](models-overview.md#live-test) and usable via API.

## Extraction Models

An **Extraction Model** in the Mindee platform is designed to extract structured data from documents.

Information to extract may be purely textual, purely visual, or a combination of both.

More information is available in the section: [Extraction Models](https://app.gitbook.com/s/u5bStlX8nv4b9z4GXB2S/extraction-models "mention")

## Utility Models

A **Utility Model** in the Mindee platform is designed to perform document analysis, or to preprocess documents in a data extraction workflow.

More information is available for each model type:

* [split.md](../split-models/split.md "mention") ⇒ find documents in a multi-page file
* [crop.md](../crop-models/crop.md "mention") ⇒ find documents on a single page
* [classification.md](../classification-models/classification.md "mention") ⇒ identify file contents
* [ocr.md](../raw-text-ocr-models/ocr.md "mention")⇒ structured text extraction

## Live Test

Once a model is created you can process documents directly on the platform. Use your own files or choose from our samples selection.

You can also view your document history.

This allows easily testing a model before integrating the API and going live to production.

For more information, consult:  [live-test.md](live-test.md "mention").

## Changing Settings

Settings control the high-level options of the model, such as storage duration and processing zone.

For more information on available options, consult:  [model-settings.md](model-settings.md "mention").

## Supported Document Texts

### Language

Mindee models can read any printed document in any writing system, and most handwriting.

**As a rule: all your documents will work** ... unless perhaps you are sending things like photos of cuneiform tablets or scans of 12th century music notation.

Fully supported languages include, but are **not limited** to:

* Western Europe: English, French, Spanish, German, Dutch, Italian, Portuguese, Danish, Swedish, Finnish, ...
* Eastern Europe: Polish, Ukrainian, Czech, Russian, Slovak, Greek, ...
* South Asia: Hindi, Bengali, Urdu, Punjabi, Tamil, Nepali, ...
* East Asia: Japanese, Mandarin Chinese (Simplified and Traditional), Cantonese, Korean, ...
* Southeast Asia: Vietnamese, Thai, Indonesian, Malay, Tagalog, ...
* Middle East: Arabic, Turkish, Farsi, Hebrew, Kurdish, ...
* Sub-Saharan Africa: Swahili, Amharic, Yoruba, Zulu, Lingala, Afrikaans, ...
* America: Guaraní, Quechua, Nahuatl, Aymara, Cree, Greenlandic, ...
* Constructed: Esperanto

### Handwriting

Mindee models are able to recognize (and OCR) any recent handwriting (19th century and on). Accuracy for handwriting is on average a bit less than printed text.
