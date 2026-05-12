---
description: >-
  Understand the core concepts of Mindee models, the different types available,
  and how to use them.
icon: print-magnifying-glass
---

# Models Overview

## What is a Model?

A **Model** in the Mindee platform is a configurable and reusable template designed to process documents. In technical terms, a model performs an inference on files uploaded to Mindee.

Various types of models are available, from simple text recognition to data extraction and classification. Models use Optical Character Recognition (OCR) combined with sophisticated data processing techniques.

Models allow you to automate the process of turning unstructured document images into actionable, structured data. They can be tailored to different document types and business needs, ensuring that only the most relevant information is captured for your workflows.

On the Models page, you can view, search, and manage all your document extraction models. Each model is represented as a card showing its name, a preview (if available), and a summary of the main fields it extracts. This makes it easy to organize, access, and deploy models for your document processing tasks.

Each Model contains a dedicated set of tools:

* Configuration: a model is defined by its configuration, that sets the way it should extract data from documents or analyze files. Configuration depends on the model type.
* Settings: overall settings of the model such as processing zone, storage policy, ownership transfer, etc.

## Extraction Models

An **Extraction Model** in the Mindee platform is designed to extract structured data from documents using Optical Character Recognition (OCR) combined with data extraction techniques.

More information is available in the section: [Broken link](/broken/pages/ywb5XsDuWyBy07coiRb0 "mention")

## Utility Models

A **Utility Model** in the Mindee platform is designed to perform document analysis, or to preprocess documents in a data extraction workflow.

More information is available for each model type:

* [split.md](../split-models/split.md "mention") ⇒ find documents in a multi-page file
* [crop.md](../crop-models/crop.md "mention") ⇒ find documents on a single page
* [classification.md](../classification-models/classification.md "mention") ⇒ identify file contents&#x20;
* [ocr.md](../ocr-models/ocr.md "mention")⇒ structured text extraction

## Live Test

Once a model is created you can process documents directly on the platform. Use your own files or choose from our samples selection.

You can also view your document history.

This allows easily testing a model before integrating the API and going live to production.

More details in the [live-test.md](live-test.md "mention") section.

## Changing Settings

Settings control the high-level options of the model, such as storage duration and processing zone.

All options are detailed in the [model-settings.md](model-settings.md "mention") section.
