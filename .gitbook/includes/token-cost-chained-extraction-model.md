---
title: token-cost-chained-extraction-model
---

You only consume tokens once, there is no double charge when chaining to an Extraction model.

The possible credit consumption scenarios are as follows:

* extraction model not chained ⇒ token usage of initial model (Split, Crop, Classification)
* extraction model chained ⇒ token usage of the configured extraction model, including any activated [optional features](../../extraction-models/optional-features/).

In other words, the initial model is provided at no additional cost to you if it triggers additional processing using an Extraction model.

All token consumption is per page as is standard for our models.
