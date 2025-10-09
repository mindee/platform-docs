---
description: Integrating Mindee in make.com scenarios.
hidden: true
---

# make.com Scenarios

{% hint style="info" %}
Only use the official **Mindee V2** app.

Community apps only work for Mindee V1.
{% endhint %}

## Add Mindee to a Make.com Scenario

You can use the Mindee app in any make.com scenario.

When adding a module, search for "mindee" and select **Mindee V2**:

<figure><img src="../../.gitbook/assets/make_select-app.png" alt="add Mindee V2 to make.com" width="563"><figcaption><p>Adding Mindee V2 to a scenario. Make sure to use the "verified" version.</p></figcaption></figure>

The Mindee V2 app has several possible modules, choose "Enqueue and Retrieve an Inference".

You may need to click on "Show more" to access it.

The other modules are for specific requirements and are not recommended for general usage.

<figure><img src="../../.gitbook/assets/make_select-enqueue-retrieve.png" alt="Selecting &#x22;Enqueue and Retrieve an Inference&#x22; in make.com scenario" width="563"><figcaption></figcaption></figure>

Once you have the "Enqueue and Retrieve an Inference" module in your scenario, you'll need to connect it to your [API key](../api-keys.md).

For this, click on the "Create a connection" button:

<figure><img src="../../.gitbook/assets/make_create-connection.png" alt="opening the Mindee V2 connection creation in make.com" width="563"><figcaption></figcaption></figure>

In the Create a connection dialog box, fill in the following information:

* A name for your connection, it should be in the format: `Mindeev2-` + your API key's name
* your API key

Finish by clicking "Save".

<figure><img src="../../.gitbook/assets/make_enter-connection-info.png" alt="mindee v2 connection info in make.com" width="563"><figcaption></figcaption></figure>

Now you can specify which model to use. For this click on "Search Model":

<figure><img src="../../.gitbook/assets/Screenshot_20251009_102507.png" alt="opening the search model for mindee v2 in make.com" width="563"><figcaption></figcaption></figure>

In the dialog window, you'll be able to enter a search string.

Enter in the name of the model you want to use and click "OK".

<figure><img src="../../.gitbook/assets/make_search-for-model.png" alt="search for Mindee v2 model in make.com" width="563"><figcaption></figcaption></figure>

If there is only one match to your search term, the model ID will be added.

If there are several matches to your search, choose the correct one from the list:

<figure><img src="../../.gitbook/assets/make_choose-model-from-list.png" alt="choosing a Mindee v2 model in make.com" width="563"><figcaption></figcaption></figure>

That's it, you're done! The Mindee V2 module is now ready to accept connections.

Click on "Save".

{% hint style="info" %}
**Do not fill in the "File" information in the Mindee V2 module.**

This is done automatically by connecting an appropriate module.
{% endhint %}
