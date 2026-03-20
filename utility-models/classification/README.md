---
description: >-
  Automatically attribute a class to a given document, from a list of classes
  you define yourself.
icon: tag
---

# Classification Model

## Use Cases

Process a single document sent in a single file. The classifier looks at all pages of the document in order to identify its type.

Some common examples:

* You have multiple types of files in your workflow input, with different business rules
* You want to identify the region or language of documents

A file sent to the Classification Model may have any number of pages, [within limits](../../integrations/technical-limitations.md#file-limits).

{% hint style="info" %}
If there is a high possibility of having multiple documents within the same file, use:

* [split](../split/ "mention") ⇒ multiple documents in the same file
* [crop](../crop/ "mention") ⇒ multiple documents on the same page
{% endhint %}

## Create a Classification Model

1. To create a Classification utility, click on **Models**, and then click on **Create your document AI model**.
2. Scroll to the **Document Utilities** section, click on **Classify.**
3. A pop-up will appear, allowing you to enter the classes you want. Most of the time, you'll use one possible document type per class.\
   \
   For example, f the files you are processing contain invoices, receipts, and driving licenses, set the classes as: `INVOICES`, `IDENTITY DOCUMENTS`, `CONTRACTS`.

{% include "../../.gitbook/includes/utilities-other-class.md" %}

<figure><img src="../../.gitbook/assets/image (11).png" alt="" width="375"><figcaption></figcaption></figure>

4. Once ready, click on **Create Utility** to create your custom Classify Utility.
5. You can now use the **Live Test** tab to process documents, and the **Utility Configuration** to update your classes.<br>

Your utility is now available in your **Models** tab.

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

Here is a step-by-step tutorial that shows you how to properly create a Classify Utility :

{% @supademo/embed demoId="cmls1rubd1jal11896wj0sg8q" url="https://app.supademo.com/demo/cmls1rubd1jal11896wj0sg8q" %}

## Integration

{% include "../../.gitbook/includes/utilities-class-names.md" %}

Once your Classification model is created and tested, integration documentation is provided in the "Documentation" page, or here: [integration.md](../crop/integration.md "mention").
