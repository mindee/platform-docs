---
icon: vector-square
---

# Polygons (Bounding Boxes)

<figure><img src="../.gitbook/assets/image (4).png" alt="bounding-box polygons displayed in the Live Interface" width="375"><figcaption></figcaption></figure>

## Overview

The `polygons` parameter, also commonly referred to as **bounding boxes**, is an option you can select in your Models.\
It indicates the precise polygonal area on the document where the value for each extracted field was detected.

* These polygons define the **exact location on the document** containing the extracted data.
* They enable visual verification by highlighting where the model found each value on the document.
* This feature is especially useful for building user interfaces that overlay extracted data on document images for validation or review.

## How It Works <a href="#how-it-works" id="how-it-works"></a>

* A polygon (bounding box) is an array of points outlining a closed shape around the detected data area.
* Points are given as normalized coordinates relative to the document page dimensions:
  * Each coordinate is a float between `0` and `1`.
  * `(0, 0)` corresponds to the top-left corner; `(1, 1)` corresponds to the bottom-right corner.
* Multiple polygons can be returned if there are several extracted fields or data areas.

## **Activate Polygons**

{% include "../.gitbook/includes/feature-availability.md" %}

### Activate Polygons on the Platform UI

{% @supademo/embed demoId="cmeidsob99f8xh3pybta14v42" url="https://app.supademo.com/demo/cmeidsob99f8xh3pybta14v42" %}

### Activate Polygons via API Calls

Check the [#set-inference-parameters](../integrations/client-libraries-sdk/configure-the-client.md#set-inference-parameters "mention") section if using our [client-libraries-sdk](../integrations/client-libraries-sdk/ "mention").

Otherwise take a look at the [#post-v2-inferences-enqueue](../integrations/api-reference.md#post-v2-inferences-enqueue "mention") section.

## Use the Result <a href="#example-polygon-bounding-box-data" id="example-polygon-bounding-box-data"></a>

We highly recommend using our [client-libraries-sdk](../integrations/client-libraries-sdk/ "mention"), as they include various geometry functions for ease of processing.

Specifically for handling polygons, take a look at the [#locations](../integrations/client-libraries-sdk/process-result-fields.md#locations "mention") section.

Otherwise, take a look at the [#get-v2-inferences-inference\_id](../integrations/api-reference.md#get-v2-inferences-inference_id "mention") section.

## Some Use Cases <a href="#use-cases" id="use-cases"></a>

* Visual validation by overlaying bounding boxes on document previews for users to confirm extraction accuracy.
* Debugging extraction quality by analyzing detected regions.
* Enhancing UI with highlighted fields for better user experience.
