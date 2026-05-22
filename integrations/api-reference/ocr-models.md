---
description: API reference for manually integrating OCR models.
---

# OCR Models

{% openapi-operation spec="mindee-api" path="/v2/products/ocr/enqueue" method="post" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-operation %}

{% openapi-operation spec="mindee-api" path="/v2/jobs/{job_id}" method="get" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-operation %}

{% openapi-operation spec="mindee-api" path="/v2/products/ocr/results/{inference_id}" method="get" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-operation %}

{% openapi-schemas spec="mindee-api" schemas="OCRResponse-Output" grouped="true" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-schemas %}

{% openapi-webhook spec="mindee-api" name="ocr-utility-processed" method="post" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-webhook %}
