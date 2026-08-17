---
description: Technical limitations when integrating Mindee.
icon: hand
---

# Technical Limitations

These limitations are designed to ensure the safety and stability of the Mindee API and platform.

Unless noted otherwise, any action that exceeds or does not comply with the limitations will be rejected with an error.

## Accepted Files

### PDF Files

All Portable Document Format (PDF) can be processed, either single page or multiple pages.

These are defined using the `application/pdf` Media type.

In some cases `application/binary` is used, this is incorrect as per the standard, but should also work, so long as the extension is `.pdf` and the binary contents are a valid PDF file.

In rare cases, the PDF headers are corrupted or invalid. Fix these using our [PDF repair tool](client-libraries-sdk/load-and-adjust-a-file.md#fix-pdf-headers), otherwise the server may reject them.

Each PDF page can be a combination of text and image elements.

{% hint style="warning" %}
**PDF files cannot be password-protected.**

The server will not attempt to open a password-protected file, so this limitation includes empty or blank passwords.
{% endhint %}

### Image Files

Most common image types can be processed.

Specifically, we accept the following image types:

<table><thead><tr><th width="140">Type</th><th width="158.5">Media Type</th><th width="135.5">Extensions</th><th>Notes</th></tr></thead><tbody><tr><td><a data-footnote-ref href="#user-content-fn-1">JPEG</a></td><td>image/jpeg</td><td>jpeg, jpg</td><td></td></tr><tr><td><a data-footnote-ref href="#user-content-fn-2">PNG</a></td><td>image/png</td><td>png</td><td>non-animated only</td></tr><tr><td>WebP</td><td>image/webp</td><td>webp</td><td></td></tr><tr><td><a data-footnote-ref href="#user-content-fn-3">TIFF</a></td><td>image/tiff</td><td>tiff, tif</td><td>single page or multiple pages</td></tr><tr><td><a data-footnote-ref href="#user-content-fn-4">HEIC</a></td><td>image/heic</td><td>heic</td><td></td></tr><tr><td><a data-footnote-ref href="#user-content-fn-5">HEIF</a></td><td>image/heif</td><td>heif</td><td>Single HEVC-encoded image only.</td></tr></tbody></table>

### Zip Files

As a convenience for testing, it is possible to upload Zip files to the [Live Test](../models/live-test.md).

The API does not support sending Zip files.

### API File Limits

These limits apply to all files sent to the API, regardless of type.

<table><thead><tr><th width="170.800048828125">Limit type</th><th width="152.7999267578125">All Paid Plans</th><th width="162.4000244140625">Free Trial</th></tr></thead><tbody><tr><td>File Size</td><td>100 MB</td><td>100 MB</td></tr><tr><td>Number of Pages</td><td>No limit</td><td>10 pages</td></tr></tbody></table>

If you have access to the file locally, there are workarounds available for these limits:

* [#manipulate-pdf-pages](client-libraries-sdk/load-and-adjust-a-file.md#manipulate-pdf-pages "mention")
* [#compress-files](client-libraries-sdk/load-and-adjust-a-file.md#compress-files "mention")

Requires using our [client-libraries-sdk](client-libraries-sdk/ "mention").

### Live Test File Limits

These limits apply to files sent to the [Live Test](../models/live-test.md).

{% include "../.gitbook/includes/live-test-file-limits-table.md" %}

## Accepted URLs

It is possible to send an URL rather than binary data to the API.

{% include "../.gitbook/includes/file-url-technical-limitation.md" %}

## Rate Limits

Calls to the Mindee API are limited to ensure the stability of the platform for all users.

These limits apply to an entire organization, meaning the combination of all models, origin IPs, and API keys.

The following limits are enforced:

<table><thead><tr><th width="254">Limit Type</th><th>Limit Value</th></tr></thead><tbody><tr><td>Send for Processing (POST)</td><td>200 requests per minute</td></tr><tr><td>Polling (GET)</td><td>1200 requests per minute<br><em>Normally, this is handled by the client library.</em></td></tr></tbody></table>

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

[^5]: 
