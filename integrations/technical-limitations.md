---
description: Technical limitations when integrating Mindee.
icon: hand
---

# Technical Limitations

## Overview

These limitations are designed to ensure the safety and stability of the Mindee API and platform.

Unless noted otherwise, any action that exceeds or does not comply with the limitations will be rejected with an error.

## Accepted Files

### PDF Files

All Portable Document Format (PDF) types can be processed, either single page or multiple pages.

Each PDF page can be a combination of text and image elements.

### Image Files

Most common image types can be processed.

Specifically, we accept the following image types:

<table><thead><tr><th width="140">Type</th><th width="158.5">Media Type</th><th width="135.5">Extensions</th><th>Notes</th></tr></thead><tbody><tr><td> <a data-footnote-ref href="#user-content-fn-1">JPEG</a></td><td>image/jpeg</td><td>jpeg, jpg</td><td></td></tr><tr><td><a data-footnote-ref href="#user-content-fn-2">PNG</a></td><td>image/png</td><td>png</td><td>non-animated only</td></tr><tr><td>WebP</td><td>image/webp</td><td>webp</td><td></td></tr><tr><td> <a data-footnote-ref href="#user-content-fn-3">TIFF</a></td><td>image/tiff</td><td>tiff, tif</td><td>single page or multiple pages</td></tr><tr><td> <a data-footnote-ref href="#user-content-fn-4">HEIC</a></td><td>image/heic</td><td>heic</td><td></td></tr></tbody></table>

### URLs

When sending a file through an URL rather than binary data.

{% include "../.gitbook/includes/file-url-technical-limitation.md" %}

### File Limits

These limits apply to all files, regardless of source or type.

| Limit type              | Limit value |
| ----------------------- | ----------- |
| Max file size           | 100 MB      |
| Maximum number of pages | 200 pages   |

If you can have the file locally, there are workarounds available for these limits:

* [#manipulate-pdf-pages](client-libraries-sdk/load-and-adjust-a-file.md#manipulate-pdf-pages "mention")
* [#compress-files](client-libraries-sdk/load-and-adjust-a-file.md#compress-files "mention")

Requires using our [client-libraries-sdk](client-libraries-sdk/ "mention").

## Rate Limits

{% hint style="info" %}
If you have needs beyond these limits, get in touch with the sales team for a custom solution.
{% endhint %}

### API Calls

For information about the pricing model of Mindee, please refer yourself to the [pricing](https://mindee.com/pricing) on the website.

### Requests

| Maximum request throughput | Limits        |
| -------------------------- | ------------- |
| per hour                   | 3000 requests |
| per minute                 | 120 requests  |
| per second                 | 5 requests    |

{% hint style="info" %}
**General tip:** You may space your API requests so that you don't go over the limit.
{% endhint %}

## Response Times

Response time will vary depending on the document, the Data Schema, and the options selected.

Unfortunately, there is no free lunch.

Source file properties which impact response time:

* file size, especially for images files
* number of pages
* density of text

Take a look at the [#guidelines-for-uploading-files](technical-guidelines.md#guidelines-for-uploading-files "mention") section for ways to improve source files.

Data Schema properties which impact response time:

* number of fields
* complexity of guidelines

Additionally, if there are list fields in the Data Schema and many items in the source document.\
For example: a receipt document with many products purchased, and each product being returned in the response.

Processing options which impact response time:

* [improving-accuracy.md](../models/improving-accuracy.md "mention")
* [automation-confidence-score.md](../models/automation-confidence-score.md "mention")
* [polygons-bounding-boxes.md](../models/polygons-bounding-boxes.md "mention")

## Data Schema

{% include "../.gitbook/includes/data-schema-technical-limitations.md" %}

## Webhooks

{% include "../.gitbook/includes/webhook-technical-limitations.md" %}



[^1]: Joint Photographic Experts Group

[^2]: Portable Network Graphics

[^3]: Tag Image File Format

[^4]: High-Efficiency Image Container
