---
description: >-
  Whether you are building a Know Your Customer (KYC) process, onboarding flow,
  or document verification pipeline, Mindee helps you parse structured passport
  data with accuracy.
icon: passport
---

# Passport

Take a look at our demo for the Indian Passport model:

{% @supademo/embed url="https://app.supademo.com/demo/cmeqvjfgw3holv9kqocym86w9" demoId="cmeqvjfgw3holv9kqocym86w9" %}

## Why Use Mindee for Passports?

Passports vary in format depending on the country, language, and issuance authority. Mindee simplifies extraction by letting you:

* Describe which fields matter to you
* Upload sample documents to refine extraction
* Get structured outputs without training models yourself

## Two Ways to Start Building your Passport Model

### 1. Choose Passport from Our Catalog (recommended)

* Select "Passport" on our document models.
* The AI will give you a list of fields you can choose from. Select the fields you need and create your first model.
* Option : if you want to refine your model, go to "Data Schema" and ask for additional fields.
* Now that your model is ready, you can try a live test.

### 2. Build a Passport Model from Scratch

* Ask the specifications directly to the AI assistant (e.g. "_I want a model that extracts the following fields from passports: surname, date of birth and MRZ_").
* Additionally, you can upload a sample passport if needed for clarification.
* Mindee builds you a tailored parser in seconds.

If you want to try and do a live test, here is a sample for Indian passport:

<figure><img src="../../.gitbook/assets/indian-passport-sample.png" alt="" width="563"><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/mindee-indian-passport.png" alt="" width="563"><figcaption></figcaption></figure>

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
You can just upload an Indian passport and ask to extract the fields present.
{% endhint %}

## Document Format

* We support both **single-page and multi-page PDFs/images of passports.**
* You can add the fields of any page in the data schema as they are all supported by Mindee.

## Passport Fields

Documentation for all fields present in the data schema.

Field _accessors_ are used as the keys for accessing the values in the returned data. On the data schema interface, this is the "Field Name".

Field _value types_ indicate how the value is returned by the API. On the data schema interface, this is the "Field Type".

### Given Names

The given names (first names) of the passport holder.

Accessor: `given_names`\
Value Type: `string`

Has a single value.

### Surnames

The surnames (last names) of the passport holder.

Accessor: `surnames`\
Value Type: `string`

Has a single value.

### Date of Birth

The date of birth of the passport holder.

Accessor: `date_of_birth`\
Value Type: `date`

Has a single value.

### Place of Birth

The place of birth of the passport holder.

Accessor: `place_of_birth`\
Value Type: `string`

Has a single value.

### Passport Number

The passport number.

Accessor: `passport_number`\
Value Type: `string`

Has a single value.

### Issuing Country

The country that issued the passport.

Accessor: `issuing_country`\
Value Type: `string`

Has a single value.

### Nationality

The nationality of the passport holder.

Accessor: `nationality`\
Value Type: `string`

Has a single value.

### Date of Issue

The date the passport was issued.

Accessor: `date_of_issue`\
Value Type: `date`

Has a single value.

### Date of Expiry

The date the passport expires.

Accessor: `date_of_expiry`\
Value Type: `date`

Has a single value.

### Sex

The sex of the passport holder.

Accessor: `sex`\
Possible Values: `Male`, `Female`, `Other`

Has a single value.

### MRZ Line 1

The first line of the Machine Readable Zone (MRZ).

Accessor: `mrz_line_1`\
Value Type: `string`

Has a single value.

### MRZ Line 2

The second line of the Machine Readable Zone (MRZ).

Accessor: `mrz_line_2`\
Value Type: `string`

Has a single value.
