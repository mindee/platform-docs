---
icon: database
---

# Data Schema

## Overview&#x20;

An Extraction Data Schema is a type of structured data that helps the system identify which data points to extract from specific documents.

A Data Schema guides the system on the technical processes required and ensures the extracted data is formatted for easy access by the user.\
\
The Data Schema is composed of a certain number of Fields (or data points), each with a type and an example.

## Field Types

There are seven different field types:

<table><thead><tr><th width="224">Field Type</th><th>Description</th></tr></thead><tbody><tr><td>String</td><td>A sequence of characters representing textual data.</td></tr><tr><td>Classification</td><td>A predefined list of categories or types.</td></tr><tr><td>Date</td><td>A specific year, month, and day, formatted as a <code>YYYY-MM-DD</code> date-time.</td></tr><tr><td>Number</td><td>Numeric data which could be an integer or a floating-point value.</td></tr><tr><td>Boolean</td><td>Represents two possible values: <code>true</code> or <code>false</code></td></tr><tr><td>Object Detection</td><td>Detect the location of a document feature, such as a logo, signature, photo, etc</td></tr><tr><td>Nested Object</td><td>A complex data type that contains multiple sub-fields or properties allowing one level of nesting.</td></tr></tbody></table>

### **Example**

An example of the field types for a basic invoice extraction Data Schema:

<table><thead><tr><th>Field</th><th width="192">Type</th><th>Example</th></tr></thead><tbody><tr><td><strong>Supplier Name</strong></td><td>String</td><td>Acme Supplies Ltd.</td></tr><tr><td><strong>Supplier Logo</strong></td><td>Object Detection</td><td>Polygon (bounding box) around the logo</td></tr><tr><td><strong>Supplier Company Registration</strong></td><td>Nested Object</td><td>(see sub-fields below)</td></tr><tr><td><em>Supplier Company Registration.Number</em></td><td>String</td><td>CRN-20250123</td></tr><tr><td><em>Supplier Company Registration.Type</em></td><td>Classification</td><td>VAT NUMBER</td></tr><tr><td><strong>Date</strong></td><td>Date</td><td>2025-06-10</td></tr><tr><td><strong>Total Amount</strong></td><td>Number</td><td>1540.75</td></tr><tr><td><strong>Taxes</strong></td><td>Nested Object</td><td>(see sub-fields below)</td></tr><tr><td><em>Taxes.Rate</em></td><td>number</td><td>0.185</td></tr><tr><td><em>Taxes.Base</em></td><td>number</td><td>1300.00</td></tr><tr><td><em>Taxes.Amount</em></td><td>number</td><td>240.75</td></tr></tbody></table>

## Building a Top-Performing Data Schema

To get the best possible extraction data from a model, you can of course use the [improving-accuracy.md](optional-features/improving-accuracy.md "mention") feature, but the very first step is to ensure the Data Schema you're using is optimized.&#x20;

> _If the foundation is solid, the house is solid_

### **Field Name and Title**

The field _name_ is automatically generated from the field _title_.

While the _title_ is purely for humans, the _name_ has an influence on how the AI system performs the extraction operation.

Try to use simple names that will precisely describe the field you want to extract.\
The goal is to avoid any possible confusion between data points present in the document.

Consider wanting to extract the name of the company that issued an invoice.

In our model, we've used the field _name_: `supplier_name`\
It clearly tells the AI to get only the name, and of the invoice supplier.

:white\_check\_mark: you could also use `vendor_name`, it means the same thing with the same level of precision.

:warning:`supplier` might work but is imprecise: which information about the supplier do you need?

:warning:`company_name` might work but is imprecise: we know you need the name of the company, but we don't know if company stands for supplier or customer?

:x:  `company` will likely not work as expected: we do not know neither which information you need nor which company is concerned.

### Field Type

Try to use the [#field-types](data-schema.md#field-types "mention")that will best suits the field you need.

For the `due_date`, you could use a string, but a date field is definitely a better solution.

### Extraction Guidelines

Sometimes changing the field name and type is not enough to explain what you need for one field.\
In that case you have the possibility to add Extraction Guidelines to the field.

Use natural language to explain how to properly extract the data.

For instance, for `supplier_phone_number` , adding the following extraction guidelines could be useful:&#x20;

> If you find several phone numbers in the document, I need the phone number of the supplier headquarters. Also, I want you to reformat the data to match the international phone number format, as follows : +1-212-456-7890

You can specify guidelines in most languages, including, _but not limited to_:

* European languages: English, French, Spanish, German, Italian, Portuguese, Russian, Greek, etc
* Asian languages: Hindi, Bengali, Turkish, Urdu, Farsi, Armenian, etc
* East Asian languages: Japanese, Mandarin, Korean, Vietnamese, etc
* Semitic languages: Arabic, Hebrew, Amharic, etc
* African languages: Swahili, Yoruba, Zulu, etc

**Note:** while the models can understand, we are not able to provide in-depth support for all languages.

## Technical Limitations

{% include "../.gitbook/includes/data-schema-technical-limitations.md" %}
