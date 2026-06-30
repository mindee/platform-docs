---
description: Officially supported client libraries for integrating the Mindee platform.
icon: code
---

# Client Libraries / SDKs

By using the client libraries you'll be able to integrate faster and lower your maintenance costs.

Some useful tools are also provided, for example PDF processing and image compression.

You can use the client libraries to make API requests following the polling and webhook patterns.

All our client libraries are open-source (MIT license) and hosted on [GitHub](https://github.com/mindee).

Supported languages/frameworks: **Python**, **Node.js** (JS/TS), **PHP**, **Ruby**, **Java**, **.NET** (C#).

## Installation Instructions

{% include "../../.gitbook/includes/installation-instructions.md" %}

## Usage Details

Overall, the steps to using the Mindee service are:

1. [configure-the-client.md](configure-the-client.md "mention")
   1. Initialize the Mindee client.
   2. Set inference parameters, in particular the model ID to use.
2. [load-and-adjust-a-file.md](load-and-adjust-a-file.md "mention")
   1. Load a file from various supported sources: path, bytes, etc.
   2. _Optional_: adjust the source file before sending.
3. [send-a-file-or-url.md](send-a-file-or-url.md "mention")
   1. Send the file or an URL with the proper parameters.
4. [process-the-response.md](process-the-response.md "mention")
   1. Optional: load from a webhook.
   2. Optional: access document metadata
5. [extraction-result.md](../../extraction-models/sdk-integration/extraction-result.md "mention")
   1. Handle the field values extracted from the document
   2. Optional: access field metadata (polygons, confidence score)

## Frequently Asked Questions

<details>

<summary><strong>Can I send requests in parallel?</strong></summary>

Yes. All clients can be used to send requests in parallel.

The exact implementation is left to the user:

* For Node.js, you'll want to use asynchronous processing.
* For all others, you'll want to use threads or processes.

</details>

<details>

<summary><strong>Can I use the v1 and v2 APIs together?</strong></summary>

Yes. Each client library has support for both v1 and v2 APIs.

You'll need to make a separate instance of the client classes:

* .NET and Java, use `MindeeClient` and `MindeeClientV2`
* all others, use `Client` and `ClientV2`

The code to make requests and to process results is **very different** between v1 and v2.

We highly recommend having different files (or even modules) for handling each API version.

</details>

<details>

<summary><strong>Can I send only a specific page of a multi-page PDF?</strong></summary>

Yes. All libraries have support for cutting/extracting PDF pages.

For more information, consult: [#manipulate-pdf-pages](load-and-adjust-a-file.md#manipulate-pdf-pages "mention").

</details>

<details>

<summary><strong>How to stop PDFs with too many pages from being sent?</strong></summary>

**Do not use file size**, a text PDF with 200 pages can be smaller than a single photo.

Much more reliable to count the actual number of pages in the PDF document.

Use the built-in file metadata methods and properties to easily add business rules based on the number of pages (among other data).

For more information, consult: [#source-file-metadata](load-and-adjust-a-file.md#source-file-metadata "mention").

</details>

<details>

<summary><strong>I'm using a Supabase edge function, should I use the API directly?</strong></summary>

We recommend using the Mindee [Node.js client library](https://github.com/mindee/mindee-api-nodejs) in Supabase.

You can install it in your edge function(s) using `npm`.

</details>

<details>

<summary><strong>Which library features are officially supported?</strong></summary>

Anything documented here is officially supported and is considered stable for production use.

Anything in a library that is not documented here, is **not** officially supported and subject to change or removal.

</details>

<details>

<summary><strong>There is a bug with the SDK, how can I get help?</strong></summary>

If you are encountering a persistant issue, you should try first:

1. Asking the Docs Assistant for help
2. Asking your local agent for help by using one of our [SKILL files](../ai-coding-assistants.md#skill-files)

After this, if you determine (or are told) there is a problem with the SDK itself, the best bet would be to open a bug report on the relevant SDK's GitHub repository:

* **Python**: [https://github.com/mindee/mindee-api-python/issues](https://github.com/mindee/mindee-api-python/issues)
* **Node.js**: [https://github.com/mindee/mindee-api-nodejs/issues](https://github.com/mindee/mindee-api-nodejs/issues)
* **PHP**: [https://github.com/mindee/mindee-api-php/issues](https://github.com/mindee/mindee-api-php/issues)
* **Ruby**: [https://github.com/mindee/mindee-api-ruby/issues](https://github.com/mindee/mindee-api-ruby/issues)
* **Java**: [https://github.com/mindee/mindee-api-java/issues](https://github.com/mindee/mindee-api-java/issues)
* **.NET**: [https://github.com/mindee/mindee-api-dotnet/issues](https://github.com/mindee/mindee-api-dotnet/issues)

Our SDK engineers will be automatically notified of the new issue.

**Note:** Pro and above plans can contact our support teams directly.

</details>
