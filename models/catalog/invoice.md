# Invoice

Documentation for the data schema of the Invoice model.

## Invoice Fields

Documentation for all fields present in the data schema.

Field _accessors_ are used as the keys for accessing the values in the returned data.
On the data schema interface, this is the "Field Name".

Field _value types_ indicate how the value is returned by the API.
On the data schema interface, this is the "Field Type".

### Supplier Name

The name of the supplier of the invoice.

Accessor: `supplier_name`\
Value Type: `string`

Has a single value.

### Supplier Phone Number

The phone number of the supplier of the invoice.

Accessor: `supplier_phone_number`\
Value Type: `string`

Has a single value.

### Customer Company Registration

A list of company registration details including type and number, for the customer of the invoice.

Accessor: `customer_company_registration`

Can have multiple values (is a list/array).

### Supplier Company Registration

A list of company registration details including type and number,  for the supplier of the invoice.

Accessor: `supplier_company_registration`

Can have multiple values (is a list/array).

### Invoice Number

The number of the invoice.

Accessor: `invoice_number`\
Value Type: `string`

Has a single value.

### Date

The date the invoice was issued.

Accessor: `date`\
Value Type: `date`

Has a single value.

### Total Amount

The final total amount paid, including all taxes and discounts.

Accessor: `total_amount`\
Value Type: `number`

Has a single value.

### Total Net

The total amount before taxes.

Accessor: `total_net`\
Value Type: `number`

Has a single value.

### Total Tax

The total amount of all taxes.

Accessor: `total_tax`\
Value Type: `number`

Has a single value.

### Taxes

A list of individual taxes applied, each including rate, base and amount.

Accessor: `taxes`

Can have multiple values (is a list/array).

### Line Items

A list of line items in the invoice.

Accessor: `line_items`

Can have multiple values (is a list/array).

### Document Type

Document type of the financial document.

Accessor: `document_type`\
Possible Values: `invoice`, `payslip`, `quote`, `purchase_order`, `statement`, `receipt`, `credit_note`, `other_financial`

Has a single value.

### Locale

The locale contains the language, country and currency of the invoice.

Accessor: `locale`

Has a single value.

### Customer Name

The name of the customer of the invoice.

Accessor: `customer_name`\
Value Type: `string`

Has a single value.

### Customer Address

The full address of the customer and the breakdown of the address in components.

Accessor: `customer_address`

Has a single value.

### Shipping Address

The full shipping address and the breakdown of the address in components.

Accessor: `shipping_address`

Has a single value.

### Billing Address

The full billing address and the breakdown of the address in components.

Accessor: `billing_address`

Has a single value.

### Supplier Address

The full address of the supplier and the breakdown of the address in components.

Accessor: `supplier_address`

Has a single value.

### Due Date

The date on which the invoice is due.

Accessor: `due_date`\
Value Type: `date`

Has a single value.

### PO Number

The purchase order number.

Accessor: `po_number`\
Value Type: `string`

Has a single value.

### Reference Numbers

List of all reference numbers on the invoice, including the purchase order number.

Accessor: `reference_numbers`\
Value Type: `string`

Can have multiple values (is a list/array).

### Payment Date

The date on which the payment is due / was full-filled.

Accessor: `payment_date`\
Value Type: `date`

Has a single value.

### Supplier Payment Details

List of payment details associated to the supplier of the invoice.

Accessor: `supplier_payment_details`

Can have multiple values (is a list/array).

### Supplier Website

The website URL of the supplier or merchant.

Accessor: `supplier_website`\
Value Type: `string`

Has a single value.

### Supplier Email

The email address of the supplier or merchant.

Accessor: `supplier_email`\
Value Type: `string`

Has a single value.

### Customer ID

The customer account number or identifier from the supplier.

Accessor: `customer_id`\
Value Type: `string`

Has a single value.
