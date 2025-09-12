---
description: Add the full text content of your documents to the API response.
icon: file-lines
---

# Raw Text (Full OCR)

## Overview

By activating this feature, the full text content of the document will be extracted using OCR (Optical Character Recognition) technology.

The resulting content will be included in the API response.

In the response, each page will have its text content filled.

## Use Cases

Having access to the raw text can be particularly useful when:

* needing to save a copy of the text for your records
* perform searches within the text

## Activate Raw Text

### Activate Raw Text via API Calls

Check the [#optional-features-configuration](../../integrations/client-libraries-sdk/configure-the-client.md#optional-features-configuration "mention") section if using our [client-libraries-sdk](../../integrations/client-libraries-sdk/ "mention").

Otherwise, take a look at the [#post-v2-inferences-enqueue](../../integrations/api-reference.md#post-v2-inferences-enqueue "mention") section.

## Use the Raw Text Result

We highly recommend using our [client-libraries-sdk](../../integrations/client-libraries-sdk/ "mention"), as they include various functions for ease of processing.

Specifically for handling the raw text, take a look at the [#raw-text](../../integrations/client-libraries-sdk/process-the-response.md#raw-text "mention") section.

Otherwise, take a look at the [#get-v2-inferences-inference\_id](../../integrations/api-reference.md#get-v2-inferences-inference_id "mention") section.
