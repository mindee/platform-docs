---
description: >-
  Mindee enables the automatic extraction of structured identity data from ID
  cards, a critical component for use cases like identity verification, KYC, and
  onboarding.
icon: address-card
---

# International ID Card

Watch this short demo to see how quickly you can set up and test the French ID Card model with Mindee:

{% @supademo/embed url="https://app.supademo.com/demo/cmf59btop30t539ozuva4neqi" demoId="cmf59btop30t539ozuva4neqi" %}

## Why use Mindee for ID cards?

ID cards differ vastly across countries in design, language, and layout. Mindee abstracts that complexity by offering:

* Pre-trained models ready for different document types
* Plug-and-play integration—no template design or training required
* High accuracy and speed, even with variations in card format, font, or photo quality

## What can be extracted from ID cards?

Mindee’s ID card API returns structured fields found on most ID documents:

| Field                  | Description                        |
| ---------------------- | ---------------------------------- |
| Document Type          | Type of ID (like national ID card) |
| Document Number        | Unique Identifier on the card      |
| Given Name(s), Surname | Personal name data                 |
| Birth Date             | YYYY-MM-DD format                  |
| Birth Place            | City or region of birth            |
| Issurance Date         | Card issue date                    |
| Expiry Date            | Expiration date                    |
| Gender                 | M/F/other options                  |
| Nationality            | Issuing country code               |
| MRZ Lines              | If present, machine-readable data  |
| Address                | (when applicable)                  |
| Additional metada      | Depends on region/document         |
| Signature              | Signature of the holder            |
| ID photo               | Photo of the holder                |

## Example: French National ID Card (Carte Nationale d’Identité – France)

### Why Mindee works for French ID Cards

Mindee’s ID Card France OCR model handles all French ID variations. It’s optimized to read both MRZ and non‑MRZ zones, ensuring high accuracy across all formats.

Mindee can extract specific French ID card fields like:

* **Card Access Number (CAN)** – a unique numeric code specific to French ID cards; not labeled on the document itself
* **Issuing Authority** – indicates the specific French administrative body (mairie, préfecture, etc.) that issued the card
* **Document Type** – classification indicating which version of the ID card it is (NEW - the issued version from 2021 or OLD - the issued version from 1988 - 2021)
* **Document Sides** – indicates whether the processed image is the front or back of the ID
* **Image Orientation** – rotation metadata indicating how the image was oriented during extraction

If you want to try and do a live test, you can use this French ID example:

<figure><img src="../../.gitbook/assets/french-id-sample.jpg" alt="" width="563"><figcaption></figcaption></figure>

### Two Ways to Start

#### 1. Pick the ID Card Model from the Catalog (Recommended)

* In your Mindee dashboard, go to the **Document Catalog** and choose the **“International ID”** model.
* Once selected, the platform will generate a prefilled schema with standard identity fields. You can accept that schema as is or adjust it in the **Data Schema** section to fine-tune what’s extracted.
* After the model is set up, you can immediately test it with your own documents.

#### 2. Build an ID Card Model from Scratch

* In the dialog with Mindee’s AI assistant, describe what the document is (e.g., “a French national ID card”) and specify the fields you want to extract (such as surname, date of birth, issuing authority).
* The AI will propose an initial schema—review it and adjust fields or mapping in the **Data Schema** tab until it fits your requirements.
* Once finalized, your custom model is ready for live testing.

## Document format support

The API handles both PDF and common image formats (JPG, PNG), including smartphone photos. It applies reliably to front/back sides and both old and new French ID layouts.

## International ID Fields

Documentation for all fields present in the data schema.

Field _accessors_ are used as the keys for accessing the values in the returned data. On the data schema interface, this is the "Field Name".

Field _value types_ indicate how the value is returned by the API. On the data schema interface, this is the "Field Type".

### Given Names

The given names of the person.

Accessor: `given_names`\
Value Type: `string`

Has a single value.

### Surnames

The surnames of the person.

Accessor: `surnames`\
Value Type: `string`

Has a single value.

### Date of Birth

The date of birth of the person.

Accessor: `date_of_birth`\
Value Type: `date`

Has a single value.

### Place of Birth

The place of birth of the person.

Accessor: `place_of_birth`\
Value Type: `string`

Has a single value.

### Nationality

The nationality of the person.

Accessor: `nationality`\
Value Type: `string`

Has a single value.

### Sex

The sex of the person.

Accessor: `sex`\
Possible Values: `M`, `F`, `Other`

Has a single value.

### Document Number

The document number of the ID.

Accessor: `document_number`\
Value Type: `string`

Has a single value.

### Date of Issue

The date when the ID was issued.

Accessor: `date_of_issue`\
Value Type: `date`

Has a single value.

### Date of Expiry

The date when the ID expires.

Accessor: `date_of_expiry`\
Value Type: `date`

Has a single value.

### Authority

The authority that issued the ID.

Accessor: `authority`\
Value Type: `string`

Has a single value.

### Address

The address of the person.

Accessor: `address`

#### Subfields

* **Street**\
  The street address.\
  Accessor: `street`\
  Value Type: `string`
* **City**\
  The city.\
  Accessor: `city`\
  Value Type: `string`
* **State**\
  The state or province.\
  Accessor: `state`\
  Value Type: `string`
* **Postal Code**\
  The postal code.\
  Accessor: `postal_code`\
  Value Type: `string`
* **Country**\
  The country.\
  Accessor: `country`\
  Value Type: `string`

Has a single value.

### Document Type

The type of ID document.

Accessor: `document_type`\
Possible Values: `Passport`, `National ID`, `Driver License`, `Residence Permit`

Has a single value.

### MRZ

The mrz, the Machine Readable Zone.

Accessor: `mrz`

#### Subfields

* **Line 1**\
  The first line of the mrz.\
  Accessor: `line_1`\
  Value Type: `string`
* **Line 2**\
  The second line of the mrz.\
  Accessor: `line_2`\
  Value Type: `string`
* **Line 3**\
  The third line of the mrz.\
  Accessor: `line_3`\
  Value Type: `string`

Has a single value.
