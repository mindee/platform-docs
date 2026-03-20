---
description: >-
  Automatically breaking a multi-page source file into separate documents and
  associate a class to each one.
icon: rectangle-vertical-history
---

# Split Model

## Use Cases

Process a bundle of different documents sent in the same file. The result has both the page range and the class for each document identified, allowing for complex workflows.

Some common examples, where a single PDF contains:

* Several different invoices
* A mix of invoices, receipts, and bank statements
* The person's driver license, vehicle registration, insurance
* Front and back of an ID card, each on a separate page
* The same type of document, but from different regions or languages

A file sent to the Split Model may have any number of pages, [within limits](../../integrations/technical-limitations.md#file-limits).

## Create a Split Model

1. To create a Split utility, you need to click on **Models**, and then on **Create your document AI model**.
2. Scroll to the **Document Utilities** section, click on **Split.**
3. A pop-up will appear, allowing you to enter the classes you want. Each class corresponds to a  document type possibly present in the documents you want to process.\
   \
   For example, if the files you are processing contain invoices, receipts, and driving licenses, set the classes as: `INVOICE`, `RECEIPT`, `DRIVING LICENSE`.

{% include "../../.gitbook/includes/utilities-other-class.md" %}

<figure><img src="../../.gitbook/assets/image (5).png" alt="" width="375"><figcaption></figcaption></figure>



4. Once ready, click on **Create Utility** to create your custom Split Utility.
5. You can now use the **Live Test** tab to process documents, and the **Utility Configuration** to update your classes.<br>

Your utility is now available in your **Models** tab:

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

Here is a step-by-step tutorial that shows you how to properly create a Split Utility : <br>

{% @supademo/embed demoId="cmls4fbup1r1611891nvrrlyw" url="https://app.supademo.com/demo/cmls4fbup1r1611891nvrrlyw" %}

## Integration

{% include "../../.gitbook/includes/utilities-class-names.md" %}

Once your Split model is created and tested, integration documentation is provided in the "Documentation" page, or here: [integration.md](integration.md "mention").
