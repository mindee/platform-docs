---
description: Extract data from detected crops.
icon: link-horizontal
---

# Extraction Model Chaining

Use Crop to automatically extract document data, meaning that several different extractions can be made for a single image.

Note: Crop Models also work on multi-page files, with potentially multiple crop items for each page. However each crop item is limited to an area on a single page. If you need a single extraction result covering multiple pages, take a look at [Broken link](/broken/pages/DQwnO3TRbgwm3KTlXsd8 "mention") instead.

## Extraction Set Up

### At Model Creation

When creating your Crop model, you'll be adding document classes in the creation window.

For each document class, you can link one of your [Broken link](/broken/pages/ywb5XsDuWyBy07coiRb0 "mention") for chaining. The Extraction Model must exist prior to the Crop Model creation.

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

## Access Extraction Results

When an Extraction Model is linked, each detected crop item with that class contains an Extraction Response object.

That object is the same as the response returned by a standalone Extraction request.

Because Crop works at object level, several crop items on the same page can each contain their own extraction result.

Check [crop-result.md](sdk-integration/crop-result.md "mention") for details on accessing crop items and their extraction responses.
