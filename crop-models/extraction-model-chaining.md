---
description: Extract data from detected crops.
icon: link-horizontal
---

# Extraction Model Chaining

Use Crop to automatically extract data from detected objects.

Several extractions can be made for the same file.

## Extraction Set Up

### At Model Creation

When creating your Crop model, you'll be adding document classes in the creation window.

For each document class, you can set one of your [Broken link](/broken/pages/ywb5XsDuWyBy07coiRb0 "mention") for chaining. The Extraction Model must exist prior to the Split Model creation.

Use the search field to filter available extraction models.

### After Model Creation

This works exactly like when creating at model creation.

Simply go to your Split model's "Utility Configuration" page and adjust as needed.

You can add new classes, remove classes, and change Extraction Models.

### Selectively Extracting

If a detected class has no linked Extraction Model, no extraction runs for that crop.

This allows selectively extracting some parts while ignoring others.

For example, a single image may contain receipts, loyalty cards, and handwritten notes.

If you only need receipts, link an Extraction Model only to the `receipt` class.

Mindee will still detect the other crop items, but it will only extract the linked ones.

## Access Extraction Results

When an Extraction Model is linked, each detected crop item with that class contains an Extraction Response object.

That object is the same as the response returned by a standalone Extraction request.

Because Crop works at object level, several crop items on the same page can each contain their own extraction result.

Check [crop-result.md](sdk-integration/crop-result.md "mention") for details on accessing crop items and their extraction responses.
