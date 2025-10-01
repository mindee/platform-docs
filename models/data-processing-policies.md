---
icon: lock
---

# Data Processing Policies

Mindee provides flexible options to help you manage how and where your document data is processed, stored, and deleted. This ensures compliance with regional regulations and gives you better control over data retention and privacy.

Below, you’ll find details on the configurable settings you can find **under each Model**:

## Processing Zone

The **Processing Zone** setting determines the geographic region where your document data will be processed. This option can impact compliance with data residency requirements (e.g., GDPR, CCPA).

Available options:

* **No Preference (Default)**\
  Mindee will automatically route your documents to the closest or most available processing region. This is the recommended default for optimal performance and availability, but your data may be processed in Europe and in the United States.
* **Europe**\
  Forces all data processing to occur exclusively within data centers located in Europe (EU). Recommended for organizations subject to GDPR or EU data residency policies.
* **United States**\
  Forces all data processing to occur exclusively within data centers located in the United States. Recommended for organizations subject to U.S. data governance or compliance policies.

{% hint style="info" %}
This is only an indication for processing, not support.

You can send documents from any country to the Mindee API!
{% endhint %}

{% include "/.gitbook/includes/model-storage-policy.md" %}

## Best Practices

* **For maximum privacy:** Set a **short Storage Duration** (1–2 hours) and enable **Delete When Fetched**.
* **For debugging or testing:** Use a longer Storage Duration (up to 24 hours) to allow time to re-check and validate processed results.
* **For compliance:** Always select the Processing Zone that matches your legal and regulatory requirements.

### Example Configuration

* **Processing Zone**: Europe
* **Storage Duration**: 4 hours
* **Delete When Fetched**: Enabled

With this setup, all documents are processed in EU data centers, results are stored for a maximum of 4 hours, and deleted automatically once you first download them.

## **How to change your model Data Processing Policy?**

{% include "../.gitbook/includes/feature-availability.md" %}

{% hint style="warning" %}
&#x20;**Important**: Once selected, your choice of processing zone applies only to this specific model.
{% endhint %}

{% @supademo/embed demoId="cmevfnfze75icv9kqgqida892" url="https://app.supademo.com/demo/cmevfnfze75icv9kqgqida892" %}
