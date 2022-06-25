---
title: "Permissions in Vulnman"
linkTitle: "Permissions in Vulnman"
weight: 15
description: >
  Explain different permissions and roles in vulnman
---

<div class="alert alert-warning">
<strong>Note:</strong> This is work in progress
For example, the "Management" group does not yet have a independed UI.
Permissions may not be enforced everywhere at the moment!
</div>

Vulnman comes with the following default groups and permission levels:
l

## Groups
`Management`
:   The management group members are allowed to list projects and clients.
The management is allowed to create and update projects.

`Pentesters`
:   The members of the pentester group can be added to different projects.
This will add permissions to the user to change, delete and view the project and its assets.
Pentesters do not have permissions to add contributors to projects (except of the project creator).
Editing clients is forbidden too.


## Project Contributor Roles
If a new contributor is added to a project the following roles are available.

`Read Only`
:   Contributors of this role are not allowed to change assets or other stuff belonging to the project.

`Pentester`
:   Pentesters are allowed to edit project related objects.