---
description: >-
  Base model settings, model mutability, and legal requirements such as
  processing zone and document storage.
icon: sliders-up
---

# Model Settings

## Model Name and Cover Image

On the Model Settings page, you'll have the opportunity to modify the model name and the cover image.

Feel free to set them up so that the Model will be easy to find among all your other Models.

## Model ID

Every model has a unique ID which is generated at creation time.

{% hint style="info" %}
Model Templates in the Catalog do not have a Model ID.

The Model ID is generated when the Model is created from the Template. If two users create a Model from the same Template, each Model gets its own unique Model ID.
{% endhint %}

You will need the Model ID in order to [use the Mindee API](../integrations/api-overview.md).

In the Model Settings page, you can view and copy the Model ID.

The Mindee Support team may request the Model ID to diagnose issues and provide solutions.

## Processing Zone

{% include "../.gitbook/includes/model-processing-zone.md" %}

## Storage Policy

{% include "../.gitbook/includes/model-storage-policy.md" %}

## Copying the Model

It can be useful to copy an existing model for some types of workflows.

You can have a base "template" model that is not called directly, but is used to make derivative models. This way you can have a common base and then modify the Data Schema to account for different providers, geographies, downstream users, etc. Each of these derivative models would be a copy of the "template" model.

You can also us this as way for testing changes to a model. For example you can copy a model used in production, modify the copy, and test the modifications in staging. Once the modifications are tested successfully, switch production over to the new model.

## Locking the Data Schema

To prevent unintended changes once your model configuration is finalized, you have the option to lock it.

This is useful for ensuring that the model remains stable for production use.

{% hint style="warning" %}
Locking the Model is an **irreversible action**, you will **not** be able to unlock it afterwards.

**Note**: you can copy a locked model and modify the copy.
{% endhint %}

## Deleting the Model

You can delete a model at any time.

{% hint style="danger" %}
Deleting a model is an **irreversible action**, you will **never** be able to recover a deleted model!
{% endhint %}

