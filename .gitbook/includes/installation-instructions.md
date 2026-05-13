---
title: Installation Instructions
---

{% tabs %}
{% tab title="Python" %}
<code class="expression">space.vars.VERSIONS_PYTHON</code>

Simply install the [PyPi package](https://pypi.org/project/mindee/) using pip:

```sh
pip install -U mindee~=4.35
```
{% endtab %}

{% tab title="Node.js" %}
<code class="expression">space.vars.VERSIONS_NODE</code>

Simply install the [NPM package](https://www.npmjs.com/package/mindee):

```sh
npm install mindee@^5.1.1
```
{% endtab %}

{% tab title="PHP" %}
<code class="expression">space.vars.VERSIONS_PHP</code>

Simply install the [Packagist package](https://packagist.org/packages/mindee/mindee) using [composer](https://getcomposer.org/):

```sh
php composer.phar require "mindee/mindee:>=2.7"
```
{% endtab %}

{% tab title="Ruby" %}
<code class="expression">space.vars.VERSIONS_RUBY</code>

Simply install the [gem](https://rubygems.org/gems/mindee) using:

```shell
gem install mindee -v '~> 5.1'
```
{% endtab %}

{% tab title="Java" %}
<code class="expression">space.vars.VERSIONS_JAVA</code>

Group ID: `com.mindee.sdk`\
Artifact ID: `mindee-api-java`\
Version: ![](https://img.shields.io/maven-central/v/com.mindee.sdk/mindee-api-java?style=flat-square\&label=%20)

There are various installation methods, Maven, Gradle, etc:

[Installation Details](https://central.sonatype.com/artifact/com.mindee.sdk/mindee-api-java)
{% endtab %}

{% tab title=".NET" %}
<code class="expression">space.vars.VERSIONS_NET</code>

Simply install the [NuGet package](https://www.nuget.org/packages/Mindee) using .NET CLI:

```sh
dotnet add package Mindee --version 4.0
```
{% endtab %}
{% endtabs %}

Don't see support for your favorite language or framework? [Make a feature request!](https://feedback.mindee.com/?b=682f69c9e2404756e7e68d1c)
