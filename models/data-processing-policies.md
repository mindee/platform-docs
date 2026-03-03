---
description: >-
  Mindee provides flexible options to help you manage how and where your
  document data is processed, stored, and deleted.
icon: lock
---

# Data Processing Policies

The following features help ensure compliance with your regional regulations and allow control over data retention and privacy.

## Processing Zone

{% include "../.gitbook/includes/model-processing-zone.md" %}

## Storage Policy

{% include "../.gitbook/includes/model-storage-policy.md" %}

## Best Practices

* **For testing and setup:** Use a longer Storage Duration (up to 24 hours) to allow time to check and validate processed results. This is particularly useful when setting up a webhook workflow.
* **For general production use:** Set a relatively short Storage Duration (3-5 hours).
* **For maximum privacy:** Always enable **Delete When Fetched.** Best to also set a short Storage Duration (1 hour) in case of failed calls (i.e. network failure on GET).
* **For compliance:** Select the Processing Zone that matches your legal and regulatory requirements.

### Example Configuration

* **Processing Zone**: Europe
* **Storage Duration**: 4 hours
* **Delete When Fetched**: Enabled

With this setup, all documents are processed in EU data centers, results are stored for a maximum of 4 hours, and deleted automatically once you first download them.

## **How to change your model Data Processing Policy?**

{% include "../.gitbook/includes/feature-availability.md" %}

{% hint style="info" %}
**Important**: Once selected, your choice of processing zone applies only to this specific model.
{% endhint %}

{% @supademo/embed url="https://app.supademo.com/demo/cmevfnfze75icv9kqgqida892" demoId="cmevfnfze75icv9kqgqida892" %}
