---
title: sample-code-javascript-extraction
---

Requires Node.js ≥ 20. Node.js ≥ 22 is recommended.\
Requires the [Mindee Node.js client library](https://www.npmjs.com/package/mindee/) version **5.0.2** or greater.

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
const productParams = {
  modelId: modelId,

  // Options: set to `true` or `false` to override defaults

  // Enhance extraction accuracy with Retrieval-Augmented Generation.
  rag: undefined,
  // Extract the full text content from the document as strings.
  rawText: undefined,
  // Calculate bounding box polygons for all fields.
  polygon: undefined,
  // Boost the precision and accuracy of all extractions.
  // Calculate confidence scores for all fields.
  confidence: undefined,
};

// Load a file from disk
const inputSource = new mindee.PathInput({ inputPath: filePath });

// Send for processing
const response = await mindeeClient.enqueueAndGetResult(
  mindee.product.Extraction,
  inputSource,
  productParams,
);

// print a string summary
console.log(response.inference.toString());

// Access the result fields
const fields = response.inference.result.fields;
```
{% endcode %}

Also take a look at the [Processing Results](https://docs.mindee.com/integrations/client-libraries-sdk/quick-start#processing-the-results) documentation.
