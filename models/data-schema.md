---
icon: database
---

# Data Schema

## Overview

An Extraction Data Schema is a type of structured data that helps the system identify which data points to extract from specific documents.

A Data Schema guides the system on the technical processes required and ensures the extracted data is formatted for easy access by the user.\
\
The Data Schema is composed of a certain number of Fields (or data points), each with a type and an example.

## Field Types

### Base Types

<table><thead><tr><th width="224">Field Type</th><th>Description</th></tr></thead><tbody><tr><td>Text</td><td>A sequence of characters representing textual data.</td></tr><tr><td>Number</td><td>Numeric data which could be an integer or a floating-point value.</td></tr><tr><td>Date</td><td>A specific year, month, and day, formatted as a <code>YYYY-MM-DD</code> date or <code>YYYY-MM-DD HH:mm:ss</code> for a date-time.</td></tr><tr><td>Classification</td><td>A predefined list of categories or types.</td></tr><tr><td>Boolean</td><td>Represents two possible values: <code>true</code> or <code>false</code></td></tr><tr><td>Nested Object</td><td>A complex data type containing multiple subfields or properties, allowing one level of nesting.</td></tr><tr><td>Object Detection</td><td>Detect the location of a document feature, such as a logo, signature, photo, etc.</td></tr><tr><td>Barcode</td><td><p>Detect the location of a 1D barcode (i.e. UPC, EAN) or a 2D barcode (i.e. QR Code, Data Matrix).</p><p>Additionally, attempt to decode the contents of the barcode as a string value.</p></td></tr></tbody></table>

### **Array Types**

Any field can be made into an array, a list of values.

Simply enable "Multiple items can be extracted" when creating or modifying the field.

The return type will be an array of the base type, for example a list of text values.

It is possible to have a list of nested objects, but not a list of lists.

{% hint style="info" %}
In some cases, there can be duplicate items, for example when the same value appears on several pages.

Enable "Filter out duplicates from the list of items" to fix this.
{% endhint %}

## **Example**

An example of the field types for a basic invoice extraction Data Schema:

<table><thead><tr><th>Field</th><th width="203.5">Type</th><th>Example</th></tr></thead><tbody><tr><td><strong>Supplier Name</strong></td><td>String</td><td><code>Acme Supplies Ltd.</code></td></tr><tr><td><strong>Supplier Logo</strong></td><td>Object Detection</td><td>Polygon around the logo</td></tr><tr><td><strong>Supplier Company Registration</strong></td><td>Nested Object</td><td><em>See sub-fields below</em></td></tr><tr><td><em>Supplier Company Registration.Number</em></td><td>String</td><td><code>CRN-20250123</code></td></tr><tr><td><em>Supplier Company Registration.Type</em></td><td>Classification</td><td><code>VAT NUMBER</code></td></tr><tr><td><strong>Date</strong></td><td>Date</td><td><code>2025-06-10</code></td></tr><tr><td><strong>Total Amount</strong></td><td>Number</td><td><code>1540.75</code></td></tr><tr><td><strong>Taxes</strong></td><td>Nested Objects Array</td><td><em>See sub-fields below</em></td></tr><tr><td><em>Taxes[0].Rate</em></td><td>number</td><td><code>0.185</code></td></tr><tr><td><em>Taxes[0].Base</em></td><td>number</td><td><code>1300.00</code></td></tr><tr><td><em>Taxes[0].Amount</em></td><td>number</td><td><code>240.75</code></td></tr></tbody></table>

## Performance Optimization

To get the best possible extraction data from a model, you can of course use the [improving-accuracy.md](optional-features/improving-accuracy.md "mention") feature, but the very first step is to ensure the Data Schema you're using is optimized.

> _If the foundation is solid, the house is solid._

The various properties of the field all have a role to play in getting the best possible performance.

### **Field Name and Title**

The field _name_ is automatically generated from the field _title_. You can however modify the _title_ afterwards.

Both the _name_ and _title_ are used during processing (inference), but the _name_ is more important.

Try to use clear, simple names that will precisely describe the field you want to extract.\
The goal is to avoid any possible confusion between data points present in the document.

Consider wanting to extract the name of the company that issued an invoice.

In our model, we've used the field _name_:  `supplier_name`\
It clearly tells the AI to get only the name, and of the invoice supplier.

:white\_check\_mark: you could also use `vendor_name`, it means the same thing with the same level of precision.

:warning:`supplier` might work but is imprecise: which information about the supplier do you need?

:warning:`company_name` might work but is imprecise: we know you need the name of the company, but we don't know if company stands for supplier or customer?

:x: `company` will likely not work as expected: we do not know neither which information you need nor which company is concerned.

### Field Type

Try to use the [#field-types](data-schema.md#field-types "mention") that will best suits the field you need.

For example, while you could use a string for `due_date`, a date field type is definitely better.

### Field Description

The field's description also has an impact on the model's performance.

Use it to describe what the field represents, and/or of what its use is to you.

For example, the `supplier_name` field could have:

> The name of the supplier.
>
> Used in internal processing to match our supplier ID with the name found on the document.

### Field Extraction Guideline

Sometimes changing the field name and type is not enough to explain what you need for one field.\
In that case you have the possibility to add an Extraction Guideline to the field.

Use natural language to explain how to properly extract the data, and/or any extra steps like formatting.

For instance, with `supplier_phone_number` , adding the following extraction guidelines could be useful:

> If you find several phone numbers in the document, use the phone number of the supplier headquarters.
>
> Always reformat the data to match the international phone number format, as follows: +1-212-456-7890

### Relative Importance of Field Properties

Not all field properties have the same importance or weight when it comes to how the models process files.

Additionally, not all types of fields are handled the same way.

In the following table, "Normal Fields" are those that extract textual information from the document (string, date, numbers, etc), whether they are simple fields, lists, or nested object fields.

"Object Detection" refers to specific processing to extract polygons of various elements from  the document, such as signatures, photos, etc.

<table><thead><tr><th width="208.0001220703125">Property</th><th width="261.4000244140625">Normal Field Usage </th><th>Object Detection Usage</th></tr></thead><tbody><tr><td>name</td><td><strong>Most important</strong></td><td>Not used</td></tr><tr><td>title</td><td>Important</td><td><strong>Most important</strong></td></tr><tr><td>description</td><td>Complementary</td><td>Not used</td></tr><tr><td>guideline</td><td>Complementary</td><td>Not used</td></tr><tr><td>classification values</td><td>Very important (only for classification fields)</td><td>Not used</td></tr></tbody></table>

### Language

You can specify a field's title, description, and guidelines in most languages.

This includes, _but is not limited to_:

* European languages: English, French, Spanish, German, Italian, Portuguese, Russian, Greek, etc
* Asian languages: Hindi, Bengali, Turkish, Urdu, Farsi, Armenian, etc
* East Asian languages: Japanese, Mandarin, Korean, Vietnamese, etc
* Semitic languages: Arabic, Hebrew, Amharic, etc
* African languages: Swahili, Yoruba, Zulu, etc

**Note:** while the models can understand, we are not able to provide in-depth support for all languages.

## Technical Limitations

{% include "../.gitbook/includes/data-schema-technical-limitations.md" %}
