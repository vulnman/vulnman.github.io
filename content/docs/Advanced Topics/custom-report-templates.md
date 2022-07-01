---
categories: []
tags: ["docs"] 
title: "Custom Report Templates"
linkTitle: "Custom Report Templates"
weight: 25
---

In the vulnman server's `resources/templates/report_templates` directory, create a new directory with the name of your template.

```
mkdir testreport
```

You need at least two files in this directory:

1. `report.html`: The Entrypoint (or whole) HTML report
2. `exported_vulnerability.html`: This file is used to export a single vulnerability

**Note: instead of starting from scratch, you may want to copy the default's template directory and customize it.**


## Enable Report Template
To enable to the report template, add the following lines to your local_settings.py file.

```python
REPORT_TEMPLATES = {
    "default": {
        "CSS": ["css/fontawesome.min.css", "css/codehilite.css"]
    },
    "testreport": {
        "CSS": []
    }
}
```
The setting above enables both, the default template and your custom one.


## Stylesheets
The report generator will automatically check the existence of the `scss/main.scss` file in the report's template directory.
If this file exists, the stylesheets are automatically used in your report template.


## Template Context
You have the full power of the django templating engine in your report template.
