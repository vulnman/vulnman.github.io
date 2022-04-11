---
title: Components and Glossary
permalink: /docs/user-guide/glossary
excerpt: "Introduce vulnman components"
last_modified_at: 2022-03-11T19:00:00
toc: true
---

Vulnman consists of several components.
These are presented in this section.

The Vulnman Server is the core component.
This provides a REST API and a web interface for easy management of pentest assets during a penetration test.


## Glossary
Vulnman introduces different components that you will see in the web interface
or external tools.
The components are explained below.

- **Client:** Clients are the customers of your projects.
Client contact information provided can be added to the pentest report.

- **Project:** A project is the container of your assessment.
It contains all tested assets, findings and reports.

- **Assets:** Vulnman supports multiple assets that can be
created through the REST-API or through the web interface.
The following assets are supported:
    - Service
    - Host
    - Web Application
    - Web Request

- **Report:** There are different types of pentest reports.
A draft report contains a *draft* watermark, while *release* versions does not.
You can store multiple versions of your report.

- **Vulnerability Templates:** Vulnerability templates are [managed](/docs/developer/contribute-vulnerability-templates) using a separate repository.
This allows other external tools to introduce these templates too.
These templates are used to derive basic information for your found vulnerabilities.

- **Vulnerability:** A vulnerability is a security flaw that you found during the project.
Vulnerabilities have a template.
The default severity is inherited from the template but can be overwritten for each vulnerability.
