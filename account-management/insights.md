---
icon: chart-column
---

# Insights

## Overview

The insights page allows you to view various data concerning your usage of the Mindee platform and API.

<figure><img src="../.gitbook/assets/Ekrankopio_20251208_205921.png" alt="Insights - general view" width="563"><figcaption></figcaption></figure>

## Accessing the Insights Page

1. Go to [app.mindee.com](https://app.mindee.com/)
2. On the left-hand menu, click on **Insights**

Or simply click here:

<a href="https://app.mindee.com/insights" class="button primary">Go to Insights page</a>

## Data Views

<div align="left"><figure><img src="../.gitbook/assets/Ekrankopio_20251208_204036.png" alt="Insights - data view selector"><figcaption></figcaption></figure></div>

The following data are available for viewing.

* Traffic: the number of calls and the number of pages processed.
* Processing Time: the average time requests take to process, in seconds.
* Errors: the number of processing (inference) errors.\
  Note: does not show user errors (HTTP 4xx).

## Data Filters

For all data views, the following filters are available.

#### Origin

Filter based on the origin of the request.

<div align="left"><figure><img src="../.gitbook/assets/Ekrankopio_20251208_204330.png" alt="Insights - filter data based on origin"><figcaption></figcaption></figure></div>

"Live Test" is when using the [live test](../models/live-test.md) functionality on the platform.

"API" is for any request made using an API key.

#### Date Range

Filter based on start and end dates.

<div align="left"><figure><img src="../.gitbook/assets/Ekrankopio_20251208_204353.png" alt=""><figcaption></figcaption></figure></div>

#### Group By

Only affects the visualization, group results by day, month, or year.

<div align="left"><figure><img src="../.gitbook/assets/Ekrankopio_20251208_204425.png" alt=""><figcaption></figcaption></figure></div>

#### API Key

Show all API keys or filter on a specific one.

<div align="left"><figure><img src="../.gitbook/assets/Ekrankopio_20251208_204442.png" alt=""><figcaption></figcaption></figure></div>

#### Options Used

Filter by [optional features](../models/optional-features/) activated in the call.

<div align="left"><figure><img src="../.gitbook/assets/Ekrankopio_20251208_204502.png" alt=""><figcaption></figcaption></figure></div>

3 states to choose:

* empty: no filter
* check mark: show only calls with the option **active**
* minus sign: show only calls with the option **inactive**
