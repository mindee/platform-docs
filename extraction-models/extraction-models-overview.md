---
icon: print-magnifying-glass
---

# Extraction Models Overview

## What is an Extraction Model?

An **Extraction Model** in the Mindee platform is a type of [model](../models/models-overview.md) designed to extract structured data from documents using Optical Character Recognition (OCR) and data extraction techniques.&#x20;

Each model defines a set of fields called a [data-schema.md](data-schema.md "mention"). Fields could include "Supplier Name," "Invoice Number," or "Total Amount" for an Invoice Model, as an example. The system will then identify and extract data from uploaded files according to these field definitions.

You can create extraction models for any type of document including: invoices, receipts, passports,  ID cards, financial statements, etc.

Models allow you to automate the process of turning unstructured document images into actionable, structured data. They can be tailored to different document types and business needs, ensuring that only the most relevant information is captured for your workflows.

Each Extraction Model contains these tools and features:

* a dedicated Data Schema: a model is also defined by a Data Schema, that sets the list of fields the API should extract for a given type of documents.
* a dedicated Continuous Learning (RAG) system: it allows the user to give additional instruction on some examples with unexpected behavior to durably improve the extraction performance of the model.
* a dedicated set of settings: it gives the capability to change meta settings of the model such as processing zone, storage policy, ownership transfer ...

## Create an Extraction Model <a href="#creating-from-scratch" id="creating-from-scratch"></a>

From the Mindee Platform main page, click on **"Create your document AI model".**

### Create from Model Catalog

Simply click on the Model that best fits your needs. You can search our catalog for suitable models.

Chances are the document you're trying to automate is a known type of document, and likely to be already present in our Model Catalog: Invoice, Receipt, Passport, Financial Document, ID Card...\
\
These Models use Data Schemas created by our Data Science team, allowing you to immediately benefit from a well-tested and validated set of fields.

{% hint style="info" %}
Catalog Models come with **generic**, worldwide fields.

You'll likely need to add and/or modify fields to fit your needs and business case.
{% endhint %}

### Create a Custom Model <a href="#creating-from-scratch" id="creating-from-scratch"></a>

If none of the catalog models fit your needs, you can start from scratch.\
When creating a new Model, click on **"Custom document".**

A dialog box will give you the opportunity to explain your need. You should explain precisely the document you want to analyze, and discuss the fields that are needed for your analysis. The AI Agent will help you define quickly a first data schema that you'll be able to adjust.

Once a first good-enough data schema is proposed, we recommend to create the Model, and to modify it using the [data-schema.md](data-schema.md "mention") page on the platform.

## Modifying Your Extraction Data Schema

Once you have created or copied a model, you can refine its [data-schema.md](data-schema.md "mention") by making modifications to better suit your needs.

Navigate to the Data Schema page where you can adjust fields, update configurations, and customize settings according to your requirements. You can proceed manually or use the dialog box to do the modifications with the AI Agent.

Be as accurate as possible with field names, exact names and values should be in quotation marks.\
\
Examples of sentences to modify your data schema:

* Add a new field: "document\_id"
* Rename the "date" field to "invoice\_date"
* Change the "document\_type" field to a classification field. The expected classes are "INVOICE" and "RECEIPT"
