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

{% hint style="warning" %}
PDF files cannot be password-protected.
{% endhint %}

### Image Files

Most common image types can be processed.

Specifically, we accept the following image types:

<table><thead><tr><th width="140">Type</th><th width="158.5">Media Type</th><th width="135.5">Extensions</th><th>Notes</th></tr></thead><tbody><tr><td> <a data-footnote-ref href="#user-content-fn-1">JPEG</a></td><td>image/jpeg</td><td>jpeg, jpg</td><td></td></tr><tr><td><a data-footnote-ref href="#user-content-fn-2">PNG</a></td><td>image/png</td><td>png</td><td>non-animated only</td></tr><tr><td>WebP</td><td>image/webp</td><td>webp</td><td></td></tr><tr><td> <a data-footnote-ref href="#user-content-fn-3">TIFF</a></td><td>image/tiff</td><td>tiff, tif</td><td>single page or multiple pages</td></tr><tr><td> <a data-footnote-ref href="#user-content-fn-4">HEIC</a></td><td>image/heic</td><td>heic</td><td></td></tr></tbody></table>

### File Limits

These limits apply to all files, regardless of source or type.

| Limit type              | Limit value |
| ----------------------- | ----------- |
| Max file size           | 100 MB      |
| Maximum number of pages | 200 pages   |

If you have access to the file locally, there are workarounds available for these limits:

* [#manipulate-pdf-pages](client-libraries-sdk/load-and-adjust-a-file.md#manipulate-pdf-pages "mention")
* [#compress-files](client-libraries-sdk/load-and-adjust-a-file.md#compress-files "mention")

Requires using our [client-libraries-sdk](client-libraries-sdk/ "mention").

### URLs

When sending a file as an URL rather than as binary data.

{% include "../.gitbook/includes/file-url-technical-limitation.md" %}

## Rate Limits

Calls to the Mindee API are limited to ensure the stability of the platform for all users.

These limits apply to an entire organization, meaning the combination of all models, origin IPs, and API keys.

The following limits are enforced:

* [Send for Processing](client-libraries-sdk/send-a-file-or-url.md#send-for-processing) ⇒ 50 requests per minute
* Polling ⇒ 300 requests per minute\
  Normally, this is handled automatically by the client library.

If rate limits are exceeded, the server will return a HTTP 429 error.

{% hint style="success" %}
If you have needs beyond these limits, get in touch with the [sales team](mailto:hello@mindee.com) for a custom solution.
{% endhint %}

## Data Schema

{% include "../.gitbook/includes/data-schema-technical-limitations.md" %}

## Webhooks

{% include "../.gitbook/includes/webhook-technical-limitations.md" %}



[^1]: Joint Photographic Experts Group

[^2]: Portable Network Graphics

[^3]: Tag Image File Format

[^4]: High-Efficiency Image Container
