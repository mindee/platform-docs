---
description: Common error messages and their handling.
hidden: true
noIndex: true
icon: hexagon-exclamation
---

# Error Handling

## Error Responses

All errors will contain the following information:

* Status: an HTTP status code.
* Detail: a human-readable description of the error.

## 4xx Errors - Client Errors

<table>
  <thead>
    <tr>
      <th width="159.5">HTTP Status</th>
      <th>Possible Reasons</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>401</td>
      <td>Invalid API key. Make sure the key starts with `md_`.</td>
    </tr>
    <tr>
      <td>402</td>
      <td>An optional feature is not in your plan.
      <br>Your subscription is either not active or exceeded limits.</td>
    </tr>
    <tr>
      <td>403</td>
      <td>You don't have access to the requested resource.</td>
    </tr>
    <tr>
      <td>404</td>
      <td>The requested resource does not exist.</td>
    </tr>
    <tr>
      <td>422</td>
      <td>Wrong format for a UUID.<br>Missing Parameter in a request.</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
    </tr>
  </tbody>
</table>
