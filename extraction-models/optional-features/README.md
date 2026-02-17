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

{% include "../../.gitbook/includes/default-optional-features.md" %}

### Set Activation During API Call

Default activation states may be overridden on a per-call basis via the API.

This is useful for developers for a variety of different scenarios, for example:

* local testing, comparing results on the same files with the feature active and inactive
* conditional activation of a feature based on business rules: document template, file origin, etc
* conditional activation of a feature based on your end-user's configuration
* etc ...

Anyone with access to the API (via an API Key) can enable or disable a feature when making an API call.

Details on setting features in the API: [#optional-features-configuration](../../integrations/client-libraries-sdk/configure-the-client.md#optional-features-configuration "mention")

## Available Extraction Features

{% include "../../.gitbook/includes/available-optional-features.md" %}
