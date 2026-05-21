---
description: Extract data from detected classes.
icon: link-horizontal
---

# Extraction Model Chaining

Use Classification to automatically extract the correct data from files.

Note: Classification Models always return a single class regardless of the number of pages or if there are multiple documents on the same page.

## Extraction Set Up

### At Model Creation

When creating your Classification Model, you'll be adding document classes in the creation window.

For each document class, you can link one of your [Broken link](/broken/pages/ywb5XsDuWyBy07coiRb0 "mention") for chaining. The Extraction Model must exist prior to the Classification Model creation.

Use the search field to filter available Extraction Models.

### After Model Creation

This works exactly like when creating at model creation.

Simply go to your Split model's "Utility Configuration" page and adjust as needed.

You can add new classes, remove classes, and change Extraction Models.

### Selectively Extracting

If a detected class has no linked Extraction Model, no extraction runs for that class.

This allows selectively extracting some files while ignoring others.

Let's say you receive mixed file types from your users, typically but not limited to: plane tickets, travel receipts, driver licenses, and passports.

You need only passports. In your Classification configuration, add a `passport` class and an `other`  class, and only link an extraction model to the `passport` class.

All documents will get classified, but only those linked to an Extraction Model will have extraction results.

{% include "../.gitbook/includes/use-other-classes.md" %}

## Access Extraction Results

When an Extraction Model is linked, the detected class contains an Extraction Response object.

That object is the same as the response returned by a standalone Extraction request.

Check [classification-result.md](sdk-integration/classification-result.md "mention") for details on accessing crop items and their extraction responses.
