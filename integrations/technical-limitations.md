---
icon: hand
---

# Technical Limitations

A set of limits are enforced to ensure the safety of Mindee's parsing document APIs. An API call that causes any of these limits to be exceeded will be rejected with an error.&#x20;

{% hint style="info" %}
If you have needs beyond these limits then get in touch with the sales team and we'll work something out.
{% endhint %}

***

## Accepted document files

| Type                                          | MIME Type       | Extensions |
| --------------------------------------------- | --------------- | ---------- |
| Image JPEG (Joint Photographic Experts Group) | image/jpeg      | jpeg, jpg  |
| Image PNG (Portable Network Graphics)         | image/png       | png        |
| Image WEBP                                    | image/webp      | webp       |
| PDF (Adobe Portable Document Format)          | application/pdf | pdf        |
| Image TIFF (Tag Image File Format)            | image/tiff      | tiff, tif  |
| Image HEIC (High-Efficiency Image Container)  | image/heic      | heic       |

***

## Rate Limits

### Documents

| Limits              | Extraction Mode |
| ------------------- | --------------- |
| Max file size       | 100 MB          |
| Max number of pages | 200 pages       |

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

### Data model

For your data model, the maximum number of properties is 50. If you think you need more, please get in touch with the [support team](mailto:contact@mindee.com), so they can further discuss the situation with you.

### Payload

Payload in Mindee refers to the data that you send to the server when you make an API request .

