---
description: >-
  Considerations affecting response times such as document structure, schema
  complexity, and enabled features.
icon: watch
---

# Response Times

Response time will vary depending on the source document, the Data Schema, and the optional features enabled.

## Impact of the Source File

Properties of the source document which impact response time:

* file size, especially for image files
* number of pages
* density of text

### Optimize Sources

Remove any pages that are not strictly needed for the data to be extracted, in particular, any pages with dense text. For example, remove the last two pages of invoices containing terms and conditions.

We offer free tooling for removing pages from PDFs before sending them.\
Take a look at the [#manipulate-pdf-pages](client-libraries-sdk/load-and-adjust-a-file.md#manipulate-pdf-pages "mention") section.

Some general tips for improving file uploads can be found in the [#guidelines-for-uploading-files](technical-guidelines.md#guidelines-for-uploading-files "mention") section.

## Impact of the Data Schema

Properties of the Data Schema which impact response time:

* number of fields
* complexity of guidelines
* lists of nested objects

In particular, lists of nested objects with many corresponding matches in the source document. For example: a multi-page invoice with many products purchased, and each product having multiple fields returned in the response.

### Optimize the Data Schema

Remove any fields that are not required.

If you find yourself adding extra fields or long-winded guidelines to handle different document templates, consider making several models instead. You can then route your documents to a more focused model, simultaneously improving response time and accuracy.

Also take a look at the [data-schema-best-practices.md](../extraction-models/data-schema-best-practices.md "mention") section for more tips on optimizing your models.

## Impact of Processing Options

Optional features which impact response time:

* [automation-confidence-score.md](../extraction-models/optional-features/automation-confidence-score.md "mention")\
  Several models are called in parallel, results are then analyzed and combined.
* [improving-accuracy.md](../extraction-models/optional-features/improving-accuracy.md "mention")\
  Before performing the inference, the RAG database must be searched.
* [polygons-bounding-boxes.md](../extraction-models/optional-features/polygons-bounding-boxes.md "mention")\
  Additional information must be extracted from the document, then polygons must be calculated.

For best results, only activate features you actually need.

## Examples

Common combinations of document types and models and their impact on response times.

### Faster

Both the source document and the Data Schema are lightweight.

Typically, single page documents with few fields:

* ID documents: passports, driver licenses, etc.
* Healthcare cards
* Tickets, boarding passes
* Envelopes, packages
* Simple single-page forms

### Average

Either the source document or the Data Schema is lightweight.

Single page documents with nested objects.\
— or —\
Multiple page documents with **no** nested objects.

Examples:

* Most receipts
* Single page invoices
* Most bills of lading
* Single-page government forms
* Most résumés, CVs

### Slower

Neither the source document nor the Data Schema are lightweight.

Multiple page documents with nested objects and small text:

* Very long receipts with many items and small text (i.e. long list of groceries for the week)
* Invoices with more than 10 pages, each page having many items
* Monthly bank statements, especially when over 10 pages
* Complex, multi-page government forms

Whenever possible, [remove any unnecessary pages](client-libraries-sdk/load-and-adjust-a-file.md#manipulate-pdf-pages) before uploading the document.
