---
title: model-fields_payslip
---

Documentation for all fields present in the data schema.

Field _accessors_ are used as the keys for accessing the values in the returned data.
On the data schema interface, this is the "Field Name".

Field _value types_ indicate how the value is returned by the API.
On the data schema interface, this is the "Field Type".


<details>
<summary>First Name</summary>

Employee's first name

Accessor: `first_name`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Last Name</summary>

Employee's last name

Accessor: `last_name`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Employee Address</summary>

Employee's address

Accessor: `employee_address`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Pay Period Start Date</summary>

Start date of the pay period

Accessor: `pay_period_start_date`\
Value Type: `date`


Has a single value.

</details>

<details>
<summary>Pay Period End Date</summary>

End date of the pay period

Accessor: `pay_period_end_date`\
Value Type: `date`


Has a single value.

</details>

<details>
<summary>Gross Pay</summary>

Gross pay amount

Accessor: `gross_pay`\
Value Type: `number`


Has a single value.

</details>

<details>
<summary>Net Pay</summary>

Net pay amount

Accessor: `net_pay`\
Value Type: `number`


Has a single value.

</details>

<details>
<summary>Deductions</summary>

List of deductions

Accessor: `deductions`

#### Subfields
- **Name**\
  Name of the deduction\
  Accessor: `name`\
  Value Type: `string`

- **Amount**\
  Amount of the deduction\
  Accessor: `amount`\
  Value Type: `number`


Can have multiple values (is a list/array).

</details>

<details>
<summary>Taxes</summary>

List of taxes

Accessor: `taxes`

#### Subfields
- **Name**\
  Name of the tax\
  Accessor: `name`\
  Value Type: `string`

- **Amount**\
  Amount of the tax\
  Accessor: `amount`\
  Value Type: `number`


Can have multiple values (is a list/array).

</details>

<details>
<summary>Employer Name</summary>

Name of the employer

Accessor: `employer_name`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Employer Address</summary>

Address of the employer

Accessor: `employer_address`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Social Security Number</summary>

Employee's Social Security Number

Accessor: `social_security_number`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Employee ID</summary>

Employee's ID

Accessor: `employee_id`\
Value Type: `string`


Has a single value.

</details>
