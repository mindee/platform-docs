---
icon: handshake-simple
---

# Manual Integration

{% hint style="info" %}
We **do not recommend** manually integrating the Mindee API.

Recommended integrations:

* [client-libraries-sdk](client-libraries-sdk/ "mention")
* [no-code-integrations](no-code-integrations/ "mention")

Also take a look at the [api-overview.md](api-overview.md "mention") if you are setting up your integration for the first time.
{% endhint %}

{% hint style="info" %}
**You'll need your Model ID and an** [**API key**](api-keys.md) **to use the API.**
{% endhint %}



If you would like to download the OpenAPI specification directly, it is available here:\
[https://api-v2.mindee.net/openapi.json](https://api-v2.mindee.net/openapi.json)

{% openapi-operation spec="mindee-api" path="/v2/inferences/enqueue" method="post" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-operation %}

Here is a working example of the built-in test client:

<figure><img src="../.gitbook/assets/api-example_post-inference.png" alt=""><figcaption></figcaption></figure>

{% openapi-operation spec="mindee-api" path="/v2/jobs/{job_id}" method="get" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-operation %}

{% openapi-operation spec="mindee-api" path="/v2/inferences/{inference_id}" method="get" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-operation %}

{% openapi-webhook spec="mindee-api" name="inference-processed" method="post" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-webhook %}
