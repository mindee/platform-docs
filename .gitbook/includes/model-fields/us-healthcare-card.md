---
title: model-fields_us-healthcare-card
---

Documentation for all fields present in the data schema.

Field _accessors_ are used as the keys for accessing the values in the returned data.
On the data schema interface, this is the "Field Name".

Field _value types_ indicate how the value is returned by the API.
On the data schema interface, this is the "Field Type".


<details>
<summary>Company Name</summary>

The name of the company that provides the healthcare plan

Accessor: `company_name`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Plan Name</summary>

The name of the healthcare plan

Accessor: `plan_name`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Member Name</summary>

The name of the member covered by the healthcare plan

Accessor: `member_name`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Member ID</summary>

The unique identifier for the member in the healthcare system

Accessor: `member_id`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Issuer 80840</summary>

The organization that issued the healthcare plan

Accessor: `issuer_80840`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Dependents</summary>

The list of dependents covered by the healthcare plan

Accessor: `dependents`\
Value Type: `string`


Can have multiple values (is a list/array).

</details>

<details>
<summary>Group Number</summary>

The group number associated with the healthcare plan

Accessor: `group_number`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Payer ID</summary>

The unique identifier for the payer in the healthcare system

Accessor: `payer_id`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Rx BIN</summary>

The BIN number for prescription drug coverage

Accessor: `rx_bin`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Rx ID</summary>

The ID number for prescription drug coverage

Accessor: `rx_id`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Rx Grp</summary>

The group number for prescription drug coverage

Accessor: `rx_grp`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Rx PCN</summary>

The PCN number for prescription drug coverage

Accessor: `rx_pcn`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Copayments</summary>

Copayments for covered services.

Accessor: `copayments`

#### Subfields
- **Service Name**\
  Service name\
  Accessor: `service_name`\
  Possible Values: `primary_care`, `emergency_room`, `urgent_care`, `specialist`, `office_visit`, `prescription`
- **Service Fees**\
  Service price\
  Accessor: `service_fees`\
  Value Type: `number`


Can have multiple values (is a list/array).

</details>

<details>
<summary>Enrollment Date</summary>

The date when the member enrolled in the healthcare plan

Accessor: `enrollment_date`\
Value Type: `date`


Has a single value.

</details>
