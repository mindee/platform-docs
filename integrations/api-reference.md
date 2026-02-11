---
description: Manual integration - reference only.
noRobotsIndex: true
icon: handshake-simple
---

# Manual Integration

{% hint style="warning" %}
**We do not recommend manually integrating**, and cannot guarantee full support in this case.
{% endhint %}

{% hint style="success" %}
**Recommended integrations:**

* [client-libraries-sdk](client-libraries-sdk/ "mention")
* [no-code-integrations](no-code-integrations/ "mention")

Also take a look at the [api-overview.md](api-overview.md "mention") if you are setting up your integration for the first time.
{% endhint %}

If you would like to download the OpenAPI specification directly, it is available here:\
[https://api-v2.mindee.net/openapi.json](https://api-v2.mindee.net/openapi.json)

{% openapi-operation spec="mindee-api" path="/v2/products/extraction/enqueue" method="post" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-operation %}

Here is a working example of the built-in test client:

<figure><img src="../.gitbook/assets/api-example_post-inference.png" alt=""><figcaption></figcaption></figure>

{% openapi-webhook spec="mindee-api" name="extraction-processed" method="post" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-webhook %}

{% openapi-operation spec="mindee-api" path="/v2/jobs/{job_id}" method="get" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-operation %}

{% openapi-operation spec="mindee-api" path="/v2/products/extraction/results/{inference_id}" method="get" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-operation %}
