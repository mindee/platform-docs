---
noIndex: true
icon: passport
---

# Passport

Mindee enables automatic extraction of key identity fields from passport documents. Whether you are building a KYC process, onboarding flow, or document verification pipeline, our AI agent help you parse structured passport data with accuracy.

## Why Use Mindee for Passports?

Passports vary in format depending on the country, language, and issuance authority. Our AI agent simplifies extraction by letting you:

* Describe which fields matter to you
* Upload sample documents to refine extraction
* Get structured outputs without training models yourself

## What Can Be Extracted from a Passport?

Typical passport documents include a standard set of fields. Our AI agent can, for example, extract the following common fields for passports:

| Field             | Description                            |
| ----------------- | -------------------------------------- |
| Page Number       | Internal page number (if visible)      |
| Country Code      | Country of issuance                    |
| Identity Number   | Passport number                        |
| Given Name(s)     | First and middle names                 |
| Surname           | Last name                              |
| Date of Birth     | In the YYYY-MM-DD format               |
| Place of Birth    | City or region of birth                |
| Place of Issue    | Location where the passport was issued |
| Gender            | M / F / X                              |
| Issuance Date     | Passport issue date                    |
| Expiry Date       | Passport expiration date               |
| MRZ Row #1/Row #2 | Machine-readable zone lines            |

### Indian Passport Example

Indian passports include additional region-specific fields. If you're processing Indian passports, our technology is also able to extract, for example, those fields:

| Field                       | Description                                  |
| --------------------------- | -------------------------------------------- |
| Name of Legal Guardian      | Often the father’s name or guardian’s name   |
| Name of Spouse              | Appears if applicable                        |
| Name of Mother              | Optional field                               |
| Old Passport Number         | Prior document if applicable                 |
| Old Passport Date of Issue  | Issue date of prior passport                 |
| Old Passport Place of Issue | Location where the prior passport was issued |
| File Number                 | Government-issued file reference             |
| Address Line 1–3            | Full residential address                     |

{% hint style="info" %}
You can just upload an Indian passport and ask the agent to extract the fields present—it will learn from your input.
{% endhint %}

If you want to try and do a live test, here is a sample for Indian passport:

<figure><img src="../.gitbook/assets/indian-passport-sample.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/mindee-indian-passport.png" alt=""><figcaption></figcaption></figure>

## Two Ways to Start

### 1. **You Know the Fields You Need**

* Describe them directly to the AI agent (e.g., “I want the surname, date of birth, and MRZ”).
* Upload a sample passport if needed for clarification.
* The agent builds a tailored parser in minutes.

### 2. **You’re Not Sure What Fields You Need**

* Upload a sample document via the Mindee App.
* Ask the agent to show you **all extractable fields**.
* Explore and refine until you're satisfied.

This option is perfect if you're working with a new document format or you're still designing your data model.

## Document Format

* Most passports are one-page scans (photo page only)
* Additional pages (like addresses or old passport info) can be added if needed
* The AI agent supports both **single-page and multi-page PDFs/images**

{% @supademo/embed demoId="cmdipnkx90upc1c4c4h4d8pph" url="https://app.supademo.com/demo/cmdipnkx90upc1c4c4h4d8pph" %}
