---
description: >-
  The Organizations feature in Mindee enables collaborative work: users can
  belong to an organization and participate in workspaces with role-based access
  control.
icon: users-rectangle
---

# Organizations

## Organization Settings

When you go to **Settings > Organization** in the Mindee platform, you can:

### **Edit Organization Details**

* _Organization Name_: Customize the display name of your organization.
* _Organization ID_: A unique identifier generated automatically (read-only).

### **Manage Team Members**

The **Team Members** section lists all users who belong to your organization, along with their:

* **Name & Email** – displayed for clarity.
* **Role** – `owner` , `admin` or `member`
* **Status** – shows as _Active_ for members with access.

### **Actions on Members**

* **Invite Member**: Use the _Invite Member_ button to add a new user by email.
* **Update Role**: If you are `owner` or `admin`, you can change a member’s role (within the limits described in Role Behavior & Rules).
* **Remove Member**: Available for `admin` and `owner`, except for existing owners or admins (cannot be removed as per restrictions).

{% hint style="info" %}
You can only invite members to your organization if you have the Pro plan or above.
{% endhint %}

## How do Roles Work?

Each organization is governed by a **role system**. A user must be explicitly added to an organization to access it — except for the **creator**, who is automatically granted the `owner` role.

| Role     | Permissions summary                                      |
| -------- | -------------------------------------------------------- |
| `owner`  | Full control of the workspace                            |
| `admin`  | Can manage members (except owners/admins), edit settings |
| `member` | Can only view/review executions                          |

{% hint style="warning" %}
⚠️ Only one **owner** per organization. Ownership is set at creation and cannot be transferred via API.
{% endhint %}

### Role Behavior & Rules

* The **creator** of an organization is always set as its `owner` automatically.
* **Admins cannot promote, edit, or remove owners or other admins**.

## Managing Members

These endpoints are available to **organization users** only.

#### Add a Member

**Role required:** `admin` or `owner`

#### Update Member Role

**Role required:** `admin` or `owner`

#### Remove Member

**Role required:** `admin` or `owner`

{% hint style="warning" %}
You cannot remove existing `owners` or `admins`.
{% endhint %}

Only users in an **organization** can be assigned roles. Standalone users are considered `owners` by default.
