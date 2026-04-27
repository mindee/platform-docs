---
description: >-
  For quick testing you can use the integrated CLI tools that ship with the
  Client Libraries.
icon: rectangle-terminal
---

# Command Line Tools (CLI)

All our APIs are asynchronous, as a result it's not very practical to use cURL or equivalent for quick testing.

For this reason the Client Libraries include a Command Line Interface (CLI) to allow for quick testing and debugging of your models.

{% tabs %}
{% tab title="Python" %}
```bash
# Install the library
pip install mindee

# General help
mindeeV2 --help

# Help for extraction models
mindeeV2 extraction --help

# Run extraction on a file
#   --key: API key, you can instead `export MINDEE_V2_API_KEY=md_XXXXXXXXXXXX`
#   --model: Your model ID
#   Positional arg: Absolute path to the file
mindeeV2 extraction \
  --key md_XXXXXXXXXXXX \
  --model abcd1234-aa11-bb22-cc33-abcdef1234567 \
  /path/to/the/file.pdf
```
{% endtab %}

{% tab title="Node.js" %}
```shellscript
# Install the library
npm install mindee

# General help
./node_modules/.bin/mindeeV2 --help

# Help for extraction models
./node_modules/.bin/mindeeV2 extraction --help

# Run extraction on a file
#   --api-key: API key, you can instead `export MINDEE_V2_API_KEY=md_XXXXXXXXXXXX`
#   --model: Your model ID
#   Positional arg: Absolute path to the file
./node_modules/.bin/mindeeV2 extraction \
  --api-key md_XXXXXXXXXXXX \
  --model abcd1234-aa11-bb22-cc33-abcdef1234567 \
  /path/to/the/file.pdf
```
{% endtab %}

{% tab title="Ruby" %}
Coming Soon
{% endtab %}

{% tab title="PHP" %}
Coming Soon
{% endtab %}

{% tab title="Java" %}
Coming Soon
{% endtab %}

{% tab title=".NET" %}
First install the CLI package: [https://www.nuget.org/packages/Mindee.Cli](https://www.nuget.org/packages/Mindee.Cli)

Note: this is a separate package from the general Mindee Client Library.

```bash
# General help
Mindee.Cli --help

# Help for extraction models
Mindee.Cli extraction --help

# Run extraction on a file
#   --api-key: API key, you can instead `export MINDEE_V2_API_KEY=md_XXXXXXXXXXXX`
#   --model-id: Your model ID
#   Positional arg: Absolute path to the file
Mindee.Cli extraction \
  --key md_XXXXXXXXXXXX \
  --model-id abcd1234-aa11-bb22-cc33-abcdef1234567 \
  /path/to/the/file.pdf
```
{% endtab %}
{% endtabs %}



{% hint style="info" %}
We are still working hard to make the CLI utilities more complete and useful.\
**As a result, the interface is not yet considered stable, and may be subject to change.**



If you have any ideas to improve them, [make a feature request!](https://feedback.mindee.com/?b=682f69c9e2404756e7e68d1c)
{% endhint %}
