---
description: Managing and using Mindee API keys.
icon: key
---

# API Keys

## Overview

{% hint style="danger" %}
**Do not expose your API keys in any location that is open to the public.**

Anyone with the key will be able to make API requests linked to your organization.
{% endhint %}

An organization can have multiple API keys.

Each API Key grants access to all models within the organization.

Keys have an unlimited lifetime and must be manually revoked by deleting them.

### Key Creation

Before using the API, you'll need to create an API key.

To create an API Key on the Mindee Platform:

1. On the left-hand menu, click [**API Keys**](https://app.mindee.com/api-keys)
2. Click on the **Create API Key** button
3. Give a name to your key.\
   You'll typically want to name by environment, i.e. `dev`, `staging`, `prod`, \&c
4. Click **Create API**, you key is now ready for use.

### Key Revocation/Deletion

You can revoke a key at any time by deleting it.

Once a key is deleted, it can never be recovered.

Any calls to Mindee made using a deleted key will result in a HTTP 401 error code.

To delete a key on the Mindee Platform:

1. On the left-hand menu, click [**API Keys**](https://app.mindee.com/api-keys)
2. Next to each key is a **Delete** button, click it.
3. Click **Delete** in the confirmation dialog, your key is now revoked.
