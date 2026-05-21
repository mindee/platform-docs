---
description: Extract data from split ranges.
icon: link-horizontal
---

# Extraction Model Chaining

Use Split to automatically extract document data, meaning that several different extractions can be made for a single file.

## Set Up

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

If no Extraction Model is linked, when the class is detected, no extraction will be performed.

This allows selectively extracting some portions of the file while ignoring others.

Let's say you receive PDFs from your users, where each PDF is a bundle of different documents: plane tickets, travel receipts, driver licenses, and passports.

You need only passports. In your Split configuration, add a "passport" class and an "other"  class, and only link an extraction model to the "passport" class. By only linking to the documents of interest, we ensure only those will get extracted.
