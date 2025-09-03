---
title: Installation Instructions
---

{% tabs %}
{% tab title="Python" %}
Requires Python ≥ 3.9.\
Python ≥ 3.10 is highly recommended.

Simply install the [PyPi package](https://pypi.org/project/mindee/) using pip:

```sh
pip install mindee>=4.28.1
```
{% endtab %}

{% tab title="Node.js" %}
Requires Node.js ≥ 20.\
Node.js ≥ 22 is recommended.

Simply install the [NPM package](https://www.npmjs.com/package/mindee):

```sh
npm install mindee@4.29.0
```
{% endtab %}

{% tab title="PHP" %}
Requires PHP ≥ 8.0.\
PHP ≥ 8.3 is recommended.

Simply install the [Packagist package](https://packagist.org/packages/mindee/mindee) using [composer](https://getcomposer.org/):

```sh
php composer.phar require "mindee/mindee:>=1.23"
```

If you get an error message like this:

```
found mindee/mindee[v1.23.0-rc2] but it does not match your minimum-stability.
```

You'll need to configure your composer settings to allow installing an RC version:

```sh
php composer.phar config minimum-stability RC
php composer.phar config prefer-stable true
```
{% endtab %}

{% tab title="Ruby" %}
Requires Ruby ≥ 3.0.\
Simply install the [gem](https://rubygems.org/gems/mindee/versions/4.7.0.pre.rc1) using:

```shell
gem install mindee --pre
```
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

Simply install the [NuGet package](https://www.nuget.org/packages/Mindee/3.29.0-rc4) using .NET CLI:

```sh
dotnet add package Mindee --version 3.32
```
{% endtab %}
{% endtabs %}

Don't see support for your favorite language or framework? [Make a feature request!](https://feedback.mindee.com/?b=682f69c9e2404756e7e68d1c)
