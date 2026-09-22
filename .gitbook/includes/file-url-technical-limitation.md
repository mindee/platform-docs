---
title: file-url-technical-limitation
---

An URL pointing to all [accepted files](../../integrations/technical-limitations.md#accepted-files) may be used, if it adheres to the [API file limits](../../integrations/technical-limitations.md#api-file-limits).

In addition, the source URL must adhere to the following rules:

* Secured using TLS (HTTPS).
* Publicly available using only the URL, no authentication _headers_.
* Authentication may be provided in the URL as query parameters: username+password or token.\
  For example, Amazon S3 signed URLs will work.
* Contents must be a binary file (raw bytes, **not** base64-encoded).
* File contents cannot be encrypted.
* The Mindee server will **not** follow redirections (HTTP 3xx).
