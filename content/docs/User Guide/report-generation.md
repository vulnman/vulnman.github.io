---
categories: []
tags: ["docs"] 
title: "Generate Reports"
linkTitle: "Generate Reports"
weight: 5
---


The reports in vulnman are generated from templates.

A simple default template is included, but you may want to [customize](/docs/advanced-topics/report-templates/) it to make it yours.


## Report List
You can have multiple reports for your projects, in case your customer wants to have for example an english, and a german report.

![Project Reports](/attachments/project-report-list.png)


## New Reports
To create a new report, you need to give vulnman some information about the report.

The `name` is just for internal purposes and is displayed in the report list.
The `author` of the report is displayed in the report.
The `title` field is optional and can be used to overwrite the default report title.
You can also choose a report template and language.

![Create Report](/attachments/project-report-create.png)

## The Report
The report requires you to write a management summary using the `Evaluation` and `Recommendation` fields.
Both fields will send a request to the API once you remove the focus of the fields and the content will be stored in the database.

![Report](/attachments/project-report.png)


## Report Releases
A report release is a fixed state of the report.
Once you create a report release the report generator will use the most current information and generates the report.
If you add new vulnerabilities or edit the management summary, you need to create a new report release.

![Report Releases](/attachments/report-release-list.png)

**Note:** There is currently no status indicator of the build process. Depending on the project size, the generation may need some time.

After the report is created, you can click the download button to receive the generated PDF report.

