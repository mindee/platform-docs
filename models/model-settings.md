---
icon: sliders-up
---

# Model Settings

## Model Name and Cover Image

On the Model Settings page, you'll have the opportunity to modify the model name and the cover image. Feel free to set them up so that the Model will be easy to retrieve among all your other Models.

## Processing Zone

This setting determines the geographic region of where your data is processed.

There are 3 available options for processing location:&#x20;

* Europe
* United States
* Global

Selecting **Global** means your data could be processed in Europe and/or the United States.

{% hint style="info" %}
This is only an indication for processing, not support.

You can send documents from any country to the Mindee API!
{% endhint %}

## Storage Policy

This section only applies when sending documents via API call.

### Retrieval Period

By default, extracted data (inferences) are stored for 12 hours after their completion.

During this time, you may make GET requests to retrieve the payload using its inference ID.

After this period, any calls to the inference ID will result in a 404 error.

You may adjust this period from between 1 to 24 hours.

### Immediate Deletetion

If "Delete extracted data when fetched" is checked, the inference will be deleted when either:&#x20;

* the inference is accessed using a GET request (usually when polling)
* the inference is successfully sent to your server via a [webhook](/integrations/webhooks.md)

The data will be deleted immediately regardless of the Retrieval Period setting.

Once the Retrieval Period is passed, the data will be deleted regardless of whether Immediate Deletion is activated.

Once the data are deleted, any calls to the inference ID will result in a 404 error.

## Locking the Data Schema

To prevent unintended changes once your data schema is finalized, you have the option to lock it. This ensures that the model remains stable and any modifications are controlled. You can unlock the data schema when changes are needed.

## Copying, Transferring, Deleting Models

These operations are available in the "Danger Zone" are of the model settings.

