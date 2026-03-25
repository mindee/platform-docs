---
icon: database
---

# Data Schema

## Overview

An **Extraction Data Schema** defines which data should be extracted, and in what way, from documents sent to the model.

You can think of the Data Schema as a map to the documents you send to the model for extraction.

This map includes which data to extract, how to format the data, pitfalls to avoid, etc.\
\
To do this, the Data Schema is composed of Fields (or data points), each field having its own configuration.

In this way the Data Schema is the foundation of your model. All other features will use and depend on the Data Schema.

{% hint style="info" icon="lightbulb" %}
Use the [live-test.md](../models/live-test.md "mention") when working on your Data Schema to quickly validate changes.
{% endhint %}

## Field Types

A field's type determines how it will be formatted when returned by the API.

The type also gives an indication on what to look for in the input file.

### Base Types

<table><thead><tr><th width="191.2000732421875">Field Type</th><th>Description</th></tr></thead><tbody><tr><td>Text</td><td>A sequence of characters representing textual data.</td></tr><tr><td>Number</td><td>Numeric data which could be an integer or a floating-point value.</td></tr><tr><td>Date</td><td>A specific year, month, and day, formatted as a <code>YYYY-MM-DD</code> date or <code>YYYY-MM-DD HH:mm:ss</code> for a date-time.</td></tr><tr><td>Classification</td><td>A defined list of categories or types to match.</td></tr><tr><td>Boolean</td><td>Represents two possible values: <code>true</code> or <code>false</code></td></tr><tr><td>Nested Object</td><td>A complex data type containing multiple subfields or properties, allowing one level of nesting.</td></tr><tr><td>Object Detection</td><td>Detect the location of a document feature, such as a logo, signature, photo, etc.</td></tr><tr><td>Barcode</td><td><p>Detect the location of a 1D barcode (i.e. UPC, EAN) or a 2D barcode (i.e. QR Code, Data Matrix, 2D-DOC, PDF417).</p><p>Additionally, attempt to decode the contents of the barcode as a string value.</p></td></tr></tbody></table>

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

<table><thead><tr><th>Field Name</th><th width="203.5">Field Type</th><th>Example Return Value</th></tr></thead><tbody><tr><td><strong>Supplier Name</strong></td><td>String</td><td><code>Acme Supplies Ltd.</code></td></tr><tr><td><strong>Supplier Logo</strong></td><td>Object Detection</td><td>Polygon around the logo</td></tr><tr><td><strong>Supplier Company Registration</strong></td><td>Nested Object</td><td><em>See sub-fields below</em></td></tr><tr><td><em>Supplier Company Registration.</em><strong>Number</strong></td><td>String</td><td><code>CRN-20250123</code></td></tr><tr><td><em>Supplier Company Registration.</em><strong>Type</strong></td><td>Classification</td><td><code>VAT NUMBER</code></td></tr><tr><td><strong>Invoice Date</strong></td><td>Date</td><td><code>2025-06-10</code></td></tr><tr><td><strong>Total Amount</strong></td><td>Number</td><td><code>1540.75</code></td></tr><tr><td><strong>Taxes</strong></td><td>Nested Objects Array</td><td><em>See sub-fields below</em></td></tr><tr><td><em>Taxes[0].</em><strong>Rate</strong></td><td>number</td><td><code>0.185</code></td></tr><tr><td><em>Taxes[0].</em><strong>Base</strong></td><td>number</td><td><code>1300.00</code></td></tr><tr><td><em>Taxes[0].</em><strong>Amount</strong></td><td>number</td><td><code>240.75</code></td></tr></tbody></table>

## Global Guidelines

In addition to individual field guidelines, a global guideline can be used in your Data Schema.

The global guideline text will apply to all or some fields, depending on your instructions.

Use global guidelines when you want to:

* Generalize instructions to several specific fields. For example:
  * _"Number fields related to amounts should always have 3 decimal places."_
  * _"Country fields should return the ISO alpha-3 code of the country."_
* Provide general instructions or context for all fields. For example:
  * _"Ensure ASCII compliance by removing all diacritics from return values."_

{% hint style="info" %}
You may put any number of unrelated guidelines in the text, for example all of the samples above.

For best results, separate each different guideline with a new line.
{% endhint %}

## Performance Optimization

To get the best possible extraction data from a model, the most important is to ensure the Data Schema you're using is clear and optimized.

Any additional features you activate to increase accuracy, such as [improving-accuracy.md](optional-features/improving-accuracy.md "mention") or [automation-confidence-score.md](optional-features/automation-confidence-score.md "mention")will rely heavily on the Data Schema.

The various properties of the field all have a role to play in getting the best possible performance.

### **Field Name and Title**

The field _Name_ is automatically generated from the field _Title_. You can however modify the _Title_ afterwards.

Both the _Name_ and _Title_ are used during processing (inference), but the _Name_ is more important.

Try to use clear, simple names that will precisely describe the field you want to extract.\
The goal is to avoid any possible confusion between data points present in the document.

Consider wanting to extract the name of the company that issued an invoice.

In our model, we've used the field _Name_:  `supplier_name`\
It clearly tells the AI to get only the name, and of the invoice supplier.

:white\_check\_mark: you could also use `vendor_name`, it means the same thing with the same level of precision.

:warning: `supplier` might work but is imprecise: which information about the supplier do you need?

:warning: `company_name` might work but is imprecise: we know you need the name of the company, but we don't know if company stands for supplier or customer?

:x: `company` will likely not work as expected: we do not know neither which information you need nor which company is concerned.

### Field Type

Try to use the [#field-types](data-schema.md#field-types "mention") that will best suits how the field is used and present in the document.

For example, while you could use a string for `due_date`, a date field type is definitely better.

### Field Description

The field's _Description_ has an impact on the model's performance.

Use it to describe what the field represents, and/or of what its use is to you.

For example, the `supplier_name` field could have:

> The name of the supplier.
>
> Used in internal processing to match our supplier ID with the name found on the document.

### Field Extraction Guidelines

Sometimes changing the field name and type is not enough to explain what you need for one field.\
In that case you have the possibility to add extraction _Guidelines_ to the field.

Use natural language to explain how to properly extract the data, and/or any extra steps like formatting.

For instance, with `supplier_phone_number` , adding the following extraction guidelines could be useful:

> If you find several phone numbers in the document, use the phone number of the supplier headquarters.
>
> Always reformat the data to match the international phone number format, as follows: +1-212-456-7890

### Relative Importance of Field Properties

Not all field properties have the same importance or weight when it comes to how the models process files.

Additionally, not all types of fields are handled the same way.

In the following table, "Normal Fields" are those that extract textual information from the document (text, dates, numbers, etc), whether they are simple fields, lists, or nested object fields.

"Object Detection" refers to specific processing to extract polygons of various elements on the document, such as signatures, ID photos, etc.

<table><thead><tr><th width="208.0001220703125">Property</th><th width="261.4000244140625">Normal Field Usage </th><th>Object Detection Usage</th></tr></thead><tbody><tr><td>Name</td><td><strong>Most important</strong></td><td>Not used</td></tr><tr><td>Title</td><td>Important</td><td><strong>Most important</strong></td></tr><tr><td>Description</td><td>Complementary</td><td>Not used</td></tr><tr><td>Guidelines</td><td>Complementary</td><td>Not used</td></tr><tr><td>Classification Values</td><td>Very important (only for classification fields)</td><td>Not used</td></tr></tbody></table>

### Language

You can specify a field's _Title_, _Name_, _Description_, and _Guidelines_ in most languages.\
Note that the _Name_ can only contain ASCII characters.

This includes, _but is not limited to_:

* European languages: English, French, Spanish, German, Italian, Portuguese, Russian, Greek, etc
* Asian languages: Hindi, Bengali, Turkish, Urdu, Farsi, Armenian, etc
* East Asian languages: Japanese, Mandarin, Korean, Vietnamese, etc
* Semitic languages: Arabic, Hebrew, Amharic, etc
* African languages: Swahili, Yoruba, Zulu, etc

**Note:** while the models can understand, we are not able to provide in-depth support for all languages.

### Less Is More

It can be tempting to give very detailed instructions in guidelines and descriptions. However, in many cases this is actually counter-productive and will lead to diminished accuracy.

Here is an example of too many details (don't do this):

> The order number is usually next to the words "order no" on the invoice, but sometimes there is no order number, so it will be next to the words "customer invoice no". It is usually present on the first page, in a green box.

What's wrong here? Well first thing to understand is that you are not giving instructions to a human, but to a machine. Machines prefer concise instructions. On the other hand, this machine has been trained on millions of documents, and is perfectly capable of determining the location of a value field on its own.

So what's left is just the instruction about the _customer invoice_ and _order number_.

A simpler, better version would be:

> Use the value of "customer invoice number" if "order number" is missing in the document.

### Remove Ambiguity with Extra Fields

In some cases, it can be beneficial to add extra fields you don't actually need in order to remove ambiguity on the data you do need.

Let's say you are processing invoices, and need to extract the "Reference Number". When processing the invoices, you notice that, sometimes, the "Order Number" is picked up as the reference number.

A first logical step would be to add a guideline, something like _"NEVER use the 'Order Number' to populate this field"_. While this should work in most cases, the distinction between a Reference and Order is may not be perfectly clear to the model.

Adding more text, more detailed information is potentially [counter-productive](data-schema.md#less-is-more).

A potential fix would be to add the "Reference Number" field in your Data Schema, in addition to the "Order Number" field. This way the ambiguity is lifted, it is now very clear to the model that these are separate data points.

In your data processing flow, simply ignore the extra field.

As a reminder, there is no additional cost to you for the number of fields in the Data Schema.

## Technical Limitations

{% include "../.gitbook/includes/data-schema-technical-limitations.md" %}

## Next Steps

Once you are satisfied with your Data Schema, you'll likely to want to use one of our [Broken link](/broken/pages/iREYUuRlIfMqqSxTfHZF "mention") to connect your model with your platform.
