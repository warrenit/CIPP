---
description: Offboard the selected user with standard requirements
---

# Offboarding Wizard

### Overview

With the Offboarding Wizard you can select a user in a tenant to off-board whilst optionally removing licences, setting out of office and delegating access to mail or files. You can also use this wizard as a method of easily setting a users Out Of Office.

### Available Tasks

* Remove Licences
* Convert to Shared Mailbox
* Disable Sign-In
* Reset Password
* Remove from all Groups
* Hide from Global Address List
* Set Out of Office
* Give access to mailbox (without auto mapping)
* Give access to mailbox (with auto mapping)
* Give access to OneDrive
* Delete User

### API Calls

The following APIs are called on this page:



{% swagger src="../../.gitbook/assets/openapicipp.json" path="/ExecOffboardUser" method="post" %}
[openapicipp.json](../../.gitbook/assets/openapicipp.json)
{% endswagger %}

{% swagger src="../../.gitbook/assets/openapicipp.json" path="/ListUsers" method="get" %}
[openapicipp.json](../../.gitbook/assets/openapicipp.json)
{% endswagger %}

### Feature Requests / Ideas

Please raise any [feature requests](https://github.com/KelvinTegelaar/CIPP/issues/new?assignees=\&labels=\&template=feature\_request.md\&title=FEATURE+REQUEST%3A+) on GitHub.
