---
icon: file-lines
---

# Crop

This utility is designed to allow you automatically identify the borders of documents on each page, and match one to a category. \
\
It is particularly useful when :&#x20;

* dealing with documents that may contain several documents (receipts for instance) within each page
* searching to remove the background from a document

## Setup



1. To create a Crop utility, you need to click on **Models**, and then on **Create your document AI model**.
2. Under the **Document Utilities** section, click on **Crop.**
3. A pop-up will appear, allowing you to enter the classes you want. Each class corresponds to a  document type possibly present in the pages you want to process. \
   \
   &#xNAN;_&#x45;xample: If the files you are receiving may contain ID cards and passports, you may select the three classes :_ _"ID Card Front", "ID Card Back", "Passport"._&#x20;

_Don't forget to add the class "Other" if you need the model to identify documents that are not one of the precedent document types._&#x20;

<figure><img src="../../.gitbook/assets/image (7).png" alt="" width="375"><figcaption></figcaption></figure>



4. Once ready, click on **Create Utility** to create your custom Crop Utility.
5. You can now use the **Live Test** tab to process documents, and the **Utility Configuration** to update your classes.<br>

Your utility is now available in your **Models** tab:

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>
