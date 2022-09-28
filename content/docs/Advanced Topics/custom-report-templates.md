---
categories: []
tags: ["docs"] 
title: "Custom Report Templates"
linkTitle: "Custom Report Templates"
weight: 25
---

You can deploy your own report templates using a python package.

The [default templates repository](https://github.com/vulnman/default-templates) contains a full example of the layout of such a package.


## Enable Report Template
To enable to the report template, add the following lines to your local_settings.py file.

```python

# Report Templates
REPORT_TEMPLATES = {
    "default": 'vulnman_default_templates.report_templates.default_template',
    "my_report": 'my_package.report_templates.my_report'
}


ADDITIONAL_PACKAGES = [
    "my_package"
]
```
The setting above enables both, the default template and your custom one.


## Stylesheets
The report generator will automatically check the existence of the `scss/main.scss` file in the report's template directory.
If this file exists, the stylesheets are automatically used in your report template.


## Template Context
You have the full power of the django templating engine in your report template.


## Translations
Translation files are located in `locale` directory.

To create the required text files, run the following command:

```bash
django-admin makemessages -l de -i "venv*" -i "build*" -i "dist*" -i "my_package.egg-info*"
```
Replace *de* with your language code.
You can now edit the `django.po` file. If you are done, you need to run the following command:

```
django-admin compilemessages
```