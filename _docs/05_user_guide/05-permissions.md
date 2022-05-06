---
title: "Permissions and Groups"
permalink: /docs/user-guide/permissions
excerpt: "Permissions and Groups"
last_modified_at: 2022-05-05T06:00:00
toc: true
---

Vulnman comes with the following default groups and permission levels:

**Note:** This is work in progress.
For example, the "management" group does not yet have a independed UI.
Permissions may not be enforced everywhere at the moment!
{: .notice--warning}


`management`
:   The management group members are allowed to list projects and clients.
The management is allowed to create and update projects.

`pentester`
:   The members of the pentester group can be added to different projects.
This will add permissions to the user to change, delete and view the project and its assets.
Pentesters do not have permissions to add contributors to projects (except of the project creator).
Editing clients is forbidden too.
