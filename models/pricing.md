---
description: >-
  Information on credit consumption for processing documents using a given
  model.
icon: coins
---

# Credit Cost

Each file successfully processed by a model will consume credits based on the number of pages contained in the file.

Files that are sent but not processed (i.e. job status "Failed", or HTTP 400) do not consume credits.

The model's "Credit Cost" page shows the exact amount of credits consumed per page processed.

For files having more than one page, such as PDF or TIFF, this is every page of the file.\
Single image files count as one page.

For example, assuming 1 credit per page:

* Single page text PDF file ⇒ 1 credit
* 5 page text and image PDF file ⇒ 5 credits
* A JPEG file ⇒ 1 credit

{% hint style="info" %}
Currently pricing is on a 1 to 1 ratio for all models — one page consumes one credit.
{% endhint %}

