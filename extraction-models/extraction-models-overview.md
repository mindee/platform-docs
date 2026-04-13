---
icon: print-magnifying-glass
---

# Extraction Models Overview

## What is an Extraction Model?

An **Extraction Model** in the Mindee platform is a type of [model](../models/models-overview.md) designed to extract structured data from documents using Optical Character Recognition (OCR) combined with data extraction techniques.&#x20;

Each model defines a set of fields called a [data-schema.md](data-schema.md "mention"). Fields could include "Supplier Name," "Invoice Number," or "Total Amount" for an Invoice Model, as an example. The system will then identify and extract data from uploaded files according to these field definitions.

You can create extraction models for any type of document including: invoices, receipts, passports,  ID cards, financial statements, etc.

Models allow you to automate the process of turning unstructured document images into actionable, structured data. They can be tailored to different document types and business needs, ensuring that only relevant information is captured for your workflows.

Each Extraction Model contains these dedicated tools and features:

* [data-schema.md](data-schema.md "mention"): a model is also defined by a Data Schema, that sets the list of fields the API should extract for a given type of documents.
* [improving-accuracy.md](optional-features/improving-accuracy.md "mention"): it allows the user to give additional instruction on some examples with unexpected behavior to durably improve the extraction performance of the model.
* [model-settings.md](../models/model-settings.md "mention"): overall settings of the model such as processing zone, storage policy, ownership transfer, etc.

## Create an Extraction Model <a href="#creating-from-scratch" id="creating-from-scratch"></a>

From the Mindee Platform main page, click on **"Create your document AI model".**

### Create from Model Catalog

Chances are the document you're trying to automate is a known type of document, and likely to be already present in our Model Catalog: Invoice, Receipt, Passport, Financial Document, ID Card...

Simply click on the Model that best fits your needs. You can search our catalog for suitable models.\
\
These Models use Data Schemas created by our Data Science team, allowing you to get started quickly by using a set of predefined fields.

{% hint style="info" %}
**Catalog Models come with generic fields.**

You'll likely need to add and/or modify fields to fit your needs and business case.
{% endhint %}

### Create a Custom Model <a href="#creating-from-scratch" id="creating-from-scratch"></a>

If none of the catalog models fit your needs, you can start from scratch.\
When creating a new Model, click on **"Custom document".**

A dialog box will give you the opportunity to explain your need. You should explain precisely the document you want to process, and discuss the fields to be extracted. Our AI Agent will help you quickly define an initial data schema that you'll be able to adjust later.

{% hint style="info" icon="lightbulb" %}
**We recommend creating an initial model quickly.**

Once created, refine the new model's [data-schema.md](data-schema.md "mention") on the platform, using the [live-test.md](../models/live-test.md "mention") feature to fine-tune your fields and guidelines.
{% endhint %}

## Modifying Your Extraction Data Schema

Once you have created or copied a model, you'll likely want to modify its [data-schema.md](data-schema.md "mention") to better suit your needs.

Navigate to the Data Schema page where you can adjust fields, update configurations, and customize settings according to your requirements.

### AI Assistant

You can use the "AI Assistant" dialog box for automated improvements.

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
