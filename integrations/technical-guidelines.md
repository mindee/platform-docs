---
description: Technical guidelines for an optimal integration.
icon: circle-info
---

# Technical Best Practices

## Guidelines For Uploading Files

Following these guidelines will ensure you get the most accurate results as quickly as possible.

### **Reduce very large images**

For faster upload and processing, downscale large images by resizing them.

For example modern smartphones can take images of 24 megapixels or more, in most cases this is completely useless, a waste of bandwidth and processing time.

For the vast majority of image files, 3-5 megapixels is enough. Just make sure the smallest text is legible.

We offer free tooling for compressing and resizing images or PDFs before sending them.\
Details here: [#compress-files](client-libraries-sdk/load-and-adjust-a-file.md#compress-files "mention")

### **Send Only What You Need**

When processing multi-page PDFs, in some cases not all pages are required to be sent for your use case.

For example, on some invoice templates the last page will be terms and conditions, this is typically very dense text that will slow down processing (and cost you money).

We offer free tooling for removing pages from PDFs before sending them.\
Details here: [#manipulate-pdf-pages](client-libraries-sdk/load-and-adjust-a-file.md#manipulate-pdf-pages "mention")

### **Do Not Upscale or Enhance**

Never upscale a low-resolution image, adding extra pixels only adds to processing time without an increase in accuracy.\
It is best to avoid very low-resolution images, if possible.

### **Keep the Aspect Ratio**

Never change the original aspect ratio. Doing so will create distortions and degrade the performance of the OCR.

### Use Text PDFs When Possible

Text (or native) PDFs are easier and faster to process. In addition, using a text PDF will provide better accuracy than an image PDF or image file.

If providing text PDFs is not possible, the next best format would be [scanned PDFs](technical-guidelines.md#scans-are-better-than-photos).

### Scans Are Better Than Photos

If possible, providing scanned images may provide better results compared to photos (typically taken with a phone).

**This is not to say that photos won't work well**, Mindee has many major users where photos (of receipts and ID documents notably) are the main use case.

For simple documents the difference is usually negligible, if user errors like blurry or cut-off photos are excluded. However, if you are handling complex documents like bank statements or multi-page invoices, scans typically have fewer errors on average.

## Usage in Web Applications

Our official guideline for Web Applications is to **always** pass your user requests through a server which you control:

* This will prevent leakage of sensitive data.
* You'll be able to much more easily diagnose any issues your users may have.

As such, we **do not recommend** using the Mindee API **directly** in an application running in the final user's web browser.

Users will be **trivially** able to intercept the API Key used for the Mindee requests, and impersonate your account.

{% hint style="info" %}
**In short:&#x20;**_**never**_**&#x20;do this**. It will only cause suffering.
{% endhint %}

## Usage in Mobile Applications

Our official guideline for Mobile Applications is to strongly prefer passing your user requests through a server which you control:

* You'll benefit from increased security and control.
* You'll be able to much more easily diagnose any issues your users may have.

As such, we **do not recommend** using the Mindee API **directly** in an application running in the final user's mobile device.

Users may be able to obtain your API key from the device.

We recommend cycling through API keys at regular intervals. Depending on your application's setup, it could be problematic to update the API Keys on the device.

Potentially, users interact with the Mindee service outside of your control. This can lead to unexpected overage charges to your account.

Possible exceptions to the recommendation:

* Usage in internal applications on devices or environments you control
* The API Key is easily revocable on the device, and _never_ user-accessible

{% hint style="info" %}
**In short: avoid if at all possible**. Only use if you really need it and understand the risks involved.
{% endhint %}
