---
icon: terminal
---

# Client Libraries / SDKs

Our client libraries are the preferred way of integrating with the Mindee platform.

Some useful tools are also provided, for example PDF processing and image compression.

You can use the client libraries to make API requests following the polling and webhook patterns.

All our client libraries are open-source (MIT license) and hosted on [GitHub](https://github.com/mindee).

## Installation Instructions

{% include "../../.gitbook/includes/installation-instructions.md" %}

## Basic Usage

To get started, take a look at the [quick-start.md](quick-start.md "mention")  page.

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
4. [process-the-result.md](process-the-result.md "mention")
   1. Optional: load from a webhook.

## Frequently Asked Questions

### Can I send requests in parallel?

Yes. All clients can be used to send requests in parallel.

The exact implementation is left to the user:

* For Node.js, you'll want to use asynchronous processing.
* For all others, you'll want to use threads or processes.

### Can I use the v1 and v2 APIs together?

Yes. Each client library has support for both v1 and v2 APIs.

You'll need to make a separate instance of the client classes:

* .NET and Java, use `MindeeClient` and `MindeeClientV2`
* all others, use `Client` and `ClientV2`

The code to make requests and to process results is **completely different** between v1 and v2.

We highly recommend having different files (or even modules) for handling each API version.

### Can I send only a specific page of a multi-page PDF?

Yes. All libraries have support for cutting/extracting PDF pages.

Check the [#pdf-page-manipulations](load-and-adjust-a-file.md#pdf-page-manipulations "mention") section.
