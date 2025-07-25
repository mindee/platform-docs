---
icon: bolt-auto
---

# Automation (Confidence Score)

## Overview

The **Automation** feature in Mindee's platform represents a major step forward in enhancing both the **accuracy** and **reliability** of document data extraction. Designed to support robust and scalable automation workflows, this feature is built on two core capabilities:

1. **Enhanced accuracy** using model ensemble algorithms
2. **Confidence scoring** for all types of extracted fields

Automation aims to solve two common challenges in intelligent document processing:

* **Maximizing extraction quality** in the face of variable and noisy document formats
* **Providing actionable trust signals** so that systems can handle uncertain extractions appropriately

By combining multiple models and analyzing their agreement, Automation ensures that the most reliable prediction is selected for each field, while transparently communicating how confident the system is in that prediction.

## Use Cases

### Full Automation

By leveraging **confidence score thresholds**, you can selectively **automate decisions** in your processing pipeline, triggering downstream actions only when extractions meet a predefined reliability level.&#x20;

For example, fields marked with a `High` or `Certain` confidence score can be automatically approved and pushed to your ERP or CRM system, while extractions with `Low` or `Medium` confidence can be routed for human review or fallback logic. This selective gating mechanism allows teams to implement **fully automated flows** for clean, predictable documents, while still handling edge cases gracefully.

#### **Use cases examples**:

* Auto-validating invoice totals and tax fields before ingestion into an accounting system
* Auto-approving identity document extractions for KYC when confidence is high
* Automatically flagging low-confidence vendor names or dates for manual verification

### Efficient human validation

To make confidence levels easily understood by end-users, each confidence score returned by Automation can be associated with a **color-coded indicator**.\
This visual feedback is especially useful in UI-driven workflows, where operators need to scan, validate, or correct extractions quickly.

The default color scheme is as follows:

| Confidence Level | Label            | Color Code | Suggested Action         | Description                                                              |
| ---------------- | ---------------- | ---------- | ------------------------ | ------------------------------------------------------------------------ |
| 🟥 Low           | `Low`            | Red        | Manual review required   | Extraction is uncertain or likely incorrect. Model disagreement is high. |
| 🟧 Medium        | `Medium`         | Orange     | Optional review          | Some confidence, but context or format may impact correctness.           |
| 🟩 High          | `High`           | Green      | Can be auto-processed    | Model consensus is strong; prediction is likely accurate.                |
| 🟦 Certain       | `Certain` (soon) | Blue       | Safe for full automation | Full confidence, human-level precision                                   |

This color-coding system allows product teams to **highlight uncertainty directly in the user interface**, enabling faster decisions, reducing cognitive load, and streamlining exception handling.&#x20;

## How to Activate Automation

{% hint style="info" %}
**Automation** is only available to users with an active **Business** subscription.
{% endhint %}

{% hint style="warning" %}
When the **Automation** feature is not activated, the `confidence` key in the JSON response will always be set to `null`.
{% endhint %}

1.  Once [connected to the platform](https://app.mindee.com), open one of your models, navigate to the **Data Schema** section, and click on the **Options** tab.

    <figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>
2. Here you can **switch on the toggle** "Include Confidence Score for automation".&#x20;
3.  Go to the live test and drop a document for testing it.\


    <figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>
4. In the JSON response, you can now see that the `confidence` key is set to `"High"`, `"Medium"`, or `"Low"`. Another level of confidence `"Certain"` will be released soon.&#x20;

## Towards 100% automation

By combining confidence-based automation with Mindee’s **RAG-powered continuous learning loop**, you can drive your workflows toward **near 100% automation**.&#x20;

Low-confidence extractions are not only flagged for human validation, but also used as feedback signals to refine models dynamically, through retrieval-augmented generation and targeted retraining.&#x20;

This creates a virtuous cycle where every uncertain case contributes to future accuracy improvements, progressively reducing manual intervention and expanding the scope of trusted predictions.

## Frequently asked questions

### How is the confidence score computed?

The confidence score in Automation is a consensus-based reliability measure, not a simple probability. It is computed by analyzing the level of agreement between multiple models, each trained independently or with complementary strategies, on the same document field.

When these models produce matching or highly similar predictions, the confidence is high. When they disagree significantly, the confidence drops. On top of that, a dedicated arbitration and correction model acts as a referee: it takes all predictions, compares their structural and semantic coherence, and assigns a final confidence level (`low`, `medium`, `high`, or soon `certain`).

### Does Automation introduce additional latency?

Yes, Automation introduces some additional latency, but in most cases, it remains minimal. This is because the ensemble of models used for prediction is executed in parallel, which allows us to keep response times close to those of a single-model pipeline.

However, depending on the number and complexity of models involved, or the document type, the latency can occasionally be a few times longer than a standard call. The tradeoff is intentional: slightly longer processing time in exchange for higher accuracy and richer metadata, including the confidence score.

### What should I do with low confidence extractions?

We recommend routing `Low` (and optionally `Medium`) confidence extractions to a human validation layer, or using fallback logic (e.g., default values, user input). These extractions are also ideal candidates for feedback-driven improvement via our continuous learning loop using the RAG feature.

### Does Automation work with any type of documents or fields?

Automation is fully compatible with all document types and extracted fields supported by Mindee.\
Every extracted field,  whether it's a piece of text, a number, a date, an amount, or any other data type, benefits from the same ensemble evaluation and confidence scoring logic. This consistent approach ensures a uniform and predictable developer experience, regardless of the document format or use case.

Moreover, nested objects and arrays of objects (e.g., `line_items` in invoices or tables in receipts) also receive individual confidence scores per field, enabling fine-grained control over complex data structures.
