---
title: file-url-technical-limitation
---

The source URL must adhere to the following rules:

* Secured using TLS (HTTPS).
* Publicly available using only the URL, no authentication _headers_.
* Authentication may be provided in the URL as query parameters: username+password or token.\
  For example, Amazon S3 signed URLs will work.
* Contents must be a binary file (raw bytes, **not** base64-encoded).
* File contents cannot be encrypted, PDFs must not be password protected.
* The Mindee server will **not** follow redirections (HTTP 3xx).
