---
icon: hand
---

# Technical Limitations

## Overview

A set of limits are enforced to ensure the safety of Mindee's parsing document APIs.

An API call that causes any of these limits to be exceeded will be rejected with an error.

## Accepted Files

### PDF Files

All Portable Document Format (PDF) types can be processed, either single page or multiple pages.

Each PDF page can be a combination of text and image elements.

### Image Files

Most common image types can be processed.

Specifically, we accept the following image types:

<table><thead><tr><th width="140">Type</th><th width="158.5">Media Type</th><th width="135.5">Extensions</th><th>Notes</th></tr></thead><tbody><tr><td> <a data-footnote-ref href="#user-content-fn-1">JPEG</a></td><td>image/jpeg</td><td>jpeg, jpg</td><td></td></tr><tr><td><a data-footnote-ref href="#user-content-fn-2">PNG</a></td><td>image/png</td><td>png</td><td>non-animated only</td></tr><tr><td>WebP</td><td>image/webp</td><td>webp</td><td></td></tr><tr><td> <a data-footnote-ref href="#user-content-fn-3">TIFF</a></td><td>image/tiff</td><td>tiff, tif</td><td>single page or multiple pages</td></tr><tr><td> <a data-footnote-ref href="#user-content-fn-4">HEIC</a></td><td>image/heic</td><td>heic</td><td></td></tr></tbody></table>

## File Limits

| Limit type              | Limit value |
| ----------------------- | ----------- |
| Max file size           | 100 MB      |
| Maximum number of pages | 200 pages   |

Take a look at the following sections for workarounds on these limits:

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

## Data Schema

{% include "../.gitbook/includes/data-schema-technical-limitations.md" %}

[^1]: Joint Photographic Experts Group

[^2]: Portable Network Graphics

[^3]: Tag Image File Format

[^4]: High-Efficiency Image Container
