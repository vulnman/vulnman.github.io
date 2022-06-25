
---
title: "Glossary"
linkTitle: "Glossary"
toc_hide: true
hide_summary: true
weight: 1
date: 2022-06-20
description:
---

Vulnman consists of several components.
These are presented in this section.

The Vulnman Server is the core component.
This provides a REST API and a web interface for easy management of pentest assets during a penetration test.


## Core
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

- **Vulnerability Templates:** Vulnerability templates are managed using a [separate repository](/doc/vulnerability-templates/).
This allows other external tools to introduce these templates too.
These templates are used to derive basic information for your found vulnerabilities.

- **Vulnerability:** A vulnerability is a security flaw that you found during the project.
Vulnerabilities have a template.
The default severity is inherited from the template but can be overwritten for each vulnerability.
