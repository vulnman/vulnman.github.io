---
categories: []
tags: ["docs"] 
title: "Custom Report Templates"
linkTitle: "Custom Report Templates"
weight: 25
---

In the vulnman server's `resources/templates/report_templates` directory, create a new directory with the name of your template.

```
mkdir -p resources/templates/report_templates/testreport
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


## Translations
Translation files are located in `resources/locale`.

To create the required text files, run the following command:

```bash
cd resources/
django-admin makemessages -l de -i "venv*" -i "apps*" -i "api*" -i "core*" -i "default*"
```
Replace *de* with your language code.
You can now edit the `django.po` file. If you are done, you need to run the following command:

```
django-admin compilemessages
```