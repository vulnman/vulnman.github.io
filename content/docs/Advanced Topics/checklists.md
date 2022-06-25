---
title: "Checklists"
linkTitle: "Checklists"
weight: 70
description:
---

Vulnman provides a simple task management application.
The tasks can be imported from files and are created depending on which assets you test.

Since my current focus is on the core modules, the current checklists are minimalistic and really incomplete.

Feel free to contribute new checklists or improve existing ones.

Currently there is little to consider and the creation is very simple.


## Structure of Checklists

First of all, the default *community checklists* repository is located [here](https://github.com/vulnman/community-checklists).


There are 2 required files for a checklist:
- **info.yaml**: Contains meta data information of the checklist
- **ReadMe.md**: A description of the test that should be performed. You may want to provide background information.

### info.yaml template
```yaml
id: sql-injection
name: SQL-Injection
conditions:
  - service.name: http
  - service.name: https
  - service.port: 80
  - service.port: 443
  - webapplication.always: true
```

The `id` key needs to be unique, while the `name` is just used for display purposes.
The conditions are used to create the task based on different asset attributes.

In the example above, the `sql-injection` task is created, if a service with a name of "http" or "https".
Also if the service port is either 80 or 443.
You can use the keyword `always` to create the task independently of the asset attribute.
