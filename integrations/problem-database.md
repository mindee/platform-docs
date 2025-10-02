---
description: Common error messages and their handling.
icon: hexagon-exclamation
---

# Error Handling

## Error Responses

All errors will contain the following information:

* Status: an HTTP status code.
* Detail: a human-readable description of the error.

## 4xx Errors - Client Errors

<table><thead><tr><th width="135">HTTP Status</th><th>Possible Reasons</th></tr></thead><tbody><tr><td>401</td><td><ul><li>Invalid API key. Make sure the key starts with <code>md_</code> and is <a href="api-keys.md">active</a>.</li></ul></td></tr><tr><td>402</td><td><ul><li>An optional feature is not in your plan.</li><li>Your subscription is either not active or exceeded limits.</li></ul></td></tr><tr><td>403</td><td><ul><li>You don't have access to the requested resource.</li></ul></td></tr><tr><td>404</td><td><ul><li>The requested resource does not exist.</li><li>The requested resource is not ready for use.</li></ul></td></tr><tr><td>422</td><td><ul><li>Wrong format for a UUID.</li><li>Invalid or empty file sent.</li><li>Missing Parameter in a request.</li></ul></td></tr><tr><td>429</td><td><ul><li>Too many requests. Wait a few seconds and try again.</li></ul></td></tr></tbody></table>

## 5xx Errors - Server Errors

<table><thead><tr><th width="135">HTTP Status</th><th>Possible Reasons</th></tr></thead><tbody><tr><td>500</td><td><ul><li>Failed to run the inference.</li><li>Failed to process the request.</li></ul></td></tr></tbody></table>
