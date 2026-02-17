---
title: sample-code-javascript-crop
---

Requires Node.js ≥ 20. Node.js ≥ 22 is recommended.\
Requires the [Mindee Node.js client library](https://www.npmjs.com/package/mindee/) version **5.0.0-alpha2** or greater.

{% code lineNumbers="true" %}
```javascript
import * as mindee from "mindee";
// If you're on CommonJS:
// const mindee = require("mindee");

const apiKey = "MY_API_KEY";
const filePath = "/path/to/the/file.ext";
const modelId = "MY_MODEL_ID";

// Init a new client
const mindeeClient = new mindee.Client(
  { apiKey: apiKey }
);

// Set product parameters
const params = {
  modelId: modelId,
};

// Load a file from disk
const inputSource = new mindee.PathInput({ inputPath: filePath });

// Send for processing
const response = await mindeeClient.enqueueAndGetResult(
  mindee.product.Crop,
  inputSource,
  params,
);

// print a string summary
console.log(response.inference.toString());

// Access the result crops
const crops = response.inference.result.crops;
```
{% endcode %}

Also take a look at the [Processing Results](https://docs.mindee.com/integrations/client-libraries-sdk/quick-start#processing-the-results) documentation.
