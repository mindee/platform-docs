---
description: >-
  Automatically parse driver licenses and extract structured driver data using
  the Driver License model template available in the Catalog.
icon: id-card
---

# Driver's License

Documentation for the data schema of the Driver's License model template.

This template can extract data from driver license documents issued by any country.

Some fields apply only to some countries or jurisdictions, if you have no need for these simply remove them. Conversely, you may need to add extra fields in order to support your specific business rules.

## Create Your Driver's License Model

* Click on "Create your document AI model" in your dashboard, then select **"DRiver's License"**.
* The Driver's License model template comes pre-configured with [standard fields](drivers-license.md#drivers-license-fields).
* Once your model is created, you can immediately [test](../../models/live-test.md) with your own documents.
* Optionally, you can adjust the model's [Data Schema](../../extraction-models/data-schema.md) if you need to modify fields.

## Driver's License Fields

{% include "../../.gitbook/includes/model-fields/drivers-license.md" %}
