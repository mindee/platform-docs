---
title: webhook-technical-limitations
---

Webhook URLs must adhere to the the following rules:

* Secured using TLS (HTTPS).
* Publicly available using only the URL, no authentication _headers_.
* Authentication may be provided in the URL as query parameters: username+password or token
* The Mindee server will **not** follow redirections (HTTP 3xx).
* The route should return OK (HTTP 2xx) when successful.
