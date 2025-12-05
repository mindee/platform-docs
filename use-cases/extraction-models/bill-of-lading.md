---
icon: ship
---

# Bill of Lading

Documentation for the data schema of the Bill of Lading model.

## Bill of Lading Fields

Documentation for all fields present in the data schema.

Field _accessors_ are used as the keys for accessing the values in the returned data.
On the data schema interface, this is the "Field Name".

Field _value types_ indicate how the value is returned by the API.
On the data schema interface, this is the "Field Type".


<details>
<summary>Bill of Lading Number</summary>

A unique identifier assigned to a Bill of Lading document

Accessor: `bill_of_lading_number`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Shipper</summary>

The party responsible for shipping the goods

Accessor: `shipper`

#### Subfields
- **Name**\
  Shipper s name\
  Accessor: `name`\
  Value Type: `string`

- **Address**\
  Shipper s address\
  Accessor: `address`\
  Value Type: `string`

- **Phone**\
  Shipper s phone number\
  Accessor: `phone`\
  Value Type: `string`

- **Email**\
  Shipper s email address\
  Accessor: `email`\
  Value Type: `string`


Has a single value.

</details>

<details>
<summary>Consignee</summary>

The party to whom the goods are being shipped

Accessor: `consignee`

#### Subfields
- **Name**\
  Consignee s name\
  Accessor: `name`\
  Value Type: `string`

- **Address**\
  Consignee s address\
  Accessor: `address`\
  Value Type: `string`

- **Phone**\
  Consignee s phone number\
  Accessor: `phone`\
  Value Type: `string`

- **Email**\
  Consignee s email address\
  Accessor: `email`\
  Value Type: `string`


Has a single value.

</details>

<details>
<summary>Notify Party</summary>

The party to be notified of the arrival of the goods

Accessor: `notify_party`

#### Subfields
- **Name**\
  Notify party s name\
  Accessor: `name`\
  Value Type: `string`

- **Address**\
  Notify party s address\
  Accessor: `address`\
  Value Type: `string`

- **Phone**\
  Notify party s phone number\
  Accessor: `phone`\
  Value Type: `string`

- **Email**\
  Notify party s email address\
  Accessor: `email`\
  Value Type: `string`


Has a single value.

</details>

<details>
<summary>Carrier</summary>

The shipping company responsible for transporting the goods

Accessor: `carrier`

#### Subfields
- **Name**\
  Carrier s name\
  Accessor: `name`\
  Value Type: `string`

- **Professional Number**\
  Carrier s professional number\
  Accessor: `professional_number`\
  Value Type: `string`

- **SCAC**\
  Carrier s SCAC code\
  Accessor: `scac`\
  Value Type: `string`


Has a single value.

</details>

<details>
<summary>Carrier Items</summary>

The goods being shipped

Accessor: `carrier_items`

#### Subfields
- **Description**\
  Description of the item\
  Accessor: `description`\
  Value Type: `string`

- **Quantity**\
  Quantity of the item\
  Accessor: `quantity`\
  Value Type: `number`

- **Gross Weight**\
  Gross weight of the item\
  Accessor: `gross_weight`\
  Value Type: `number`

- **Weight Unit**\
  Unit of weight\
  Accessor: `weight_unit`\
  Value Type: `string`

- **Measurement**\
  Measurement of the item\
  Accessor: `measurement`\
  Value Type: `number`

- **Measurement Unit**\
  Unit of measurement\
  Accessor: `measurement_unit`\
  Value Type: `string`


Can have multiple values (is a list/array).

</details>

<details>
<summary>Port of Loading</summary>

The port where the goods are loaded onto the vessel

Accessor: `port_of_loading`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Port of Discharge</summary>

The port where the goods are unloaded from the vessel

Accessor: `port_of_discharge`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Place of Delivery</summary>

The place where the goods are to be delivered

Accessor: `place_of_delivery`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Issue Date</summary>

The date when the bill of lading is issued.

Accessor: `issue_date`\
Value Type: `date`


Has a single value.

</details>

<details>
<summary>Departure Date</summary>

The date when the vessel departs from the port of loading

Accessor: `departure_date`\
Value Type: `date`


Has a single value.

</details>
