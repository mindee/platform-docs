---
description: API reference for manually integrating Crop models.
---

# Crop Models

{% openapi-operation spec="mindee-api" path="/v2/products/crop/enqueue" method="post" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-operation %}

{% openapi-operation spec="mindee-api" path="/v2/jobs/{job_id}" method="get" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-operation %}

{% openapi-operation spec="mindee-api" path="/v2/products/crop/results/{inference_id}" method="get" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-operation %}

{% openapi-schemas spec="mindee-api" schemas="CropResponse-Output" grouped="true" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-schemas %}

{% openapi-webhook spec="mindee-api" name="crop-utility-processed" method="post" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-webhook %}
