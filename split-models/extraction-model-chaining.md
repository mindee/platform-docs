---
description: Extract data from split ranges.
icon: link-horizontal
---

# Extraction Model Chaining

Use Split to automatically extract document data, meaning that several different extractions can be made for a single file.

## Extraction Set Up

### At Model Creation

When creating your Split model, you'll be adding document classes in the creation window.

For each document class, you can set one of your [Broken link](/broken/pages/ywb5XsDuWyBy07coiRb0 "mention") for chaining. The Extraction Model must exist prior to the Split Model creation.

Use the search field to filter available extraction models.

<figure><img src="../.gitbook/assets/split-creation-chaining.png" alt="Configuring extraction model chaining on Split creation" width="563"><figcaption></figcaption></figure>

### After Model Creation

This works exactly like when creating at model creation.

Simply go to your Split model's "Utility Configuration" page and adjust as needed.

You can add new classes, remove classes, and change Extraction Models.

<figure><img src="../.gitbook/assets/split-created-chaining.png" alt="Configuring extraction model chaining on Split after creation" width="563"><figcaption></figcaption></figure>

### Selectively Extracting

If a detected class has no linked Extraction Model, no extraction runs for that crop.

This allows selectively extracting some sections of the file while ignoring others.

Let's say you receive large multi-page PDFs from your users, where each PDF is a bundle of different scanned documents: plane tickets, travel receipts, driver license, and passport.

You need only the passports.

In your Split configuration, add a `passport` class and an `other`  class, and only link an extraction model to the `passport` class.

All split ranges will get classified, but only those linked to an Extraction Model will have extraction results.

{% include "../.gitbook/includes/use-other-classes.md" %}

## Access Extraction Results

When an Extraction model is linked, each Split Range with the detected class will contain an Extraction Response object, which is identical when making an Extraction request for a single document.

Check the [split-result.md](sdk-integration/split-result.md "mention") section for more details.
