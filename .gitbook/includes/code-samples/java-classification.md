---
title: code-sample-java-classification
---

Requires Java ≥ 8. Java ≥ 11 recommended.\
Requires the [Mindee Java client library](https://central.sonatype.com/artifact/com.mindee.sdk/mindee-api-java) version **4.43.0** or greater.

```java
import com.mindee.MindeeClientV2;
import com.mindee.input.LocalInputSource;
import com.mindee.v2.product.classification.ClassificationClassifier;
import com.mindee.v2.product.classification.ClassificationResponse;
import com.mindee.v2.product.classification.ClassificationResult;
import com.mindee.v2.product.classification.params.ClassificationParameters;
import java.io.IOException;

public class SimpleMindeeClientV2 {

  public static void main(String[] args)
      throws IOException, InterruptedException
  {
    String apiKey = "MY_API_KEY";
    String filePath = "/path/to/the/file.ext";
    String modelId = "MY_MODEL_ID";

    // Init a new client
    MindeeClientV2 mindeeClient = new MindeeClientV2(apiKey);

    // Set inference parameters
    // Note: modelId is mandatory.
    ClassificationParameters classificationParams = ClassificationParameters
        // ID of the model, required.
        .builder(modelId)
        .build();

    // Load a file from disk
    LocalInputSource inputSource = new LocalInputSource(filePath);

    // Send for processing using polling
    ClassificationResponse response = mindeeClient.enqueueAndGetResult(
        ClassificationResponse.class,
        inputSource,
        classificationParams
    );

    // Print a summary of the response
    System.out.println(response.getInference().toString());

    // Access the classification result
    ClassificationResult result = response.getInference().getResult();
    ClassificationClassifier classification = result.getClassification();
  }
}

```

Also take a look at the [Processing Results](https://docs.mindee.com/integrations/client-libraries-sdk/quick-start#processing-the-results) documentation.
