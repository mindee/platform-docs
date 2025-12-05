---
title: model-fields_resume
---

Documentation for all fields present in the data schema.

Field _accessors_ are used as the keys for accessing the values in the returned data.
On the data schema interface, this is the "Field Name".

Field _value types_ indicate how the value is returned by the API.
On the data schema interface, this is the "Field Type".


<details>
<summary>Name</summary>

The full name of the resume owner

Accessor: `name`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Address</summary>

The address of the resume owner

Accessor: `address`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Phone Number</summary>

The phone number of the resume owner

Accessor: `phone_number`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Email</summary>

The email address of the resume owner

Accessor: `email`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>LinkedIn Profile</summary>

The LinkedIn profile URL of the resume owner

Accessor: `linkedin_profile`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Education</summary>

List of educational experiences

Accessor: `education`

#### Subfields
- **School Name**\
  The name of the school\
  Accessor: `school_name`\
  Value Type: `string`

- **Degree**\
  The degree obtained\
  Accessor: `degree`\
  Value Type: `string`

- **Dates Attended**\
  The dates the person attended the school\
  Accessor: `dates_attended`\
  Value Type: `string`

- **GPA**\
  The GPA obtained\
  Accessor: `gpa`\
  Value Type: `number`

- **Relevant Coursework**\
  Relevant coursework taken\
  Accessor: `relevant_coursework`\
  Value Type: `string`


Can have multiple values (is a list/array).

</details>

<details>
<summary>Experience</summary>

List of work experiences

Accessor: `experience`

#### Subfields
- **Company Name**\
  The name of the company\
  Accessor: `company_name`\
  Value Type: `string`

- **Job Title**\
  The job title held\
  Accessor: `job_title`\
  Value Type: `string`

- **Dates Employed**\
  The dates the person was employed\
  Accessor: `dates_employed`\
  Value Type: `string`

- **Responsibilities**\
  List of responsibilities\
  Accessor: `responsibilities`\
  Value Type: `string`


Can have multiple values (is a list/array).

</details>

<details>
<summary>Skills</summary>

List of skills

Accessor: `skills`\
Value Type: `string`


Can have multiple values (is a list/array).

</details>

<details>
<summary>Languages</summary>

List of languages and proficiency

Accessor: `languages`

#### Subfields
- **Language**\
  The language\
  Accessor: `language`\
  Value Type: `string`

- **Proficiency**\
  The proficiency level\
  Accessor: `proficiency`\
  Value Type: `string`


Can have multiple values (is a list/array).

</details>

<details>
<summary>Projects</summary>

List of projects

Accessor: `projects`

#### Subfields
- **Project Name**\
  The name of the project\
  Accessor: `project_name`\
  Value Type: `string`

- **Description**\
  The description of the project\
  Accessor: `description`\
  Value Type: `string`

- **Technologies Used**\
  List of technologies used\
  Accessor: `technologies_used`\
  Value Type: `string`


Can have multiple values (is a list/array).

</details>

<details>
<summary>Awards & Certifications</summary>

List of awards and certifications

Accessor: `awards_certifications`

#### Subfields
- **Name**\
  The name of the award or certification\
  Accessor: `name`\
  Value Type: `string`

- **Date Received**\
  The date the award or certification was received\
  Accessor: `date_received`\
  Value Type: `date`


Can have multiple values (is a list/array).

</details>

<details>
<summary>Summary/Objective</summary>

The summary or objective statement

Accessor: `summary_objective`\
Value Type: `string`


Has a single value.

</details>

<details>
<summary>Candidate Photo</summary>

The profile photo of the candidate.

Accessor: `candidate_photo`\
Value Type: `object_detection`


Has a single value.

</details>
