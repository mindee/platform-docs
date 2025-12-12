---
icon: chart-column
---

# Insights

## Overview

The insights page allows you to view various data concerning your usage of the Mindee platform and API.

<figure><img src="../.gitbook/assets/insights-overview.png" alt="Insights - general view" width="563"><figcaption></figcaption></figure>

## Accessing the Insights Page

1. Go to [app.mindee.com](https://app.mindee.com/)
2. On the left-hand menu, click on **Insights**

Or simply click here:

<a href="https://app.mindee.com/insights" class="button primary">Go to Insights page</a>

## Data Views

<div align="left"><figure><img src="../.gitbook/assets/insights-show-data.png" alt="Insights - data view selector"><figcaption></figcaption></figure></div>

### Traffic

The number of calls and the number of pages successfully processed.

This does not include calls that resulted in an error.

These requests count towards your plan's billing.

### Processing Time

The average time requests take to process, in seconds.

Processing time is calculated from when the request was received to when the inference was finished.

### Errors

The number of processing (inference) errors.

Does not include user errors (HTTP 4xx), since these requests get rejected before any processing takes place.

Errors do **not** count towards your plan's billing.

## Data Filters

For all data views, the following filters are available.

### Origin

Filter based on the origin of the request.

<div align="left"><figure><img src="../.gitbook/assets/insights-filter-origin.png" alt="Insights - filter data based on origin"><figcaption></figcaption></figure></div>

"Live Test" is when using the [live test](../models/live-test.md) functionality on the platform.

"API" is for any request made using an API key.

### Date Range

Filter based on start and end dates.

<div align="left"><figure><img src="../.gitbook/assets/insights-date-select.png" alt=""><figcaption></figcaption></figure></div>

### Group By

Only affects the visualization, group results by day, month, or year.

<div align="left"><figure><img src="../.gitbook/assets/insights-summarize.png" alt=""><figcaption></figcaption></figure></div>

### API Key

Show all API keys or filter on a specific one.

<div align="left"><figure><img src="../.gitbook/assets/insights-filter-api-key.png" alt=""><figcaption></figcaption></figure></div>

### Activated Options

Filter by [optional features](../models/optional-features/) activated in the call.

<div align="left"><figure><img src="../.gitbook/assets/insights-filter-options.png" alt=""><figcaption></figcaption></figure></div>

3 states to choose from:

* empty: no filter
* check mark: show only calls with the option **active**
* minus sign: show only calls with the option **inactive**
