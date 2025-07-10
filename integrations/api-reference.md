---
icon: code
---

# API Reference



{% hint style="warning" %}
**You'll need your Model ID and an API key to use the API.**
{% endhint %}

{% hint style="info" %}
Take a look at the [api-overview](api-overview/ "mention") if you are setting up your integration for the first time.
{% endhint %}

{% openapi-operation spec="mindee-api" path="/v2/inferences/enqueue" method="post" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-operation %}

{% openapi-operation spec="mindee-api" path="/v2/jobs/{job_id}" method="get" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-operation %}

{% openapi-operation spec="mindee-api" path="/v2/inferences/{inference_id}" method="get" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-operation %}

{% openapi-webhook spec="mindee-api" name="inference-processed" method="post" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-webhook %}
