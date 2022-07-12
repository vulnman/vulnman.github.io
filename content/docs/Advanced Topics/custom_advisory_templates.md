---
categories: []
tags: ["docs"] 
title: "Custom Advisory Templates"
linkTitle: "Custom Advisory Templates"
weight: 50
---

In the vulnman server's `resources/templates/advisory_templates` directory, create a new file with the name of your template.

```
mkdir -p resources/templates/advisory_templates
touch mycooladvisory.md
```



## Use the template

Add the following line to your `local_settings.py` file.
```python
RD_ADVISORY_TEMPLATES = [
    ("default", "Default"),
    ("mycooladvisory", "My Cool Advisory")
]
```
