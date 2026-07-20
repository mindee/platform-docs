---
description: >-
  Extraction models enable structured data extraction based on fields, which can
  be configured for any document type.
icon: print-magnifying-glass
---

# Extraction Model Overview

## What is an Extraction Model?

An **Extraction Model** in the Mindee platform is a type of [model](../models/models-overview.md) designed to extract structured data from documents using Optical Character Recognition (OCR) combined with advanced data extraction techniques.

Each model defines a set of fields called a [data-schema.md](data-schema.md "mention"). Fields could include "Supplier Name," "Invoice Number," or "Total Amount" for an Invoice Model, as an example. The system will then identify and extract data from uploaded files according to these field definitions.

You can create extraction models for any type of document including: invoices, receipts, passports, ID cards, financial statements, etc.

Models allow you to automate the process of turning unstructured document images into actionable, structured data. They can be tailored to different document types and business needs, ensuring that only relevant information is captured for your workflows.

Each Extraction Model contains these dedicated tools and features:

* [data-schema.md](data-schema.md "mention"): a model is also defined by a Data Schema, that sets the list of fields the API should extract for a given type of documents.
* [improving-accuracy.md](optional-features/improving-accuracy.md "mention"): it allows the user to give additional instruction on some examples with unexpected behavior to durably improve the extraction performance of the model.
* [model-settings.md](../models/model-settings.md "mention"): overall settings of the model such as processing zone, storage policy, ownership transfer, etc.

## Create an Extraction Model <a href="#creating-from-scratch" id="creating-from-scratch"></a>

From the Mindee Platform main page, click on **"Create your document AI model"**.

### Create From the Model Catalog

Chances are the document you're trying to automate is a known type of document, and likely to be already present in our Model Catalog: Invoice, Receipt, Passport, Financial Document, ID Card...\
\
These are model templates with Data Schemas created by our Data Science team, allowing you to get started quickly by using a set of predefined fields.

You can search our catalog for suitable templates, then simply click on the one that best fits your needs. This will create a new model in your organization's account with its own model ID, allowing you to use and modify it.

{% hint style="info" %}
**Catalog Models come with generic extraction fields.**

You'll likely need to add and/or modify fields to fit your needs and business case.
{% endhint %}

### Create a Custom Model <a href="#creating-from-scratch" id="creating-from-scratch"></a>

If none of the catalog models fit your needs, you can start from scratch.\
When creating a new Model, click on **"Custom document"**.

Next, choose how to create the custom model:

* Describe as precisely as possible the document(s) the model will process.\
  Best when documents processed show variance.
* Uploading a sample file representative of documents to process.\
  Best when documents processed are similar.

Our AI Agent will help you to quickly define an initial data schema that you'll be able to adjust later.

This step will also generate the model's unique ID.

{% hint style="info" icon="lightbulb" %}
**We recommend creating an initial model quickly.**

Once created, refine the new model's [data-schema.md](data-schema.md "mention") on the platform, using the [live-test.md](../models/live-test.md "mention") feature to fine-tune your fields and guidelines.
{% endhint %}

## Modifying Your Extraction Data Schema

Once you have created a model, you'll likely want to modify its [Data Schema](data-schema.md) to better suit your needs.

Even if the model was created from a model template in the Catalog, it is unique to your account and fully customizable.

Navigate to the Data Schema page where you can adjust fields, update configurations, and customize settings according to your requirements.

### Using the AI Assistant

The Mindee AI Assistant is a powerful tool that can help you get the most of your model. It is the preferred method of modifying the Data Schema.

The Assistant is available in a dialog box in the model's Data Schema page.

Be as accurate as possible with field names, exact names and values should be in quotation marks.\
\
Example sentences to modify your data schema with the AI Assistant:

* _Add a new field: "document id"_\
  ⇒ Will create a new text field.
* _Add a new field: "is past due"_\
  ⇒ Will create a new boolean field\
  Hint: boolean field names should start with "is" or "has".
* _Rename the "date" field to "invoice date"_
* _Change the "document\_type" field to a classification field. The expected classes are "INVOICE" and "RECEIPT"_

## Optimizing Model Results

In order to optimize the accuracy of a given model, the first step is to [fine-tune the Data Schema](data-schema-best-practices.md).

In particular, start by asking the Mindee AI Assistant to [automatically optimize](data-schema-best-practices.md#automated-optimization) your Data Schema.

If you started from a template in the catalog, it is usually necessary to adapt it to your specific documents and use case.

After this step, if there are still some lingering issues or unexpected behavior, there are further refinements available.

### Problems With Specific Templates

When the overall accuracy is good, but there are problems on specific document templates.

For this you'll want to activate [improving-accuracy.md](optional-features/improving-accuracy.md "mention"). This allows adding guidance to specific templates, meaning you can target problem documents while leaving others unaffected.

### High Accuracy Required

When you need very high precision for all the documents that you process.

Consider enabling [automation-confidence-score.md](optional-features/automation-confidence-score.md "mention"). This uses multiple models for higher accuracy **and** flags problematic fields.

Flagged fields can be sent for [human review](extraction-models-overview.md#end-user-review) or the document can be rejected entirely, based on business rules defined on your side.

### End User Review

When you are displaying the documents to end users, typically when they can review and correct the extracted data.

You can enable [polygons-bounding-boxes.md](optional-features/polygons-bounding-boxes.md "mention") so that the location of the extracted fields can be shown (this is always activated in the [live-test.md](../models/live-test.md "mention")). In this way, it will be much easier for your users to find erroneous fields correct them.

This is even more powerful when combined with [confidence scores](optional-features/automation-confidence-score.md), you can flag fields needing attention directly in your forms.

### Combined Benefits

These features work together to create a system that becomes more accurate as you use it, reducing manual corrections and improving automation success rates.
