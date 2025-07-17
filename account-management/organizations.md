---
description: >-
  The Organizations feature in Mindee enables collaborative work around
  workflows. Users can belong to an organization and participate in workflows
  with role-based access control.
noIndex: true
icon: users-rectangle
---

# Organizations

### 👥 Roles in a Workflow

Each workflow in an organization is governed by a **role system**. A user must be explicitly added to a workflow to access it — except for the **creator**, who is automatically granted the `owner` role.

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

* The **creator** of a workflow is always set as its `owner` automatically.
* Organization **admins are not automatically admins** on all workflows.
* **Admins cannot promote, edit, or remove owners or other admins**.
* Users outside of organizations (standalone accounts) are treated as `owners` on all their workflows — no roles are enforced.

***

### 📥 Role Visibility in API Responses

Every endpoint that includes a `workflow_id` in the path returns a `X-Allowed-Roles` header indicating the roles the current user holds, in ascending hierarchy:

```
operator
operator,approver
operator,approver,developer
operator,approver,developer,admin
operator,approver,developer,admin,owner
```

Use this to manage conditional UI display on the frontend.

***

### 🔄 Managing Workflow Members

These endpoints are available to **organization users** only.

#### ➕ Add a Member

**Role required:** `admin` or `owner`

```http
POST /workflow_id/members
```

**Body:**

```json
{
  "user_id": "abc123",
  "role": "operator" // or approver, developer, admin
}
```

**Response:**

```json
{
  "workflow_id": "...",
  "user_id": "...",
  "role": "...",
  "has_pending_invitation": true
}
```

{% hint style="success" %}
✅ `user_id` must already exist in your organization.
{% endhint %}

#### 📋 List Members

**Role required:** `approver` or higher\
Returns all workflow members, sorted by role (descending).

```http
GET /workflow_id/members
```

#### ✏️ Update Member Role

**Role required:** `admin` or `owner`

```http
PATCH /workflow_id/members/user_id
```

Body:

```json
{
  "role": "developer"
}
```

{% hint style="warning" %}
⚠️ You cannot promote anyone to `admin` or `owner` via API.
{% endhint %}

#### ❌ Remove Member

**Role required:** `admin` or `owner`

```http
DELETE /workflow_id/members/user_id
```

{% hint style="warning" %}
⚠️ You cannot remove existing `owners` or `admins`.
{% endhint %}

### ⚙️ Workflow Action Permissions

Only users in an **organization** can be assigned roles. Standalone users are considered `owners` by default.

| Action                                                                                                     | Minimum Required Role |
| ---------------------------------------------------------------------------------------------------------- | --------------------- |
| `create_workflow`                                                                                          | organization `admin`  |
| `get_workflow`, `list_workflows`                                                                           | `operator`            |
| `update_workflow`                                                                                          | `admin`               |
| `archive_workflow`                                                                                         | `owner`               |
| `create_execution`                                                                                         | `developer`           |
| `review_execution`, `get_execution`                                                                        | `operator`            |
| `update_execution`, `remove_execution`                                                                     | `developer`           |
| `create_export`, `list_exports`, `download_export`, `create_batch`                                         | `operator`            |
| `archive_export`                                                                                           | `developer`           |
| `create_learning_document`, `list_learning_documents`, `get_learning_document`, `update_learning_document` | `developer`           |
| `create_member`, `update_member`, `remove_member`                                                          | `admin`               |
| `list_members`                                                                                             | `approver`            |

