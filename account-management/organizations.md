---
description: >-
  Organizations in Mindee enable collaborative work: users can belong to an
  organization and participate in workspaces with role-based access control.
icon: users-rectangle
---

# Organization & Members

## Access Organization Settings

Click on "<i class="fa-gear">:gear:</i> Settings" in the main menu, then on the "Organization" tab.

Or simply click here: <a href="https://app.mindee.com/settings?tab=organization" class="button primary">Go to Organization page</a>

## Organization Details

Customize the display name of your organization.

Access your Organization ID, a unique identifier generated automatically.

### Default Processing Zone

Set the processing zone used for all models by default.

Most users will want to set the processing zone here rather than at the model level.

## Actions

### Usage Alerts

You can set an alert to receive an email when your [plan](plans.md) has reached a certain percentage of use.

## **Team Members**

The **Team Members** section lists all users who belong to your organization, along with their:

* **Name & Email** – displayed for clarity.
* **Role** – `owner` , `admin` or `member`
* **Status** – shows as _Active_ for members with access.

### Add New Team Members

Use the "Invite Member" button to add a new user.

Enter their email address and select their role.

They will receive an email allowing them to create an account and join your organization.

{% hint style="info" icon="money-check-dollar-pen" %}
You can only invite members to your organization if you have the the Pro, Business, or Enterprise [plans.md](plans.md "mention").
{% endhint %}

### Remove Team Members

Use the "<i class="fa-trash-can">:trash-can:</i>" button to remove a member from your organization.

You must have the `admin` or `owner` role to remove users.

You must have the `owner` role to remove users with the `admin` role.

### Update a Member's Role

Use the "Edit Role" button to change a member's role.

You must have the `admin` or `owner` role to update users.

You must have the `owner` role to update users with the `admin` role.

#### Member Roles

Each organization is governed by a **role system**.

A user must be explicitly added to an organization to access it, except for the **creator**, who is automatically granted the `owner` role.

| Role     | Permissions summary                                                                                                                           |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| `member` | <p>Add and manage models<br>Run Live Tests<br>Manage API keys</p>                                                                             |
| `admin`  | <p>All  <code>member</code> permissions<br>Manage <code>member</code> users</p><p>Update Organization settings<br>Manage Billing settings</p> |
| `owner`  | <p>All <code>admin</code> permissions</p><p>Can add and remove <code>admin</code> users</p>                                                   |

{% hint style="info" %}
Only one `owner` per organization. Ownership is set at creation and cannot be transferred.
{% endhint %}
