---
title: model-fields_financial-document
---

Documentation for all fields present in the data schema.

Field _accessors_ are used as the keys for accessing the values in the returned data.
On the data schema interface, this is the "Field Name".

Field _value types_ indicate how the value is returned by the API.
On the data schema interface, this is the "Field Type".


<details>
<summary>Supplier Name</summary>

The name of the supplier of the invoice.

Accessor: `supplier_name`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Supplier Phone Number</summary>

The phone number of the supplier of the invoice.

Accessor: `supplier_phone_number`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Customer Company Registration</summary>

A list of company registration details including type and number, for the customer of the invoice.

Accessor: `customer_company_registration`

#### Subfields
- **Number**\
  The company registration number.\
  Accessor: `number`\
  Value Type: `string`

- **Type**\
  The type of the company registration number.\
  Accessor: `type`\
  Possible Values: `VAT`, `SIRET`, `SIREN`, `NIF`, `CF`, `UID`, `STNR`, `HRA_HRB`, `TIN`, `RFC`, `BTW`, `ABN`, `UEN`, `CVR`, `ORGNRO`, `INN`, `DPH`, `NIP`, `GSTIN`, `CRN`, `KVK`, `DIC`, `TAX_ID`, `CIF`, `GST_HST_CA`, `COC`

Can have multiple values (is a list/array).

</details>

<details>
<summary>Supplier Company Registration</summary>

A list of company registration details including type and number,  for the supplier of the invoice.

Accessor: `supplier_company_registration`

#### Subfields
- **Number**\
  The company registration number.\
  Accessor: `number`\
  Value Type: `string`

- **Type**\
  The type of the company registration number.\
  Accessor: `type`\
  Possible Values: `VAT`, `SIRET`, `SIREN`, `NIF`, `CF`, `UID`, `STNR`, `HRA_HRB`, `TIN`, `RFC`, `BTW`, `ABN`, `UEN`, `CVR`, `ORGNRO`, `INN`, `DPH`, `NIP`, `GSTIN`, `CRN`, `KVK`, `DIC`, `TAX_ID`, `CIF`, `GST_HST_CA`, `COC`

Can have multiple values (is a list/array).

</details>

<details>
<summary>Invoice Number</summary>

The number of the invoice.

Accessor: `invoice_number`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Date</summary>

The date the invoice was issued.

Accessor: `date`\
Value Type: `date`


Has a single value.

</details>

<details>
<summary>Total Amount</summary>

The final total amount paid, including all taxes and discounts.

Accessor: `total_amount`\
Value Type: `number`


Has a single value.

</details>

<details>
<summary>Total Net</summary>

The total amount before taxes.

Accessor: `total_net`\
Value Type: `number`


Has a single value.

</details>

<details>
<summary>Total Tax</summary>

The total amount of all taxes.

Accessor: `total_tax`\
Value Type: `number`


Has a single value.

</details>

<details>
<summary>Taxes</summary>

A list of individual taxes applied, each including rate, base and amount.

Accessor: `taxes`

#### Subfields
- **Rate**\
  The tax rate of this tax as a decimal.\
  Accessor: `rate`\
  Value Type: `number`

- **Base**\
  The base amount on which this tax is computed.\
  Accessor: `base`\
  Value Type: `number`

- **Amount**\
  The computed tax amount for this tax.\
  Accessor: `amount`\
  Value Type: `number`


Can have multiple values (is a list/array).

</details>

<details>
<summary>Line Items</summary>

A list of line items in the invoice.

Accessor: `line_items`

#### Subfields
- **Description**\
  A description of the item or service.\
  Accessor: `description`\
  Value Type: `string`

- **Quantity**\
  The quantity of the item or service.\
  Accessor: `quantity`\
  Value Type: `number`

- **Unit Price**\
  The price per unit of the item or service.\
  Accessor: `unit_price`\
  Value Type: `number`

- **Total Price**\
  The total price for the line item: quantity * unit price.\
  Accessor: `total_price`\
  Value Type: `number`

- **Product Code**\
  The product code of the item.\
  Accessor: `product_code`\
  Value Type: `string`

- **Tax Amount**\
  The tax amount of the item.\
  Accessor: `tax_amount`\
  Value Type: `number`

- **Tax Rate**\
  The tax rate of the item.\
  Accessor: `tax_rate`\
  Value Type: `number`

- **Unit Measure**\
  The unit of measure of the item.\
  Accessor: `unit_measure`\
  Value Type: `string`


Can have multiple values (is a list/array).

</details>

<details>
<summary>Document Type</summary>

Document type of the financial document.

Accessor: `document_type`\
Possible Values: `invoice`, `payslip`, `quote`, `purchase_order`, `statement`, `receipt`, `credit_note`, `other_financial`

Has a single value.

</details>

<details>
<summary>Locale</summary>

The locale contains the language, country and currency of the invoice.

Accessor: `locale`

#### Subfields
- **Language**\
  The language of the invoice, ISO 639-1 language code.\
  Accessor: `language`\
  Value Type: `string`

- **Country**\
  The country of the invoice, ISO 3166-1 alpha-2.\
  Accessor: `country`\
  Value Type: `string`

- **Currency**\
  The currency in which is issued the invoice, ISO 4217.\
  Accessor: `currency`\
  Value Type: `string`


Has a single value.

</details>

<details>
<summary>Customer Name</summary>

The name of the customer of the invoice.

Accessor: `customer_name`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Customer Address</summary>

The full address of the customer and the breakdown of the address in components.

Accessor: `customer_address`

#### Subfields
- **Address**\
  The full raw address of the customer as written in the document.\
  Accessor: `address`\
  Value Type: `string`

- **Street number**\
  The street number of the address.\
  Accessor: `street_number`\
  Value Type: `string`

- **Street Name**\
  The street name of the address.\
  Accessor: `street_name`\
  Value Type: `string`

- **PO Box**\
  PO Box number, if there is one in the address.\
  Accessor: `po_box`\
  Value Type: `string`

- **Address Complement**\
  Address complement: floor, building, suite, ...\
  Accessor: `address_complement`\
  Value Type: `string`

- **City**\
  The city of the address.\
  Accessor: `city`\
  Value Type: `string`

- **Postal Code**\
  The postal code of the address.\
  Accessor: `postal_code`\
  Value Type: `string`

- **State**\
  The state / region / land of the address, if there is any.\
  Accessor: `state`\
  Value Type: `string`

- **Country**\
  The country of the address.\
  Accessor: `country`\
  Value Type: `string`


Has a single value.

</details>

<details>
<summary>Shipping Address</summary>

The full shipping address and the breakdown of the address in components.

Accessor: `shipping_address`

#### Subfields
- **Address**\
  The full raw shipping address as written in the document.\
  Accessor: `address`\
  Value Type: `string`

- **Street number**\
  The street number of the address.\
  Accessor: `street_number`\
  Value Type: `string`

- **Street Name**\
  The street name of the address.\
  Accessor: `street_name`\
  Value Type: `string`

- **PO Box**\
  PO Box number, if there is one in the address.\
  Accessor: `po_box`\
  Value Type: `string`

- **Address Complement**\
  Address complement: floor, building, suite, ...\
  Accessor: `address_complement`\
  Value Type: `string`

- **City**\
  The city of the address.\
  Accessor: `city`\
  Value Type: `string`

- **Postal Code**\
  The postal code of the address.\
  Accessor: `postal_code`\
  Value Type: `string`

- **State**\
  The state / region / land of the address, if there is any.\
  Accessor: `state`\
  Value Type: `string`

- **Country**\
  The country of the address.\
  Accessor: `country`\
  Value Type: `string`


Has a single value.

</details>

<details>
<summary>Billing Address</summary>

The full billing address and the breakdown of the address in components.

Accessor: `billing_address`

#### Subfields
- **Address**\
  The full full raw billing address as written in the document.\
  Accessor: `address`\
  Value Type: `string`

- **Street number**\
  The street number of the address.\
  Accessor: `street_number`\
  Value Type: `string`

- **Street Name**\
  The street name of the address.\
  Accessor: `street_name`\
  Value Type: `string`

- **PO Box**\
  PO Box number, if there is one in the address.\
  Accessor: `po_box`\
  Value Type: `string`

- **Address Complement**\
  Address complement: floor, building, suite, ...\
  Accessor: `address_complement`\
  Value Type: `string`

- **City**\
  The city of the address.\
  Accessor: `city`\
  Value Type: `string`

- **Postal Code**\
  The postal code of the address.\
  Accessor: `postal_code`\
  Value Type: `string`

- **State**\
  The state / region / land of the address, if there is any.\
  Accessor: `state`\
  Value Type: `string`

- **Country**\
  The country of the address.\
  Accessor: `country`\
  Value Type: `string`


Has a single value.

</details>

<details>
<summary>Supplier Address</summary>

The full address of the supplier and the breakdown of the address in components.

Accessor: `supplier_address`

#### Subfields
- **Address**\
  The full raw supplier address as written in the document.\
  Accessor: `address`\
  Value Type: `string`

- **Street number**\
  The street number of the address.\
  Accessor: `street_number`\
  Value Type: `string`

- **Street Name**\
  The street name of the address.\
  Accessor: `street_name`\
  Value Type: `string`

- **PO Box**\
  PO Box number, if there is one in the address.\
  Accessor: `po_box`\
  Value Type: `string`

- **Address Complement**\
  Address complement: floor, building, suite, ...\
  Accessor: `address_complement`\
  Value Type: `string`

- **City**\
  The city of the address.\
  Accessor: `city`\
  Value Type: `string`

- **Postal Code**\
  The postal code of the address.\
  Accessor: `postal_code`\
  Value Type: `string`

- **State**\
  The state / region / land of the address, if there is any.\
  Accessor: `state`\
  Value Type: `string`

- **Country**\
  The country of the address.\
  Accessor: `country`\
  Value Type: `string`


Has a single value.

</details>

<details>
<summary>Due Date</summary>

The date on which the invoice is due.

Accessor: `due_date`\
Value Type: `date`


Has a single value.

</details>

<details>
<summary>PO Number</summary>

The purchase order number.

Accessor: `po_number`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Reference Numbers</summary>

List of all reference numbers on the invoice, including the purchase order number.

Accessor: `reference_numbers`\
Value Type: `string`


Can have multiple values (is a list/array).

</details>

<details>
<summary>Payment Date</summary>

The date on which the payment is due / was full-filled.

Accessor: `payment_date`\
Value Type: `date`


Has a single value.

</details>

<details>
<summary>Supplier Payment Details</summary>

List of payment details associated to the supplier of the invoice.

Accessor: `supplier_payment_details`

#### Subfields
- **IBAN**\
  The International Bank Account Number (IBAN).\
  Accessor: `iban`\
  Value Type: `string`

- **SWIFT**\
  The bank s SWIFT Business Identifier Code (BIC).\
  Accessor: `swift`\
  Value Type: `string`

- **Account Number**\
  The account number.\
  Accessor: `account_number`\
  Value Type: `string`

- **Routing Number**\
  The routing number.\
  Accessor: `routing_number`\
  Value Type: `string`


Can have multiple values (is a list/array).

</details>

<details>
<summary>Supplier Website</summary>

The website URL of the supplier or merchant.

Accessor: `supplier_website`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Supplier Email</summary>

The email address of the supplier or merchant.

Accessor: `supplier_email`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Customer ID</summary>

The customer account number or identifier from the supplier.

Accessor: `customer_id`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Purchase Category</summary>

The category of the receipt.

Accessor: `category`\
Possible Values: `food`, `gasoline`, `parking`, `toll`, `accommodation`, `transport`, `telecom`, `software`, `shopping`, `energy`, `miscellaneous`

Has a single value.

</details>

<details>
<summary>Purchase Subcategory</summary>

The purchase subcategory of the receipt.

Accessor: `subcategory`\
Possible Values: `restaurant`, `delivery`, `train`, `public`, `taxi`, `car_rental`, `plane`, `micromobility`, `office_supplies`, `electronics`, `cultural`, `groceries`, `other`

Has a single value.

</details>

<details>
<summary>Receipt Number</summary>

The receipt number or identifier only if document is a receipt.

Accessor: `receipt_number`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Document Number</summary>

The document number or identifier (invoice number or receipt number).

Accessor: `document_number`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Tip and Gratuity</summary>

The total amount of tip and gratuity

Accessor: `tip`\
Value Type: `number`


Has a single value.

</details>

<details>
<summary>Purchase Time</summary>

The time the purchase was made (only for receipts).

Accessor: `time`\
Value Type: `string`


Has a single value.

</details>

