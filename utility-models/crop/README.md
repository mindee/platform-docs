---
description: >-
  Automatically identify the borders of documents on each page, and match one to
  a category.
icon: crop-simple
---

# Crop Model

## Use Cases

Process different documents sent on the same page (usually a photo). The result has both the location (page and coordinates) and the class for each document identified, allowing for complex workflows.

A file sent to the Crop Model may have any number of pages, [within limits](../../integrations/technical-limitations.md#file-limits). Use the page index in the results to identify on which page the document was found.

Some common examples:

* Single photo of a bunch of receipts on the table
* Front and back of an ID card, each on the same PDF page
* Remove the background from all documents in a multi-page PDF

## Create a Crop Model

1. To create a Crop utility, click on **Models**, and then click on **Create your document AI model**.
2. Scroll to the **Document Utilities** section, click on **Crop.**
3. A pop-up will appear, allowing you to enter the classes you want. Each class corresponds to a  document type possibly present in the pages you want to process.\
   \
   For example, if the files you are processing contain ID cards and passports, set the classes as: `ID Card Front`, `ID Card Back`, `Passport`.

{% include "../../.gitbook/includes/utilities-other-class.md" %}

<figure><img src="../../.gitbook/assets/image (7).png" alt="" width="375"><figcaption></figcaption></figure>



4. Once ready, click on **Create Utility** to create your custom Crop Utility.
5. You can now use the **Live Test** tab to process documents, and the **Utility Configuration** to update your classes.<br>

Your utility is now available in your **Models** tab:

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

Here is a step-by-step tutorial that shows you how to properly create a Crop Utility :&#x20;

{% @supademo/embed demoId="cmlrtp7mk0u531189vkn2azqr" url="https://app.supademo.com/demo/cmlrtp7mk0u531189vkn2azqr" %}

## Integration

{% include "../../.gitbook/includes/utilities-class-names.md" %}

Once your Crop model is created and tested, integration documentation is provided in the "Documentation" page.
