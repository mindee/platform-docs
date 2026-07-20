---
description: General description of an extraction model's Data Schema.
icon: database
---

# Data Schema Overview

An **Extraction Data Schema** defines which data should be extracted, and in what way, from documents sent to the model.

The Data Schema is the foundation of your model. All other features will use and depend on the Data Schema.

You can think of the Data Schema as a map to the documents you send to the model for extraction.

This map includes which data to extract, how to format the data, pitfalls to avoid, etc.\
\
To do this, the Data Schema is composed of Fields (or data points), each field having its own configuration.

{% hint style="info" icon="lightbulb" %}
Use the [live-test.md](../models/live-test.md "mention") when working on your Data Schema to quickly validate changes.
{% endhint %}

## Fields Overview

A Data Schema is primarily composed of fields.

A field describes a single data point to extract in the document.

Each field has the following properties:

* Title - human-readable
* Name - machine-readable, used as the field's key in the API return
* Type - the type of data to extract, details in: [#field-types](data-schema.md#field-types "mention")
* Description (optional) - provides extra context on how the field is used
* Guidelines (optional) - provides instructions to better extract the field

## Field Types

A field's type determines how it will be formatted when returned by the API.

The type also gives an indication on what to look for in the input file.

### Base Types

<table><thead><tr><th width="191.2000732421875">Field Type</th><th>Description</th></tr></thead><tbody><tr><td>Text</td><td>A sequence of characters representing textual data, a string value.</td></tr><tr><td>Number</td><td>Numeric data which can be a whole value (integer) or a decimal value (floating point).</td></tr><tr><td>Date</td><td>A specific year, month, and day, formatted as a <code>YYYY-MM-DD</code> date or <code>YYYY-MM-DD HH:mm:ss</code> for date and time.</td></tr><tr><td>Classification</td><td>A defined list of categories or types to match. Category names are text strings.</td></tr><tr><td>Boolean</td><td><p>Represents two possible values: <code>true</code> or <code>false</code> </p><p>Should be used for checkboxes.</p><p>Hint: boolean field names should start with "is" or "has".</p></td></tr><tr><td>Nested Object</td><td><p>A complex data type containing multiple subfields or properties.</p><p>Used to group related elements, such as the components of an address.</p><p>Subfields may contain a single value or a list of values.</p><p>Only one level of nesting: subfields may not be nested objects.</p></td></tr><tr><td>Object Detection</td><td>Detect the location of a document feature, such as a logo, signature, photo, etc.</td></tr><tr><td>Barcode</td><td><p>Detect the location of a 1D barcode (i.e. UPC, EAN) or a 2D barcode (i.e. QR Code, Data Matrix, 2D-DOC, PDF417).</p><p>Additionally, attempt to decode the contents of the barcode as a string value.</p></td></tr></tbody></table>

{% hint style="info" %}
All fields can have an empty (null) value.
{% endhint %}

### **Array Types**

Any field type can be made into an array, a list of values.

Simply enable "Multiple items can be extracted" when creating or modifying the field.

The return type will be an array of the base type, for example a list of text values, or a list of numbers.

It is possible to have a list of nested objects, but not a list of lists.

{% hint style="info" icon="lightbulb" %}
In some cases, there can be duplicate items, for example when the same value appears on several pages.

Enable "Filter out duplicates from the list of items" to fix this.
{% endhint %}

## **Field Examples**

Some examples for the best field types to use, given a basic invoice extraction Data Schema.

<table><thead><tr><th>Field Name</th><th width="203.5">Field Type</th><th>Example Return Value</th></tr></thead><tbody><tr><td><strong>Supplier Name</strong></td><td>String</td><td><code>Acme Supplies Ltd.</code></td></tr><tr><td><strong>Supplier Logo</strong></td><td>Object Detection</td><td>Polygon around the logo</td></tr><tr><td><strong>Supplier Company Registration</strong></td><td>Nested Object</td><td><em>See sub-fields below</em></td></tr><tr><td><em>Supplier Company Registration.</em><strong>Number</strong></td><td>String</td><td><code>CRN-20250123</code></td></tr><tr><td><em>Supplier Company Registration.</em><strong>Type</strong></td><td>Classification</td><td><code>VAT NUMBER</code></td></tr><tr><td><strong>Invoice Date</strong></td><td>Date</td><td><code>2025-06-10</code></td></tr><tr><td><strong>Is Past Due</strong></td><td>Boolean</td><td><code>false</code></td></tr><tr><td><strong>Total Amount</strong></td><td>Number</td><td><code>1540.75</code></td></tr><tr><td><strong>Taxes</strong></td><td>Nested Objects Array</td><td><em>See sub-fields below</em></td></tr><tr><td><em>Taxes[0].</em><strong>Rate</strong></td><td>number</td><td><code>0.185</code></td></tr><tr><td><em>Taxes[0].</em><strong>Base</strong></td><td>number</td><td><code>1300.00</code></td></tr><tr><td><em>Taxes[0].</em><strong>Amount</strong></td><td>number</td><td><code>240.75</code></td></tr></tbody></table>

## Overall Guidelines

In addition to individual field guidelines, an overall (or global) guideline can be used in your Data Schema.

The overall guideline text will apply to all or some fields, depending on your instructions.

Use overall guidelines when you want to:

* Generalize instructions to several specific fields. For example:
  * _"Number fields related to amounts should always have 3 decimal places."_
  * _"Country fields should return the ISO alpha-3 code of the country."_
* Provide general instructions or context for all fields. For example:
  * _"Ensure ASCII compliance by removing all diacritics from return values."_

{% hint style="info" %}
You may put any number of unrelated guidelines in the text, for example all of the samples above.

For best results, separate each different guideline with a new line.
{% endhint %}

## Document Text

### Language

You can specify a field's _Title_, _Name_, _Description_, and _Guidelines_ in most languages.

This also applies to the Data Schema's [#global-guidelines](data-schema.md#global-guidelines "mention").

Mindee models can process documents in most languages.

This includes, but is **not limited** to:

* European languages: English, French, Spanish, German, Italian, Portuguese, Russian, Greek, etc
* Asian languages: Hindi, Bengali, Turkish, Urdu, Farsi, Armenian, etc
* East Asian languages: Japanese, Mandarin, Korean, Vietnamese, etc
* Semitic languages: Arabic, Hebrew, Amharic, etc
* African languages: Swahili, Yoruba, Zulu, etc

**Note:** while the models can understand these languages, we are not able to provide in-depth support for all languages.

### Handwriting

Mindee models are able to recognize (or OCR) handwritten texts. Accuracy for handwriting is on average a bit less than printed text.

## Technical Limitations

{% include "../.gitbook/includes/data-schema-technical-limitations.md" %}

## Next Steps

Now that you're familiar with the different components of the Data Schema, you'll want to take a look at tips for [building an accurate Data Schema](data-schema-best-practices.md).
