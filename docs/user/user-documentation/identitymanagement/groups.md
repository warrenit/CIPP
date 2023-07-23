---
description: Interact with Microsoft 365 groups.
---

# Groups

Group management. Equivalent to [Microsoft 365 admin center > Active teams and groups](https://admin.microsoft.com/#/groups).

### Details

| Fields        | Description                                       |
| ------------- | ------------------------------------------------- |
| Name          | The name of the group.                            |
| Group Type    | The type of the group, for example Microsoft 365. |
| Dynamic Group | Does the group use dynamic membership rules?      |
| Teams Enabled | Is the group enabled for Microsoft Teams?         |
| On-Prem Sync  | Is the group enabled for on-prem syncronisation?  |
| E-Mail        | The primary e-mail attached to the group.         |

### Actions

#### Edit Group

Edit basic group details. Supported actions:

* Add user to group
* Remove user from group
* Add owner to group
* Remove owner from group
* Allow external senders (Distribution and Microsoft 365 groups)
* Hide from Global Address List (Distribution and Microsoft 365 groups)
* Unhide from Global Address List (Distribution and Microsoft 365 groups)

### API Calls

The following APIs are called on this page:

{% swagger src="../../.gitbook/assets/openapicipp.json" path="/ListGroups" method="get" %}
[openapicipp.json](../../.gitbook/assets/openapicipp.json)
{% endswagger %}

### Feature Requests / Ideas

Please raise any [feature requests](https://github.com/KelvinTegelaar/CIPP/issues/new?assignees=\&labels=\&template=feature\_request.md\&title=FEATURE+REQUEST%3A+) on GitHub.
