---
icon: hand
---

# Technical Limits

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

## General Guidelines For Uploading Files

Following these guidelines will ensure you get the most accurate results as quickly as possible.

### **Reduce very large images**

For faster upload and processing, downscale large images by resizing them.

For example modern smartphones can take images of 24 megapixels or more, in most cases this is completely useless, a waste of bandwidth and processing time.

For the vast majority of image files, 3-5 megapixels is enough. Just make sure the smallest text is legible.

We offer free tooling for compressing and resizing images or PDFs before sending them.\
Details here: [#file-compression](client-libraries-sdk/load-and-adjust-a-file.md#file-compression "mention")

### **Do not upscale or enhance**

Never upscale a low-resolution image, adding extra pixels only adds to processing time without an increase in accuracy.\
It is best to avoid very low-resolution images, if possible.

### **Keep the aspect ratio**

Never change the original aspect ratio. Doing so will create distortions and degrade the performance of the OCR.

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

### Data Schema

For your data schema, the recommended maximum number of properties is 25. Beyond this limit, performances will be drastically reduced.

Payload in Mindee refers to the data that you send to the server when you make an API request .



[^1]: Joint Photographic Experts Group

[^2]: Portable Network Graphics

[^3]: Tag Image File Format

[^4]: High-Efficiency Image Container
