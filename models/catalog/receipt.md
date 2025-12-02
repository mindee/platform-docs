# Receipt

Documentation for the data schema of the Receipt model.

## Receipt Fields

Documentation for all fields present in the data schema.

Field _accessors_ are used as the keys for accessing the values in the returned data.
On the data schema interface, this is the "Field Name".

Field _value types_ indicate how the value is returned by the API.
On the data schema interface, this is the "Field Type".


### Supplier Name

The name of the supplier of the receipt.

Accessor: `supplier_name` \
Value Type: `string`


Has a single value.


### Supplier Address

The full address of the supplier who delivered the receipt.

Accessor: `supplier_address` \
Value Type: `string`


Has a single value.


### Supplier Phone Number

The phone number of the supplier of the receipt.

Accessor: `supplier_phone_number` \
Value Type: `string`


Has a single value.


### Supplier Company Registration

A list of company registration details including type and number,  for the supplier of the receipt.

Accessor: `supplier_company_registration`

#### Subfields
  - **Number** \
  The company registration number. \
  Accessor: `number` \
  Value Type: `string`

  - **Type** \
  The type of the company registration number. \
  Accessor: `type` \
  Possible Values: `VAT`, `SIRET`, `SIREN`, `NIF`, `CF`, `UID`, `STNR`, `HRA_HRB`, `TIN`, `RFC`, `BTW`, `ABN`, `UEN`, `CVR`, `ORGNRO`, `INN`, `DPH`, `NIP`, `GSTIN`, `CRN`, `KVK`, `DIC`, `TAX_ID`, `CIF`, `GST_HST_CA`, `COC`

Can have multiple values (is a list/array).


### Receipt Number

The number of the receipt.

Accessor: `receipt_number` \
Value Type: `string`


Has a single value.


### Date

The date the receipt was issued.

Accessor: `date` \
Value Type: `date`


Has a single value.


### Time

The time the receipt was issued.

Accessor: `time` \
Value Type: `string`


Has a single value.


### Total Amount

The final total amount paid, including all taxes and discounts.

Accessor: `total_amount` \
Value Type: `number`


Has a single value.


### Total Net

The total amount before taxes.

Accessor: `total_net` \
Value Type: `number`


Has a single value.


### Total Tax

The total amount of all taxes.

Accessor: `total_tax` \
Value Type: `number`


Has a single value.


### Taxes

A list of individual taxes applied, each including rate, base and amount.

Accessor: `taxes`

#### Subfields
  - **Rate** \
  The tax rate of this tax as a decimal. \
  Accessor: `rate` \
  Value Type: `number`

  - **Base** \
  The base amount on which this tax is computed. \
  Accessor: `base` \
  Value Type: `number`

  - **Amount** \
  The computed tax amount for this tax. \
  Accessor: `amount` \
  Value Type: `number`


Can have multiple values (is a list/array).


### Tips & Gratuity

The total tips and gratuities for the receipt.

Accessor: `tips_gratuity` \
Value Type: `number`


Has a single value.


### Line Items

A list of line items in the receipt, each including description, quantity, unit price and total price.

Accessor: `line_items`

#### Subfields
  - **Description** \
  A description of the item or service. \
  Accessor: `description` \
  Value Type: `string`

  - **Quantity** \
  The quantity of the item or service. \
  Accessor: `quantity` \
  Value Type: `number`

  - **Unit Price** \
  The price per unit of the item or service. \
  Accessor: `unit_price` \
  Value Type: `number`

  - **Total Price** \
  The total price for the line item: quantity * unit price. \
  Accessor: `total_price` \
  Value Type: `number`


Can have multiple values (is a list/array).


### Document Type

Document type: expense receipt or credit card receipt

Accessor: `document_type` \
Possible Values: `expense_receipt`, `credit_card_receipt`

Has a single value.


### Purchase Category

The category of the receipt.

Accessor: `purchase_category` \
Possible Values: `food`, `gasoline`, `parking`, `toll`, `accommodation`, `transport`, `telecom`, `software`, `shopping`, `energy`, `miscellaneous`

Has a single value.


### Purchase Subcategory

The purchase subcategory of the receipt.

Accessor: `purchase_subcategory` \
Possible Values: `restaurant`, `delivery`, `train`, `public`, `taxi`, `car_rental`, `plane`, `micromobility`, `office_supplies`, `electronics`, `cultural`, `groceries`, `other`

Has a single value.


### Locale

The locale contains the language, country and currency of the receipt.

Accessor: `locale`

#### Subfields
  - **Language** \
  The language of the receipt, ISO 639-1 language code. \
  Accessor: `language` \
  Value Type: `string`

  - **Country** \
  The country of the receipt, ISO 3166-1 alpha-2. \
  Accessor: `country` \
  Value Type: `string`

  - **Currency** \
  The currency in which is issued the receipt, ISO 4217. \
  Accessor: `currency` \
  Value Type: `string`


Has a single value.
