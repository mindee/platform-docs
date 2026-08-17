---
description: >-
  Mindee provides flexible options to help you manage how and where your
  document data is processed, stored, and deleted.
icon: lock
---

# Data Processing Policies

The following features help ensure compliance with your regional regulations and allow control over data retention and privacy.

## Processing Zone

{% include "../.gitbook/includes/feature-not-all-plans.md" %}

{% include "../.gitbook/includes/model-processing-zone.md" %}

## Storage Policy

{% hint style="success" %}
This feature is available on all plans.
{% endhint %}

{% include "../.gitbook/includes/model-storage-policy.md" %}

## Best Practices

* **For testing and setup:** Use a longer Storage Duration (up to 24 hours) to allow time to check and validate processed results. This is particularly useful when setting up a webhook workflow.
* **For general production use:** Set a relatively short Storage Duration (3-5 hours).
* **For privacy or Zero Data Retention:** Always enable **Delete When Fetched.** Best to also set a short Storage Duration (1 hour) in case of failed calls (i.e. network failure on GET).
* **For compliance:** Select the Processing Zone that matches your legal and regulatory requirements.

### Example Configuration

* **Processing Zone**: Europe
* **Storage Duration**: 4 hours
* **Delete When Fetched**: Enabled

With this setup, all documents are processed in EU data centers, results are stored for a maximum of 4 hours, and deleted automatically once you first download them.

## **Configure the Data Processing Policy**

{% include "../.gitbook/includes/feature-not-all-plans.md" %}

{% @supademo/embed url="https://app.supademo.com/demo/cmevfnfze75icv9kqgqida892" demoId="cmevfnfze75icv9kqgqida892" %}

## Frequently Asked Questions

<details>

<summary><strong>Does Mindee use my documents for training?</strong></summary>

No, all documents are the property of their organization and are not used for training Mindee models.

We only use your documents internally with your explicit knowledge and prior consent. Usage is limited to helping us resolve a ticket you opened with our support team.

</details>

<details>

<summary><strong>Are my documents or their data shared or sold to 3rd parties?</strong></summary>

No, never.

Documents and their data are only accessible to the users of the organization that the model belongs to.

Mindee never sells documents or their data to 3rd parties.

</details>

<details>

<summary><strong>Is Mindee GDPR &#x26; SOC 2 Type II compliant?</strong></summary>

Yes. Mindee V2 is fully GDPR-compliant and maintains its SOC 2 Type II certification, ensuring rigorous security controls, data protection standards, and transparency for enterprise needs.

</details>

<details>

<summary><strong>Can I request data deletion at any time?</strong></summary>

Yes. You can request full or partial data deletion at any time by using the deletion features available in your [model settings](model-settings.md#delete-the-model), [organization settings](../account-management/organizations.md#delete-organization), or [account settings](../account-management/account-settings.md#delete-account).

Mindee ensures that your data is securely and permanently removed upon request.

You can also contact our support team if you are unsure.

</details>

<details>

<summary><strong>Can you sign a BAA for HIPAA compliance?</strong></summary>

We can, however these agreements are limited to enterprise users.

If you have an enterprise plan, contact your dedicated account manager for more information.

</details>

