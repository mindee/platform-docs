---
icon: circle-info
---

# Technical Guidelines

## Usage in Web Applications

We **do not recommend** using the Mindee API directly in an application running in the final user's web browser.

Users will be **trivially** able to intercept the API Key used for the Mindee requests, and impersonate your account.

Our official guideline is to **always** pass your user requests through a server which you control.\
Not only will this prevent leakage of sensitive data, it will allow you to much more easily diagnose any issues your users may have.

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

### **Do not upscale or enhance**

Never upscale a low-resolution image, adding extra pixels only adds to processing time without an increase in accuracy.\
It is best to avoid very low-resolution images, if possible.

### **Keep the aspect ratio**

Never change the original aspect ratio. Doing so will create distortions and degrade the performance of the OCR.
