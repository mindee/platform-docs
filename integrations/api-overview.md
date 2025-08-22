---
description: General description of how to use the Mindee API.
icon: globe
---

# API Overview

## General Description

The Mindee API is RESTful, and returns data in a JSON format.

In this section we'll go over the major steps required for a successful integration, and link to the relevant sections of the documentation.

## Before Starting

You'll need at least one model configured, see the [models-overview.md](../models/models-overview.md "mention") section for more details.

We recommend using the [live-test.md](../models/live-test.md "mention") feature before attempting to integrate the API.

You'll also need at least one API key, see the [api-keys.md](api-keys.md "mention") section for more info.

## How to Integrate

We highly recommend using one of our [client-libraries-sdk](client-libraries-sdk/ "mention").

They are the fastest and easiest way to call our APIs, and allow our support teams to better help you.

You can also integrate directly by looking at our [api-reference.md](api-reference.md "mention") section.

## What to Send

You can send either a local file or an URL, it makes no difference for server-side processing.

However, when using our client libraries, you can [#adjust-the-source-file](client-libraries-sdk/load-and-adjust-a-file.md#adjust-the-source-file "mention") if you have it locally.

## How to Receive Results

You can decide on either the polling flow or the webhook flow.

[polling-for-results.md](polling-for-results.md "mention") is better suited to testing and small volumes.

[webhooks.md](webhooks.md "mention") are more suited to heavy production use.

## Ask for Code Samples

You can ask for specific code samples from the documentation AI.

Use the search bar at the top of the page.

