---
hidden: true
noIndex: true
---

# Processing a Result

## Requirements

Before proceeding you'll need to have already [sent a file to the Mindee servers](processing-a-file.md) using a client library.

## Overview

## Load From Webhook

If you're using the webhook pattern, you'll need to use the payload sent to your Web server.

Reading the callback data will vary greatly depending on your HTTP server.

This is therefore beyond the scope of this example.

{% tabs %}
{% tab title="Python" %}
Assuming you're able to get the raw HTTP request via the variable `request` .

```python
from mindee import LocalResponse

local_response = LocalResponse(request.body())

# You can also load the json from a local path.
# local_response = LocalResponse("path/to/my/file.ext")

# Optional: verify the HMAC signature
# You'll need to get the "X-Mindee-Hmac-Signature" custom HTTP header.
hmac_signature = request.headers.get("X-Mindee-Hmac-Signature")
if not local_response.is_valid_hmac_signature(my_secret_key, hmac_signature):
    raise Error("Bad HMAC signature! Is someone trying to do evil?")

# Deserialize the response

result = mindee_client.load_prediction(
    product.InternationalIdV2,
    local_response
)
```
{% endtab %}
{% endtabs %}

## Extract Field Values

### Single-Value Fields

### Multiple-Value Fields (Objects)

### Looping over lists

