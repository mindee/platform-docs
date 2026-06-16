---
description: Overview of connecting your system to the Mindee API.
icon: print-magnifying-glass
---

# Integration Overview

## General Description

Mindee is ideal for handling large amounts of documents. The vast majority of our users will want to connect Mindee to their systems using our APIs.

It's then possible to design any number of different use cases around document processing. These can be for purely internal processing or to provide final end users with a polished experience.

In this section we'll go over the major steps required for a successful integration, and link to the relevant sections of the documentation.

## Before Starting

You'll need at least one model configured, see the [models-overview.md](../models/models-overview.md "mention") section for more details. This can be any model type (extraction or utility model), all models are integrated in a very similar way.

We recommend using the [live-test.md](../models/live-test.md "mention") feature before attempting to integrate the API.

You'll also need at least one API key, see the [api-keys.md](api-keys.md "mention") section for more info.

## How to Integrate

All file processing routes are asynchronous, no synchronous routes are provided. You can either use a polling or webhook workflow.

If using our SDK integrations polling is abstracted away for you, meaning you can use a single synchronous method within the SDK to receive processing results.

These are are the fastest and easiest way to call our APIs, and allow our support teams to better help you.

### Client Libraries / SDKs

For a quick introduction and copy-paste ready code, look in the [quick-start.md](../extraction-models/sdk-integration/quick-start.md "mention") section.

{% hint style="success" %}
**Ask for Code Samples**

You can ask for specific code samples from the documentation AI.

Use the "Ask" button at the top of any page, or click below:

<button type="button" class="button primary" data-action="ask" data-query="List available model types and a brief description (Extraction, Split, Crop, Classify, OCR), allow to pick one. Then list available SDK languages and allow to pick one. Finally ask for model ID, and generate the code sample for polling." data-icon="gitbook-assistant">Ask "Write a code sample for me."</button>
{% endhint %}

Supported languages/frameworks: **Python**, **Node.js** (JS/TS), **PHP**, **Ruby**, **Java**, **.NET** (C#).

We provide full support for Client Libraries regardless of your plan. You can report any issues on our [bug tracker](https://feedback.mindee.com/?b=685c08afd7a1d2e47b124cbb) or directly on [GitHub](https://github.com/orgs/mindee/repositories).

### No-Code or Low-Code

If you're integrating using a no-code or low-code platform, take a look at the [no-code-integration](../extraction-models/no-code-integration/ "mention") section.

### Manual Integration

If none of the above options fit your requirements, take a look at the [api-reference](api-reference/ "mention") section.

{% hint style="warning" %}
**We do not recommend manually integrating**, and cannot guarantee full support.

Pro plans and above benefit from extended integration support.
{% endhint %}

## What to Send

You can send either a local file or an URL, it makes no difference for server-side processing.

However, when using our client libraries, you can [#adjust-the-source-file](client-libraries-sdk/load-and-adjust-a-file.md#adjust-the-source-file "mention") if you have it locally.

## How to Receive Results

Inference operations are always asynchronous, meaning there is a route to POST the file and another mechanism to retrieve the results.

You can decide on using either the polling flow or the webhook flow.

[polling-for-results.md](polling-for-results.md "mention") - uses a GET route, and is better suited for testing and small volumes.

[webhooks.md](webhooks.md "mention") - sends directly to your server, and is more suited for heavy production use.

## Developing and Testing

A typical release life cycle could look like this:

1. Start with a new model. If you are making adjustments to an existing production model, we recommend copying it and only making changes to the copy.\
   Consider adding versioning info to the copied model's name, i.e. "Invoices v1.1" or "Receipts 2026-05-17".
2. Adjust your code as needed and test.
3. When deploying your code to testing or production environments, use the new model's ID.
4. After deployment, [lock your production model](../models/model-settings.md#locking-the-data-schema) to avoid accidental changes.
5. `GOTO 1`



Note: we do not provide separate environments for development, staging, production, etc.
