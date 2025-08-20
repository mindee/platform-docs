---
icon: vector-square
---

# Polygons (Bounding Boxes)

## Overview

The `polygons` parameter, also commonly referred to as **bounding boxes**, is an option you can select in your Models. \
It indicates the precise polygonal area on the document where the value for each extracted field was detected.

* These polygons define the **exact region on the document image** containing the extracted data.
* They enable visual verification by highlighting where the model found each value on the document.
* This feature is especially useful for building user interfaces that overlay extracted data on document images for validation or review.

## How It Works <a href="#how-it-works" id="how-it-works"></a>

* A polygon (bounding box) is an array of points outlining a closed shape around the detected data area.
* Points are given as normalized coordinates relative to the document page dimensions:
  * Each coordinate is a float between `0` and `1`.
  * `(0, 0)` corresponds to the top-left corner; `(1, 1)` corresponds to the bottom-right corner.
* Multiple polygons can be returned if there are several extracted fields or data areas.

## Example Polygon JSON Result <a href="#example-polygon-bounding-box-data" id="example-polygon-bounding-box-data"></a>

Here is an example of how the polygons parameter appears in the JSON response for a field named `date`:

```json
"fields": {
  "date": {
    "locations": [
      {
        "polygon": [
          [0.15, 0.35],
          [0.85, 0.35],
          [0.85, 0.30],
          [0.15, 0.30]
        ],
        "page": 0
      }
    ],
    "confidence": null,
    "value": "2000-01-01"
  }
  ...
}
```

* The `polygon` array defines a rectangular bounding polygon for the detected date value on page 0.
* Coordinates are normalized floats from 0 to 1, relative to the page dimensions.
* `locations` can contain multiple polygon/page objects if the field appears multiple times or on multiple pages.

## Use Cases <a href="#use-cases" id="use-cases"></a>

* Visual validation by overlaying bounding boxes on document previews for users to confirm extraction accuracy.
* Debugging extraction quality by analyzing detected regions.
* Enhancing UI with highlighted fields for better user experience.

## **How to activate Polygons?**&#x20;

{% hint style="info" %}
**Polygons** option is only available to users with an active **Pro** or **Business** subscription.
{% endhint %}

{% hint style="warning" %}
When the **Polygons** feature is not activated, the `locations` keys in the JSON response will always be set to an empty list.
{% endhint %}

{% @supademo/embed demoId="cmeidsob99f8xh3pybta14v42" url="https://app.supademo.com/demo/cmeidsob99f8xh3pybta14v42" %}
