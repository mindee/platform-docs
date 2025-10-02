---
icon: watch
---

# Response Times

Response time will vary depending on the source document, the Data Schema, and the options selected.

Unfortunately, there is no free lunch.

## Source Document

Properties of the source document which impact response time:

* file size, especially for images files
* number of pages
* density of text

Take a look at the [#guidelines-for-uploading-files](technical-guidelines.md#guidelines-for-uploading-files "mention") section for ways to improve source files.

## Data Schema

Properties of the Data Schema which impact response time:

* number of fields
* complexity of guidelines

Additionally, lists of nested objects in the Data Schema and many corresponding items in the source document. For example: a multi-page invoice with many products purchased, and each product having multiple fields returned in the response.

## Processing Options

Processing options which impact response time:

* [improving-accuracy.md](../models/optional-features/improving-accuracy.md "mention")\
  Before performing the inference, the RAG database must be searched.
* [automation-confidence-score.md](../models/optional-features/automation-confidence-score.md "mention")\
  Several models are called in parallel, results are then analyzed and combined.
* [polygons-bounding-boxes.md](../models/optional-features/polygons-bounding-boxes.md "mention")\
  Additional information must be extracted from the document, then polygons must be calculated.

## Examples

Common combinations of document types and models.

### Fast

Single page with few fields.

* ID documents: passports, driver licenses, etc.
* Healthcare cards
* Tickets, boarding passes
* Envelopes, packages

### Average

Single page with nested objects. Multiple pages with no nested objects.

* Most receipts
* Single page invoices
* Bills of lading
* Most business contracts

### Slower

Multiple pages with nested objects and small text.

* Very long receipts with many items and small text (like groceries for the week)
* Invoices with more than 10 pages, each page having many items
* Monthly bank statements
