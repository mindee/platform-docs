---
description: Selectively extract data from detected classes.
icon: link-horizontal
---

# Extraction Model Chaining

Link a Classification model to one or more [Extraction Models](../extraction-models/extraction-models-overview.md), to automatically extract structured data from documents based on their detected class.

Note: Classification Models always return a single class regardless of the number of pages or if there are multiple documents on the same page.

## Extraction Set Up

### At Model Creation

When creating your Classification Model, you'll be adding document classes in the creation window.

For each document class, you can link one of your Extraction Models for chaining. The Extraction Model must exist prior to the Classification Model creation.

Use the search field to filter available Extraction Models.

### After Model Creation

This works exactly like when creating at model creation.

Simply go to your Split model's "Utility Configuration" page and adjust as needed.

You can add new classes, remove classes, and change Extraction Models.

### Selectively Extracting

All documents will get classified, but only those linked to an Extraction Model will have extraction results.

This allows selectively extracting some files while ignoring others.

Let's say you receive mixed file types from your users, as an example: plane tickets, travel receipts, driver licenses, and passports.

As a simple example, let's assume you need only the passports. In your Classification configuration, add a `passport` class and an `other`  class, then chain a [Passport extraction model](../use-cases/extraction-models/passport.md) on the `passport` class. Do not chain any models on the `other` class.

Another example, if you need only IDs (so driver license and passport), you have two choices:

* Create an `identification_document` class and chain it to an [International ID extraction model](../use-cases/extraction-models/international-id-card.md).\
  This is recommended if you accept a wide variety of ID documents.
* Create a `driving_license` and `passport` class and chain the [Driver's License](../use-cases/extraction-models/drivers-license.md) and Passport extraction models to them, respectively.\
  This is recommended if you only accept a certain subset of ID documents.

As in the earlier example, do not chain any models on the `other` class.

In the above examples, the documents classified as `other` will **not** have extraction results, while those with specific classes **will** have results.

{% include "../.gitbook/includes/use-other-classes.md" %}

### Token Usage With Chaining

{% include "../.gitbook/includes/token-cost-chained-extraction-model.md" %}

## Access Extraction Results

When an Extraction Model is linked, the detected class contains an Extraction Response object.

That object is the same as the response returned by a standalone Extraction request.

Check [classification-result.md](sdk-integration/classification-result.md "mention") for details on accessing crop items and their extraction responses.
