---
title: model-fields_drivers-license
---

Documentation for all fields present in the data schema.

Field _accessors_ are used as the keys for accessing the values in the returned data.
On the data schema interface, this is the "Field Name".

Field _value types_ indicate how the value is returned by the API.
On the data schema interface, this is the "Field Type".


<details>
<summary>First Name</summary>

The given name(s) or first name(s) of the person.

Accessor: `first_name`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Last Name</summary>

The surnames or last names of the person.

Accessor: `last_name`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Date of Birth</summary>

The date of birth of the person.

Accessor: `date_of_birth`\
Value Type: `date`


Has a single value.

</details>

<details>
<summary>Place of Birth</summary>

The place of birth of the person.

Accessor: `place_of_birth`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Nationality</summary>

The nationality of the person.

Accessor: `nationality`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Sex</summary>

The sex of the person.

Accessor: `sex`\
Possible Values: `M`, `F`, `Other`

Has a single value.

</details>

<details>
<summary>Document Id</summary>

The document number or the ID number of the document.

Accessor: `document_id`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Issued Date</summary>

The date when the document was issued.

Accessor: `issued_date`\
Value Type: `date`


Has a single value.

</details>

<details>
<summary>Expiry Date</summary>

The date when the Document expires.

Accessor: `expiry_date`\
Value Type: `date`


Has a single value.

</details>

<details>
<summary>Country Code</summary>

Country code extracted as a string.

Accessor: `country_code`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Issuing Authority</summary>

The authority that issued the document.

Accessor: `issuing_authority`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Address</summary>

The address of the person.

Accessor: `address`

#### Subfields
- **Street**\
  The street address.\
  Accessor: `street`\
  Value Type: `string`

- **City**\
  The city.\
  Accessor: `city`\
  Value Type: `string`

- **State**\
  The state or province.\
  Accessor: `state`\
  Value Type: `string`

- **Postal Code**\
  The postal code.\
  Accessor: `postal_code`\
  Value Type: `string`

- **Country**\
  The country.\
  Accessor: `country`\
  Value Type: `string`


Has a single value.

</details>

<details>
<summary>MRZ</summary>

Machine-readable license number

Accessor: `mrz`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Driver License Category</summary>

EU driver license holders categories

Accessor: `category`\
Value Type: `string`


Has a single value.

</details>
