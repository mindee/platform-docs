---
icon: file-lines
---

# Models

## What is a Model?

A **Model** in the Mindee platform is a configurable and reusable template designed to extract structured data from documents using Optical Character Recognition (OCR) and data extraction techniques. Each model defines a set of fields called a Document Schema —such as "Supplier Name," "Invoice Number," or "Total Amount" for an Invoice Model as an example— that the system will identify and extract from uploaded documents like invoices, receipts, or financial statements.

Models allow you to automate the process of turning unstructured document images into actionable, structured data. They can be tailored to different document types and business needs, ensuring that only the most relevant information is captured for your workflows.

On the Models page, you can view, search, and manage all your document extraction models. Each model is represented as a card showing its name, a preview (if available), and a summary of the main fields it extracts. This makes it easy to organize, access, and deploy models for your document processing tasks.

Each Model contains a certain set of tools/features :&#x20;

* a dedicated Data Schema: a model is also defined by a Data Schema, that sets the list of fields the API should extract for a given type of documents.
* a dedicated Continuous Learning (RAG) system: it allows the user to give additional instruction on some examples with unexpected behavior to durably improve the extraction performance of the model.
* a dedicated set of settings: it gives the capability to change meta settings of the model such as processing zone, storage policy, ownership transfer ...

## Creating from Scratch

When trying to create a new Model, you need to click on **"+ Create Model".**

A dialog box should open to give you the opportunity to explain your need. You should explain precisely the document you want to analyse, and discuss the fields that are needed for your analysis. The AI Agent will help you define quickly a first data schema that you'll be able to adjust.

Once a first good-enough data schema is proposed, we recommend to create the Model, and to modify it using the Data Schema page.

## Copying / Creating from Existing

If the document you're trying to automate is a pretty standard document, it is likely to be already managed by a Catalog API such as Invoice, Receipt, Financial Document, ID Card... \
\
Those APIs are pre-existing Data Schemas you can copy to immediately benefit from a well setup basis. You'll be able to modify it, but it can help win a bit of time.



## Modifying Your Data Schema

Once you have created or copied a [data-schema.md](data-schema.md "mention") you can refine it by making necessary modifications to better suit your needs. Navigate to the Data Schema page where you can adjust fields, update configurations, and customize settings according to your requirements.\
You can proceed manually or use the dialog box to do the modifications with the AI Agent. \
\
Examples of sentences to modify your data schema:&#x20;

* "Add a new document id field"
* "Rename the date field to invoice date"
* "Change the document type field to a classification field. The expected classes are INVOICE and RECEIPT"

## Configuration Options

All options are detailed in the [model-settings.md](model-settings.md "mention")page.
