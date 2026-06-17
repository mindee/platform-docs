---
description: >-
  For quick testing you can use the integrated CLI tools that ship with the
  Client Libraries.
icon: rectangle-terminal
---

# Command Line Tools (CLI)

All our APIs are asynchronous, as a result it's not very practical to use cURL or equivalent for quick testing.

For this reason the SDKs include a Command Line Interface (CLI) to allow for quick testing and debugging of your models.

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
#   -k: API key, you can instead `export MINDEE_V2_API_KEY=md_XXXXXXXXXXXX`
#   -m: Your model ID
#   Positional arg: Absolute path to the file
mindeeV2 extraction \
  -k md_XXXXXXXXXXXX \
  -m abcd1234-aa11-bb22-cc33-abcdef1234567 \
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
#   -k: API key, you can instead `export MINDEE_V2_API_KEY=md_XXXXXXXXXXXX`
#   -m: Your model ID
#   Positional arg: Absolute path to the file
./node_modules/.bin/mindeeV2 extraction \
  -k md_XXXXXXXXXXXX \
  -m abcd1234-aa11-bb22-cc33-abcdef1234567 \
  /path/to/the/file.pdf
```
{% endtab %}

{% tab title="Ruby" %}
```bash
# General help
./bin/mindee.rb --help

# Help for extraction models
./bin/mindee.rb v2 extraction --help

# Run extraction on a file
#   -k: API key, you can instead `export MINDEE_V2_API_KEY=md_XXXXXXXXXXXX`
#   -m: Your model ID
#   Positional arg: Absolute path to the file
./bin/mindee.rb v2 extraction \
  -k md_XXXXXXXXXXXX \
  -m abcd1234-aa11-bb22-cc33-abcdef1234567 \
  /path/to/the/file.pdf
```
{% endtab %}

{% tab title="PHP" %}
Coming Soon
{% endtab %}

{% tab title="Java" %}
Use from the root of the [Git repository](https://github.com/mindee/mindee-api-java).

```bash
# Compile locally
mvn clean verify

# General help
./cli.sh --help

# Help for extraction models
./cli.sh extraction --help

# Run extraction on a file
#   -k: API key, you can instead `export MINDEE_V2_API_KEY=md_XXXXXXXXXXXX`
#   -m: Your model ID
#   Positional arg: Absolute path to the file
./cli.sh extraction \
  -k md_XXXXXXXXXXXX \
  -m abcd1234-aa11-bb22-cc33-abcdef1234567 \
  /path/to/the/file.pdf
```
{% endtab %}

{% tab title=".NET" %}
First install the CLI package: [https://www.nuget.org/packages/Mindee.Cli](https://www.nuget.org/packages/Mindee.Cli)

Note: this is a separate package from the general Mindee SDK.

```bash
# General help
Mindee.Cli --help

# Help for extraction models
Mindee.Cli extraction --help

# Run extraction on a file
#   -k: API key, you can instead `export MINDEE_V2_API_KEY=md_XXXXXXXXXXXX`
#   -m: Your model ID
#   Positional arg: Absolute path to the file
Mindee.Cli extraction \
  -k md_XXXXXXXXXXXX \
  -m abcd1234-aa11-bb22-cc33-abcdef1234567 \
  /path/to/the/file.pdf
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
We are still working hard to make the CLI utilities more complete and useful.\
**As a result, the interface is not yet considered stable, and may be subject to change.**

If you have any ideas to improve them, [make a feature request!](https://feedback.mindee.com/?b=682f69c9e2404756e7e68d1c)
{% endhint %}
