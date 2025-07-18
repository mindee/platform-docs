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
Python 3.9 or greater is recommended.

Install the PyPi package using pip:

```
pip install mindee>=4.25.0
```

[Github Repository](https://github.com/mindee/mindee-api-python)
{% endtab %}

{% tab title="Node.js" %}
[In Progress](https://feedback.mindee.com/p/nodejs-jsts-client-library)
{% endtab %}

{% tab title="Ruby" %}
[Planned](https://feedback.mindee.com/p/ruby-client-library)
{% endtab %}

{% tab title="PHP" %}
[Planned](https://feedback.mindee.com/p/php-client-library)
{% endtab %}

{% tab title="Java" %}
Requires Java 8 or greater (11 recommended).

Group ID: `com.mindee.sdk` \
Artifact ID: `mindee-api-java` \
Version: ![](https://img.shields.io/maven-central/v/com.mindee.sdk/mindee-api-java?style=flat-square\&label=%20)

There are various installation methods, Maven, Gradle, etc:

[Installation Details](https://central.sonatype.com/artifact/com.mindee.sdk/mindee-api-java)
{% endtab %}

{% tab title=".NET" %}
Requires .NET 6.0 or greater.

Install the NuGet package using .NET CLI:

```
dotnet add package Mindee --version 3.29.0-rc3
```

[Github Repository](https://github.com/mindee/mindee-api-dotnet)
{% endtab %}
{% endtabs %}

Don't see support for your favorite language or framework? [Make a feature request!](https://feedback.mindee.com/)

## Usage

To get started, take a look at the [integrating-mindee.md](../getting-started/integrating-mindee.md "mention") page.

