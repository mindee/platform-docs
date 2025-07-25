---
title: sample-code-javascript
---

Requires Node.js ≥ 20. Node.js ≥ 22 is recommended.\
Requires the [Mindee Node.js client library](https://www.npmjs.com/package/mindee/v/4.29.0-rc1) version **4.29.0-rc3** or greater.

{% code lineNumbers="true" %}
```javascript
const mindee = require("mindee");
// for TS or modules:
// import * as mindee from "mindee";

// Init a new client
const mindeeClient = new mindee.ClientV2({ apiKey: "MY_API_KEY" });
const modelId = "MY_MODEL_ID";

// Load a file from disk
const inputSource = mindeeClient.docFromPath("/path/to/the/file.ext");
const params = {
  modelId: modelId,
  // If set to `true`, will enable Retrieval-Augmented Generation.
  rag: false
};

const apiResponse = mindeeClient.enqueueAndGetInference(
  inputSource,
  params
);

// Handle the response Promise
apiResponse.then((resp) => {
  // print a string summary
  console.log(resp.inference.toString());
});
```
{% endcode %}
