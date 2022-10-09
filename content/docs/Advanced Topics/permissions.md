---
title: "Permissions in Vulnman"
linkTitle: "Permissions in Vulnman"
weight: 15
description: >
  Explain different permissions and roles in vulnman
---

Vulnman comes with the following default roles and permission levels:

## Roles
`Pentesters`
:   The members of the pentester group can be added to different projects.
This will add permissions to the user to change, delete and view the project and its assets.
Pentesters do not have permissions to add contributors to projects (except of the project creator).
Pentesters are allowed to create new clients and create and invite their employees.

`Vendors`
:   A vendor is allowed to use the [Responsible Disclosure](/docs/user-guide/responsible-disclosure-application-usage/)
application. The vendor is allowed to comment on shared vulnerabilities.

`Customers`
:   Customers are low privilged users. They can be added to projects.


## Project Contributor Roles
If a new contributor is added to a project the following roles are available.

`Read Only`
:   Contributors of this role are not allowed to change assets or other stuff belonging to the project.

`Pentester`
:   Pentesters are allowed to edit project related objects.