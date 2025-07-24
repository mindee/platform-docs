# Processing a Result

## Requirements

Before proceeding you'll need to have already [sent a file to the Mindee servers](sending-a-file.md) using a client library.

## Overview

Depending on how you've sent the file, there are two ways of obtaining the result.

If you've sent via polling (or polling and webhook) you'll get the response directly in your method call.

If you've sent only via webhook, you'll receive the response on your Web server.

Here we'll go over how you can best process the results.

## Load From Webhook

If you're using the webhook pattern, you'll need to use the payload sent to your Web server.

Reading the callback data will vary greatly depending on your HTTP server.

This is therefore beyond the scope of this example.

{% tabs %}
{% tab title="Python" %}
Assuming you're able to get the raw HTTP request via the variable `request` .

```python
from mindee import LocalResponse, InferenceResponse

local_response = LocalResponse(request.body())

# You can also load the json from a local path.
# local_response = LocalResponse("path/to/my/file.ext")

# Optionally: verify the HMAC signature
# You'll need to get the "X-Signature" custom HTTP header.
hmac_signature = request.headers.get("X-Signature")
if not local_response.is_valid_hmac_signature(my_secret_key, hmac_signature):
    raise Error("Bad HMAC signature! Is someone trying to do evil?")

# Deserialize the response
result = local_response.deserialize_response(InferenceResponse)
```
{% endtab %}

{% tab title="Java" %}
Assuming you have a Web server instance `myHttpServer` .

```java

// Load the JSON string sent by the Mindee webhook POST callback.
//
// Reading the callback data will vary greatly depending on your HTTP server.
// This is therefore beyond the scope of this example.
String jsonData = myHttpServer.getPostBodyAsString();
LocalResponse localResponse = new LocalResponse(jsonData);

// Verify the HMAC signature.
// You'll need to get the "X-Signature" custom HTTP header.
String hmacSignature = myHttpServer.getHeader("X-Signature");
boolean isValid = localResponse.isValidHmacSignature(
    "obviously-fake-secret-key", hmacSignature
);
if (!isValid) {
    throw new MyException("Bad HMAC signature! Is someone trying to do evil?");
}

// You can also use a File object as the input.
//LocalResponse localResponse = new LocalResponse(new File("/path/to/file.json"));

// Deserialize the response into Java objects
InferenceResponse response = localResponse.deserializeResponse(
    InferenceResponse.class
);

// Print a summary of the parsed data
System.out.println(response.getDocument().toString());
```
{% endtab %}
{% endtabs %}

## Extract Field Values

Fields are dynamic depending on your model.

In the client library, you'll have access to the various fields as a mapping type.

Each field will then be one of the following types:

* A single value.
* Multiple values, an object.
* A list or array of fields.

{% hint style="info" %}
On the platform, you can specify date and classification types.

These are returned as strings.
{% endhint %}

### Single-Value Fields

Basic field type having a single value attribute.

Possible types: string, number (integer or floating-point), boolean.\
All types can be null.

### Multiple-Value Fields (Objects)

Each field can _theoretically_ be of any type (single, multi, list).\
**In practice:** we limit to a single value, meaning no recursive objects nor lists.

### Lists

Each item in the list can _theoretically_ be of any type (single, multi, list).\
**In practice:** we limit items to be either single or multi field, meaning no lists of lists.

