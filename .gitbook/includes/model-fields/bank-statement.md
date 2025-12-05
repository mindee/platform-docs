---
title: model-fields_bank-statement
---

## Bank Statement Fields

Documentation for all fields present in the data schema.

Field _accessors_ are used as the keys for accessing the values in the returned data.
On the data schema interface, this is the "Field Name".

Field _value types_ indicate how the value is returned by the API.
On the data schema interface, this is the "Field Type".


<details>
<summary>Account Holder Name</summary>

List of the account holder s names

Accessor: `account_holder_names`\
Value Type: `string`


Can have multiple values (is a list/array).

</details>

<details>
<summary>Account Number</summary>

Account number

Accessor: `account_number`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Statement Period Start Date</summary>

Start date of the statement period

Accessor: `statement_period_start_date`\
Value Type: `date`


Has a single value.

</details>

<details>
<summary>Statement Period End Date</summary>

End date of the statement period

Accessor: `statement_period_end_date`\
Value Type: `date`


Has a single value.

</details>

<details>
<summary>Statement Date</summary>

Date the statement was issued

Accessor: `statement_date`\
Value Type: `date`


Has a single value.

</details>

<details>
<summary>Beginning Balance</summary>

Beginning balance of the statement period

Accessor: `beginning_balance`\
Value Type: `number`


Has a single value.

</details>

<details>
<summary>Ending Balance</summary>

Ending balance of the statement period

Accessor: `ending_balance`\
Value Type: `number`


Has a single value.

</details>

<details>
<summary>List of Transactions</summary>

List of transactions

Accessor: `list_of_transactions`

#### Subfields
- **Date**\
  Date of the transaction\
  Accessor: `date`\
  Value Type: `date`

- **Description**\
  Description of the transaction\
  Accessor: `description`\
  Value Type: `string`

- **Amount**\
  Amount of the transaction\
  Accessor: `amount`\
  Value Type: `number`


Can have multiple values (is a list/array).

</details>

<details>
<summary>Bank Name</summary>

Name of the bank

Accessor: `bank_name`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Account Type</summary>

Type of account

Accessor: `account_type`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Currency</summary>

Currency of the account

Accessor: `currency`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Total Credits</summary>

Total credits for the statement period

Accessor: `total_credits`\
Value Type: `number`


Has a single value.

</details>

<details>
<summary>Total Debits</summary>

Total debits for the statement period

Accessor: `total_debits`\
Value Type: `number`


Has a single value.

</details>

<details>
<summary>Bank Address</summary>

Address of the bank

Accessor: `bank_address`

#### Subfields
- **Address**\
  The full raw address of the bank as written in the document.\
  Accessor: `address`\
  Value Type: `string`

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
<summary>Branch Code</summary>

Branch code of the bank

Accessor: `branch_code`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Daily Balances</summary>

List of daily balances.

Accessor: `daily_balances`

#### Subfields
- **Date**\
  The date of the daily balance item, returned as an ISO formatted string (yyyy-mm-dd).\
  Accessor: `date`\
  Value Type: `date`

- **Balance Amount**\
  Signed number representing the value of the balance.\
  Accessor: `balance_amount`\
  Value Type: `number`


Can have multiple values (is a list/array).

</details>

<details>
<summary>Account Holder Address</summary>

Address of account holder.

Accessor: `account_holder_address`

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
