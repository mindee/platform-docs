---
icon: tag
---

# Classify

This utility is designed to allow you automatically attribute a class to a given document, from a list of classes you define yourself.&#x20;

{% hint style="success" %}
If your documents have one or several pages and you want to get the most appropriate class for the whole document, **Classify** is definitely your best option.&#x20;
{% endhint %}

{% hint style="warning" %}
If your documents have more than one page, and you need to find the different document types present in the whole file, then [**Split**](split.md) is probably a better utility for your use case.
{% endhint %}

## Setup

1. To create a Classify utility, you need to click on **Models**, and then on **Create your document AI model**.
2. Under the **Document Utilities** section, click on **Classify.**
3. A pop-up will appear, allowing you to enter the classes you want. Most of the time, you'll use one possible document type per class.\
   \
   &#xNAN;_&#x45;xample: If the files you are receiving may contain invoices, receipts, and driving licenses you may select the three classes "INVOICES", "IDENTITY DOCUMENTS", "CONTRACTS"._

{% hint style="info" %}
Add the class "Other" if you need the model to identify documents that are not one of the precedent document types.
{% endhint %}

<figure><img src="../../.gitbook/assets/image (11).png" alt="" width="375"><figcaption></figcaption></figure>

4. Once ready, click on **Create Utility** to create your custom Classify Utility.
5. You can now use the **Live Test** tab to process documents, and the **Utility Configuration** to update your classes.<br>

Your utility is now available in your **Models** tab.

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

Here is a step-by-step tutorial that shows you how to properly create a Classify Utility :

{% @supademo/embed demoId="cmls1rubd1jal11896wj0sg8q" url="https://app.supademo.com/demo/cmls1rubd1jal11896wj0sg8q" %}
