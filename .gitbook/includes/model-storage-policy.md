## Storage Policy

The **Storage Policy** defines how long extracted data (i.e., the results of document processing) is retained in Mindee’s systems before being permanently deleted.

This section only applies when sending documents via API call.

### Storage Duration

* Defines the exact number of hours that extracted data is stored.
* **Default:** 12 hours
* **Minimum**: 1 hour
* **Maximum**: 24 hours

Data is automatically deleted as soon as the storage duration expires.

During this time, you may make GET requests to retrieve the payload using its inference ID.\
After this period, any calls to the inference ID will result in a 404 error.

This setting helps balance between accessibility of results for your workflow and minimizing retention for privacy and compliance.

### Delete Extracted Data When Fetched

When **disabled**, data will be retained until the configured **Storage Duration** elapses. **(Default)**

When **enabled**, extracted data is automatically and permanently deleted immediately after:&#x20;

* the inference is accessed using a GET request (usually when polling)
* the inference is successfully sent to your server via a [webhook](/integrations/webhooks.md)

The data will be deleted regardless of the Storage Period setting.

Once the Storage Period is passed, the data will be deleted regardless of whether this option is enabled.\
Once the data are deleted, any calls to the inference ID will result in a 404 error.

This option is recommended for workflows where you only need the extracted data once and do not require retrieval beyond the initial API call.
