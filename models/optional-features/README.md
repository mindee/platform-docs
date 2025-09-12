---
description: Optional model features to enhance document processing.
icon: lightbulb-gear
---

# Optional Features

## Overview

Models can have optional processing features activated depending on your requirements.

{% hint style="info" %}
Not all features are available on all plans.

Check the [#feature-comparison](../../account-management/plans.md#feature-comparison "mention") section for more information.
{% endhint %}

There are two ways of enabling and disabling features: on the Platform, or via API calls.

### Set Default Activation on the Platform

When setting the activation state of a feature on the Platform, this will be the default. All API calls will use the default state unless explicitly set otherwise.

This is useful for project managers, as it allows activating or deactivating a feature across all API calls on that model.

Anyone with write access to the model can set the option's default value.

### Set Activation During API Call

Default activation states may be overridden on a per-call basis via the API.

This is useful for developers for a variety of different scenarios, for example:

* local testing, comparing results on the same files with the feature active and inactive
* conditional activation of a feature based on business rules: document template, file origin, etc
* conditional activation of a feature based on your end-user's configuration
* etc ...

Anyone with access to the API (via an API Key) can enable or disable a feature when making an API call.

Details on setting features in the API: [#optional-features-configuration](../../integrations/client-libraries-sdk/configure-the-client.md#optional-features-configuration "mention")

## Available Features

* [improving-accuracy.md](improving-accuracy.md "mention")\
  Enhance extraction accuracy with Retrieval-Augmented Generation using your own documents.
* [automation-confidence-score.md](automation-confidence-score.md "mention") \
  🚀 Boost the precision and accuracy of all extractions.\
  Add a confidence score to each extracted field.
* [polygons-bounding-boxes.md](polygons-bounding-boxes.md "mention")\
  Add the polygon coordinates of each extracted field to the API response.
* [raw-text-full-ocr.md](raw-text-full-ocr.md "mention")\
  Add the full text content of your documents to the API response.
