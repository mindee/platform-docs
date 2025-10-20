---
description: Integrating Mindee in Zapier zaps.
hidden: true
noIndex: true
---

# Zapier Zaps

## Add Mindee to a Zap <a href="#add-mindee-to-a-make.com-scenario" id="add-mindee-to-a-make.com-scenario"></a>

You can use the Mindee integration as a step in any zap.

When adding a step, search for "mindee" and select **Mindee OCR**:

— IMAGE —&#x20;

The Mindee integration has several possible actions, choose "Send File and Get Inference".

The other actions are for specific requirements and are not recommended for general usage.

— IMAGE —

Once you have the "Send File and Get Inference" action in your Zap, you'll need to connect it to one of your [api-keys.md](../api-keys.md "mention").

For this, click on the "select" button in the "Account" section:

— IMAGE —

Click on "Connect a new account".\
Then, in the connection dialog box, fill in the following information:

* A name for your connection, it should be in the format: `MindeeV2-` + your API key's name
* your [Mindee V2 API key](../api-keys.md#key-creation)

Finish by clicking on "Yes, Continue to Mindee OCR".

— IMAGE —

You can now click on "Continue" to configure the action.

First, click on "Model to Use", you'll then be given a list of models available in your organization\
Click the one that you want to use:

— IMAGE —

For the "File to Send", you'll need to connect to a valid file input.

Normally it will be a field called "File (Exists but not shown).\
As an example, here is what it looks like when connecting to a Drive folder:

<figure><img src="../../.gitbook/assets/zapier_select-file-to-use.png" alt="" width="374"><figcaption></figcaption></figure>

You can also set various options:

* "Alias" - Allows specifying an alias for the file name.\
  Useful for matching a document to your system, i.e. your purchase order ID for an invoice.
* "Polling Timeout" - The maximum number of seconds to attempt retrieving results, before stopping with an error. Increase this value if you are sending documents with many pages and are consistently getting timeout errors.
* For all other options, see the [optional-features](../../models/optional-features/ "mention") section.

