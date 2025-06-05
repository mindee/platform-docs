---
icon: code
---

# API Reference



{% hint style="warning" %}
**You'll need your Model ID and an API key to use the API.**
{% endhint %}

{% hint style="info" %}
Take a look at the [api-overview.md](api-overview.md "mention") if you are setting up your integration for the first time.
{% endhint %}

{% openapi-operation spec="mindee-api" path="/v2/inferences/enqueue" method="post" %}
[OpenAPI mindee-api](https://gitbook-x-prod-openapi.4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/raw/71f19d7d67027571545f84090cd8c03d7cb9f96c542e4c7ff3224891df25893d.txt?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20250620%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20250620T164049Z&X-Amz-Expires=172800&X-Amz-Signature=d1ec48ce868dcac428be5974ce9cd4d8eaa689727b27ce23c5453d3fb7094618&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

{% openapi-operation spec="mindee-api" path="/v2/jobs/{job_id}" method="get" %}
[OpenAPI mindee-api](https://gitbook-x-prod-openapi.4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/raw/71f19d7d67027571545f84090cd8c03d7cb9f96c542e4c7ff3224891df25893d.txt?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20250620%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20250620T164049Z&X-Amz-Expires=172800&X-Amz-Signature=d1ec48ce868dcac428be5974ce9cd4d8eaa689727b27ce23c5453d3fb7094618&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

{% openapi-operation spec="mindee-api" path="/v2/inferences/{inference_id}" method="get" %}
[OpenAPI mindee-api](https://gitbook-x-prod-openapi.4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/raw/71f19d7d67027571545f84090cd8c03d7cb9f96c542e4c7ff3224891df25893d.txt?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20250620%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20250620T164049Z&X-Amz-Expires=172800&X-Amz-Signature=d1ec48ce868dcac428be5974ce9cd4d8eaa689727b27ce23c5453d3fb7094618&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

{% openapi-webhook spec="mindee-api" name="inference-processed" method="post" %}
[OpenAPI mindee-api](https://gitbook-x-prod-openapi.4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/raw/71f19d7d67027571545f84090cd8c03d7cb9f96c542e4c7ff3224891df25893d.txt?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20250620%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20250620T164049Z&X-Amz-Expires=172800&X-Amz-Signature=d1ec48ce868dcac428be5974ce9cd4d8eaa689727b27ce23c5453d3fb7094618&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-webhook %}
