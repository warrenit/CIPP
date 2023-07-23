---
description: Review members for M365 roles
---

# Roles

The Roles page shows a list of all M365 roles such as Billing Admin, Global Admin etc and allows you to view the members of said group.

### Details

| Fields      | Description                |
| ----------- | -------------------------- |
| Role Name   | The name of the role.      |
| Description | A description of the role. |

[::: note This page only displays Office 365 admin roles. Exchange, Azure IAM, and Pervue rights are outside the scope of this area.\
](#user-content-fn-1)[^1]Only roles with assigned members are displayed. :::

### Actions

* View Members

### API Calls

The following APIs are called on this page:

{% swagger src="../../.gitbook/assets/openapicipp.json" path="/ListRoles" method="get" %}
[openapicipp.json](../../.gitbook/assets/openapicipp.json)
{% endswagger %}

### Feature Requests / Ideas

Please raise any [feature requests](https://github.com/KelvinTegelaar/CIPP/issues/new?assignees=\&labels=\&template=feature\_request.md\&title=FEATURE+REQUEST%3A+) on GitHub.

[^1]: 
