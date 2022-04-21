---
title: "Documentation"
permalink: /docs/
excerpt: "Vulnman documentation."
last_modified_at: 2022-03-07T17:00:00
toc: true
---

Vulnman is an open source web application to manage pentest projects, vulnerability and other related assets.
The report generator allows you to create custom templates containing all your necessary styles and information for your customers.

It has been developed using the powerful [django framework](https://www.djangoproject.com/).

**Note:** Vulnman is in a really early stage of development. Feel free to use, test it and please report bugs and other ideas.
You should **not** use it in production, because there may be breaking changes in the database schema.
{: .notice--warning}


## Features
- Unlimited projects
- Unlimited users
- Easy pentest report generation based on information stored in the project
- Customizable report template
- Markdown syntax supported (mostly)
- Vulnerability templates
   - Templates can be imported from YAML files
- Vulnerability management
   - CVSS
   - Add proof of concepts so your customer can reproduce the vulnerability
- Manage To Dos (checklists) during a pentest
   - Import checklist from YAML and Markdown files
- Manage assets of projects like:
   - Hosts
   - Web Applications
   - Web Requests
   - Services

## Source Code
All source code is available on [Github](https://github.com/vulnman).
