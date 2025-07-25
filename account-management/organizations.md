---
description: >-
  The Organizations feature in Mindee enables collaborative work around
  workflows. Users can belong to an organization and participate in workflows
  with role-based access control.
noIndex: true
icon: users-rectangle
---

# Organizations

### 👥 Roles

Each organization is governed by a **role system**. A user must be explicitly added to an organization to access it — except for the **creator**, who is automatically granted the `owner` role.

| Role        | Permissions summary                                      |
| ----------- | -------------------------------------------------------- |
| `owner`     | Full control of the workflow                             |
| `admin`     | Can manage members (except owners/admins), edit settings |
| `developer` | Can upload documents, tag files, and manage executions   |
| `approver`  | Can view and validate documents                          |
| `operator`  | Can only view/review executions                          |

{% hint style="warning" %}
⚠️ Only one **owner** per workflow. Ownership is set at creation and cannot be transferred via API.
{% endhint %}

### 🔐 Role Behavior & Rules

* The **creator** of an organization is always set as its `owner` automatically.
* Organization **admins don't have the same right as owners**.
* **Admins cannot promote, edit, or remove owners or other admins**.

### 🔄 Managing Members

These endpoints are available to **organization users** only.

#### ➕ Add a Member

**Role required:** `admin` or `owner`

#### 📋 List Members

**Role required:** `approver` or higher

#### ✏️ Update Member Role

**Role required:** `admin` or `own`

#### ❌ Remove Member

**Role required:** `admin` or `owner`

{% hint style="warning" %}
⚠️ You cannot remove existing `owners` or `admins`.
{% endhint %}

Only users in an **organization** can be assigned roles. Standalone users are considered `owners` by default.
