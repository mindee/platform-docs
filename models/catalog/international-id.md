# International ID

Documentation for the data schema of the International ID model.

## International ID Fields

Documentation for all fields present in the data schema.

Field _accessors_ are used as the keys for accessing the values in the returned data.
On the data schema interface, this is the "Field Name".

Field _value types_ indicate how the value is returned by the API.
On the data schema interface, this is the "Field Type".


### Given Names

The given names of the person.

Accessor: `given_names` \
Value Type: `string`


Has a single value.


### Surnames

The surnames of the person.

Accessor: `surnames` \
Value Type: `string`


Has a single value.


### Date of Birth

The date of birth of the person.

Accessor: `date_of_birth` \
Value Type: `date`


Has a single value.


### Place of Birth

The place of birth of the person.

Accessor: `place_of_birth` \
Value Type: `string`


Has a single value.


### Nationality

The nationality of the person.

Accessor: `nationality` \
Value Type: `string`


Has a single value.


### Sex

The sex of the person.

Accessor: `sex` \
Possible Values: `M`, `F`, `Other`

Has a single value.


### Document Number

The document number of the ID.

Accessor: `document_number` \
Value Type: `string`


Has a single value.


### Date of Issue

The date when the ID was issued.

Accessor: `date_of_issue` \
Value Type: `date`


Has a single value.


### Date of Expiry

The date when the ID expires.

Accessor: `date_of_expiry` \
Value Type: `date`


Has a single value.


### Authority

The authority that issued the ID.

Accessor: `authority` \
Value Type: `string`


Has a single value.


### Address

The address of the person.

Accessor: `address`

#### Subfields
  - **Street** \
  The street address. \
  Accessor: `street` \
  Value Type: `string`

  - **City** \
  The city. \
  Accessor: `city` \
  Value Type: `string`

  - **State** \
  The state or province. \
  Accessor: `state` \
  Value Type: `string`

  - **Postal Code** \
  The postal code. \
  Accessor: `postal_code` \
  Value Type: `string`

  - **Country** \
  The country. \
  Accessor: `country` \
  Value Type: `string`


Has a single value.


### Document Type

The type of ID document.

Accessor: `document_type` \
Possible Values: `Passport`, `National ID`, `Driver License`, `Residence Permit`

Has a single value.


### MRZ

The mrz, the Machine Readable Zone.

Accessor: `mrz`

#### Subfields
  - **Line 1** \
  The first line of the mrz. \
  Accessor: `line_1` \
  Value Type: `string`

  - **Line 2** \
  The second line of the mrz. \
  Accessor: `line_2` \
  Value Type: `string`

  - **Line 3** \
  The third line of the mrz. \
  Accessor: `line_3` \
  Value Type: `string`


Has a single value.
