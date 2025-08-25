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

{% @supademo/embed demoId="cmeqvjfgw3holv9kqocym86w9" url="https://app.supademo.com/demo/cmeqvjfgw3holv9kqocym86w9" %}

### 1. Choose Passport from Our Catalogue (recommended)

* Select "Passport" on our document models.
* The AI agent will give you a list of fields you can choose from. Select the fields you need and create your first model.
* Option : if you want to refine your model, go to "Data Schema" and ask the AI agent for additional fields.
* Now that your model is ready, you can try a live test.

### 2. Build a Passport Model from Scratch

* Ask the specifications directly to the AI agent (e.g. "_I want a model that extracts the following fields from passports: surname, date of birth and MRZ_").
* Additionally, you can upload a sample passport if needed for clarification.
* The agent builds a tailored parser in seconds.

## Document Format

* The AI agent supports both **single-page and multi-page PDFs/images of passports.**
* You can add the fields of any page in the data schema as they are all supported by our AI agent.
