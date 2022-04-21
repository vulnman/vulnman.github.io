---
title: Introducing the Web Interface
permalink: /docs/user-guide/intro-web-interface
excerpt: "Introducing the Web Interface"
last_modified_at: 2022-04-21T19:30:00
toc: true
---

The web interface allows you to manage your pentest and its assets using a user interface.

You can visit the vulnman server by opening your instance from within your browser.
The application needs you to be logged in.

![Login Screen](/assets/images/attachments/login-web-ui.png)

After you logged in, you will be redirected to the list of your current (non archived) projects.
By clicking on one of the projects, you are able to *activate* the project and see its details and do your work.


## Project Dashboard
The project dashboard is the home of your project.
It gives you a short overview about the state of your project.

![Dashboard](/assets/images/attachments/web_dashboard.png)

It contains the remaining time for the project, different counts like how many vulnerabilities were found and open to dos are left.

You can close the project through the `X` button.
Closing a project makes it read-only.

If for some reasons you forgot your role in the project, you can found it here - in the top left of the dashboard.

A sidebar will be available with project related actions.


## The Sidebar
The sidebar only contains project related links, while the top bar include *global* links.
The sidebar is devided into different *categories*.

**Pentest:**

The pentest group contains links to your project's dashboard, vulnerabilities, tasks, user accounts and project tokens.

**Assets:**

In this group you can create and manage your assets.

**Management:**

This group handels links to manage the project. Currently there is just one item in here, which allows you to add or remove contributors.
It is important to know, that you need permissions to do so. By default, the project creator user will be able to remove or add contributors.

**Reporting:**

Here you can create new reports or download existing one.
You can write the management summary here.


## Reporting
This page allows you to manage your project's reports.

![Report Management Page](/assets/images/attachments/reporting-ui.png)

A general draft report can be created. This report will not have a named, unchangable version.
If you click on the `Create Draft` button, it will create, and overwrite the previous, report.

If you need a new persisted version of your reports, you must click on `Create Report`.
This will open a new window, where you can choose between the report types "Release" and "Draft".
This version will not be overwritten by other reports.

The management summary fields `Evaluation` and `Recommendation` supports markdown syntax.
If your cursor leaves the focus of the field, the data is saved into the database and will appear in your next reports.
