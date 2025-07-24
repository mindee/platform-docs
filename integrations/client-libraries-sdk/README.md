---
icon: terminal
---

# Client Libraries / SDK

Our client libraries are the preferred way of integrating with the Mindee platform.

They are the fastest and easiest way to call our APIs, and allow our support teams to better help you.

Some useful tools are also provided, for example PDF processing and image compression.

You can use the client libraries to make API requests following the polling and webhook patterns.

All our client libraries are open-source (MIT license) and hosted on [GitHub](https://github.com/mindee).

## Installation Instructions

{% tabs %}
{% tab title="Python" %}
Requires Python ≥ 3.9.\
Python ≥ 3.10 is highly recommended.

Typically the fastest way to get started is to install the [PyPi package](https://pypi.org/project/mindee/) using pip:

```
pip install mindee>=4.25.0
```
{% endtab %}

{% tab title="Node.js" %}
Requires Node.js ≥ 20.\
Node.js ≥ 22 is recommended.

Typically the fastest way to get started is to install the [NPM package](https://www.npmjs.com/package/mindee):

```
npm install mindee@">=4.29.0-rc1
```
{% endtab %}

{% tab title="Ruby" %}
[Planned](https://feedback.mindee.com/p/ruby-client-library)
{% endtab %}

{% tab title="PHP" %}
[In Progress](https://feedback.mindee.com/p/php-client-library)
{% endtab %}

{% tab title="Java" %}
Requires Java ≥ 8.\
Java ≥ 11 is highly recommended.

Group ID: `com.mindee.sdk` \
Artifact ID: `mindee-api-java` \
Version: ![](https://img.shields.io/maven-central/v/com.mindee.sdk/mindee-api-java?style=flat-square\&label=%20)

There are various installation methods, Maven, Gradle, etc:

[Installation Details](https://central.sonatype.com/artifact/com.mindee.sdk/mindee-api-java)
{% endtab %}

{% tab title=".NET" %}
Requires .NET ≥ 6.0.\
.NET ≥ 8.0 is recommended.

Install the [NuGet package](https://www.nuget.org/packages/Mindee/3.29.0-rc4) using .NET CLI:

```
dotnet add package Mindee --version 3.29.0-rc4
```
{% endtab %}
{% endtabs %}

Don't see support for your favorite language or framework? [Make a feature request!](https://feedback.mindee.com/?b=682f69c9e2404756e7e68d1c)

## Basic Usage

To get started, take a look at the [integrating-mindee.md](../../getting-started/integrating-mindee.md "mention") page.

## Usage Details

Overall, the steps to using the Mindee service are:

1. [configure-the-client.md](configure-the-client.md "mention")
   1. Initialize the Mindee client.
   2. Set inference parameters, in particular the model ID to use.
2. [send-a-file.md](send-a-file.md "mention")
   1. Load a file from various supported sources: path, bytes, etc.
   2. _Optional_: adjust the source file before sending.
   3. Send the file with the proper parameters.
3. [process-the-result.md](process-the-result.md "mention")
   1. Optional: load from a webhook.

