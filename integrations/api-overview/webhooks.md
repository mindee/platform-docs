---
icon: webhook
---

# Webhooks

## Overview

Webhooks allow Mindee to post an inference result directly to your Web server.

It's recommended to use webhooks for heavy production use.

This page assumes you have experience setting up a Web server in your framework of choice.

If you're unsure, take a look at the [#rest-api-integration](./#rest-api-integration "mention") section before continuing.

## Platform Set Up

A webhook endpoint is a configuration that allows Mindee to POST to a given URL, and for you to specify when uploading a file.

Webhook endpoints are set up on a per-model basis. This allows you to set up a specific endpoint on your server for each model you have in your Mindee organization.

We **highly recommend** using a separate URL for each model, for ease of deserializing the inference payload. We will not be able to provide support if you send all models to the same URL.

### Creating an Endpoint

In the Mindee platform, navigate to your model by clicking on it from the "My Models" page.

Once in the model page, there will be a "<i class="fa-webhook">:webhook:</i> Webhooks" link in the left-hand menu, click it.

In the Webhooks page, there will be a "Add Webhook" button, clicking it opens a dialog allowing you to enter the name of the webhook, and the URL of your Web server:

* Choose any name that makes sense to you.
* The URL must be secured using TLS (HTTPS) and must be publicly accessible.

You can create any number of webhook endpoints.\
This is useful for example if you want to send to various different environments in your system (i.e. dev, staging, prod). This also allows for easy local testing.

Once you've entered in the required information, the endpoint will be present in the list of Webhook Endpoints.

There is a "Copy ID" button which will allow you to actually use the webhook in your API calls.

### Deleting an Endpoint

In your list of Webhook Endpoints, simply click on the trashcan icon "<i class="fa-trash-can">:trash-can:</i>" to delete an endpoint.

Any future attempts to use a deleted webhook will result in a HTTP error.

## Specifying on File Upload

When [enqueuing](../api-reference.md#post-v2-inferences-enqueue) an inference, simply specify the webhook endpoint ID(s) you would like to use.

The endpoint's ID is a UUID v4, and can be obtained by clicking on the "Copy ID" button in your list of Webhook Endpoints.

When POSTing the multipart form, use the `webhook_ids` parameter to specify the endpoints.

The parameter is a list, allowing to specify multiple endpoints:

```
webhook_ids=[ENDPOINT_1_UUID, ENDPOINT_2_UUID]
```

A single endpoint must also be sent as a list:

```
webhook_ids=[ENDPOINT_1_UUID]
```

Each endpoint in the given list will be sent the inference results.

## Local Testing

To test your integration locally, you can use open-source software like [rathole](https://github.com/rathole-org/rathole),  [frp](https://github.com/fatedier/frp), or [localtunnel](https://www.npmjs.com/package/localtunnel).

There are also proprietary solutions like [ngrok](https://ngrok.com/use-cases/webhook-testing).

## Loading an Inference

On your Web server, you'll need to have a handler for the URL you configured in the webhook endpoint.

Mindee will POST the inference results to this URL.

Processing the result is then a matter of loading the sent JSON payload from the Web server.

The payload is identical to a polling result and processing its contents is done in exactly the same way.

More details here: [processing-an-inference.md](../processing-an-inference.md "mention")

We **highly recommend** saving all received payloads to disk or a database before attempting to load the inference. We will not be able to provide support if you are not able to retrieve payloads after having received them.
