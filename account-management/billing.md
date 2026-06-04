---
description: >-
  The Billing page in your Mindee account lets you manage your subscription and
  access past invoices.
icon: wallet
---

# Billing

## Overview

From the Billing page, you can:

* View your current plan
* Choose a new plan (upgrade or downgrade)
* Access your Stripe customer portal

## Access the Billing Page

1. Go to [app.mindee.com](https://app.mindee.com/)
2. On the left-hand menu, click on "<i class="fa-gear">:gear:</i> Settings"
3. Select the "Billing" tab

Or simply click here: <a href="https://app.mindee.com/settings?tab=billing" class="button primary">Go to Billing page</a>

Only `admin` and `owner` [users](organizations.md#team-members) can access and modify billing details.

## Change Your Plan

To change your plan:

1. Find the plan under the available options
2. Click on the "Downgrade" or "Upgrade" button at the bottom of the plan

## Stripe Customer Portal

To access your Stripe customer portal, click on the "Manage Subscription" button.

<figure><img src="../.gitbook/assets/billing-manage-subscription.png" alt="Manage Subscription button - access Stripe customer portal" width="563"><figcaption></figcaption></figure>

### Access Invoices

Your past invoices are available in the "Invoice History" section of your organization's billing page.

From there you can also pay any outstanding invoices and download payment receipts.

Note that only `owner` or `admin` members may access the Invoice History section, for other members it is not present on the page at all.

Additionally, you can download past invoices or pay any outstanding invoices from your Stripe account.

{% hint style="info" %}
Invoices are issued automatically at the start of each billing period.
{% endhint %}

### Set Your Tax ID

You can set your Tax ID at any time. After clicking on "Manage Subscription", click on "Update Information", and finally edit the "Tax ID" field.

## Supported Payment Methods

You can use any payment method supported by Stripe for all self-serve plans.

Among these, the most popular are credit and debit cards.

Custom payment options are available for Enterprise customers.

## Included Credits and Overages

Each plan includes monthly or yearly included credits depending on your subscription frequency. There is no service disruption if you exceed the included credits.

If you exceed the included credits in your plan, these additional credits will be charged according to the Overage Rate. These extra credits will be invoiced every €100, or at the end of your subscription.

| Plan     | Included Credits | Overage Rate                 |
| -------- | ---------------- | ---------------------------- |
| Starter  | 6,000 per year   | €0.05 per additional credit  |
| Pro      | 30,000 per year  | €0.04 per additional credit  |
| Business | 120,000 per year | €0.035 per additional credit |

{% hint style="info" %}
**Pages are calculated based on successfully processed documents.**

Client errors (HTTP 4xx) and processing errors will **not** count towards your page usage.
{% endhint %}

To track your page usage, you can consult the [insights.md](insights.md "mention") page.

Additionally, API responses contain the number of pages processed in the [#file-metadata](../integrations/client-libraries-sdk/process-the-response.md#file-metadata "mention") object.

Finally, you can be notified when your plan is reaching its limit by setting [#usage-alerts](organizations.md#usage-alerts "mention").

## Billing Frequency

You will be billed as soon as you complete your subscription payment online.

Payment is required upfront to access the platform and the features included in your plan.

Enterprise customers have access to different billing methods, please reach out to us directly.

## Frequently Asked Questions

### How do additional credit charges appear on the invoice?

Additional credit usage is itemized separately, on the invoice as "overage charges".

The invoice will show:

* your selected [plan](plans.md)'s base fee
* any additional credits consumed beyond your plan's included credits
* fee per credit
