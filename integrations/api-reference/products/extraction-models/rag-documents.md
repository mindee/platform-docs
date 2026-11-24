---
description: API management of RAG documents associated to a model.
icon: layer-group
layout:
  width: wide
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# RAG Documents

## Overview

The server side APIs are semi-asynchronous: a given route will respond immediately with the current data, but changes require the system some processing time to take effect. During this time the document will be in a transitive state.

## Routes

{% openapi-operation spec="mindee-api" path="/v2/products/extraction/rag-documents" method="post" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-operation %}

{% openapi-operation spec="mindee-api" path="/v2/products/extraction/rag-documents/{document_id}" method="get" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-operation %}

{% openapi-operation spec="mindee-api" path="/v2/products/extraction/rag-documents/{document_id}" method="patch" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-operation %}

{% openapi-operation spec="mindee-api" path="/v2/products/extraction/rag-documents/{document_id}" method="delete" %}
[OpenAPI mindee-api](https://api-v2.mindee.net/openapi.json)
{% endopenapi-operation %}
