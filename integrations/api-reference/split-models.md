---
description: API reference for manually integrating Split models.
---

# Split Models

{% openapi-operation spec="mindee-api" path="/v2/products/split/enqueue" method="post" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-operation %}

{% openapi-operation spec="mindee-api" path="/v2/jobs/{job_id}" method="get" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-operation %}

{% openapi-operation spec="mindee-api" path="/v2/products/split/results/{inference_id}" method="get" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-operation %}

{% openapi-schemas spec="mindee-api" schemas="SplitResponse-Output" grouped="true" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-schemas %}

{% openapi-webhook spec="mindee-api" name="split-utility-processed" method="post" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-webhook %}
