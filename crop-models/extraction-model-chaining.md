---
description: Selectively extract data from detected crops.
icon: link-horizontal
---

# Extraction Model Chaining

Link a Crop model to one or more [Extraction Models](../extraction-models/extraction-models-overview.md), to automatically extract structured data from documents based on their detected class.

Since Crop models can detect multiple document classes on the same page, several different extractions can be made on a single image file.

Crop models work on multi-page files, with potentially multiple crop items on each page.

Note:  Each crop item is limited to an area on a single page. If you need a single extraction result covering multiple pages, take a look at [Split Models](https://app.gitbook.com/s/u5bStlX8nv4b9z4GXB2S/split-models "mention") instead.

## Extraction Set Up

### At Model Creation

When creating your Crop model, you'll be adding document classes in the creation window.

For each document class, you can link one of your [Extraction Models](https://app.gitbook.com/s/u5bStlX8nv4b9z4GXB2S/extraction-models "mention") for chaining. The Extraction Model must exist prior to the Crop Model creation.

Use the search field to filter available extraction models.

### After Model Creation

This works exactly like when creating at model creation.

Simply go to your Crop Model's "Utility Configuration" page and adjust as needed.

You can add new classes, remove classes, and change Extraction Models.

### Selectively Extracting

If a detected class has no linked Extraction Model, no extraction runs for that crop.

This allows selectively extracting some parts while ignoring others.

Let's say your users upload images of their trip documents on their hotel table, typically but not limited to: plane tickets, travel receipts, driver license, and passport.

You need only the passports.

In your Crop configuration, add a `passport` class and an `other`  class, and only link an extraction model to the `passport` class.

All crop items will get classified, but only those linked to an Extraction Model will have extraction results.

{% include "../.gitbook/includes/use-other-classes.md" %}

## Token Usage With Chaining

{% include "../.gitbook/includes/token-cost-chained-extraction-model.md" %}

For Crop models specifically, there can be multiple chained extractions on the same file. Since each page may contain multiple documents, the total pages processed can be greater than the total number of pages in the source document.

For example, on a JPEG image where 4 receipts are detected and each receipt is chained to an extraction model, processing the file will consume 4 pages worth of credits.

## Access Extraction Results

When an Extraction Model is linked, each detected crop item with that class contains an Extraction Response object.

That object is the same as the response returned by a standalone Extraction request.

Because Crop works at object level, several crop items on the same page can each contain their own extraction result.

Check [crop-result.md](sdk-integration/crop-result.md "mention") for details on accessing crop items and their extraction responses.
