---
title: model-fields_international-id
---

# International ID Fields

Documentation for all fields present in the data schema.

Field _accessors_ are used as the keys for accessing the values in the returned data.
On the data schema interface, this is the "Field Name".

Field _value types_ indicate how the value is returned by the API.
On the data schema interface, this is the "Field Type".


<details>
<summary>Given Names</summary>

The given names of the person.

Accessor: `given_names`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Surnames</summary>

The surnames of the person.

Accessor: `surnames`\
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
<summary>Document Number</summary>

The document number of the ID.

Accessor: `document_number`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Date of Issue</summary>

The date when the ID was issued.

Accessor: `date_of_issue`\
Value Type: `date`


Has a single value.

</details>

<details>
<summary>Date of Expiry</summary>

The date when the ID expires.

Accessor: `date_of_expiry`\
Value Type: `date`


Has a single value.

</details>

<details>
<summary>Authority</summary>

The authority that issued the ID.

Accessor: `authority`\
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
<summary>Document Type</summary>

The type of ID document.

Accessor: `document_type`\
Possible Values: `Passport`, `National ID`, `Driver License`, `Residence Permit`

Has a single value.

</details>

<details>
<summary>MRZ</summary>

The mrz, the Machine Readable Zone.

Accessor: `mrz`

#### Subfields
- **Line 1**\
  The first line of the mrz.\
  Accessor: `line_1`\
  Value Type: `string`

- **Line 2**\
  The second line of the mrz.\
  Accessor: `line_2`\
  Value Type: `string`

- **Line 3**\
  The third line of the mrz.\
  Accessor: `line_3`\
  Value Type: `string`


Has a single value.

</details>
