---
categories: []
tags: ["docs"]
title: "Configuration"
linkTitle: "Configuration"
weight: 7
---

Have a look at the `local_settings.template.py` file for a more complete and commented example.

## Database
### PostgreSQL
```python
DATABASES = {
  'default': {
    'ENGINE': 'django.db.backends.postgresql',
    'HOST': 'db',
    'NAME': 'vulnman',
    'USER': 'vulnman_db_user',
    'PASSWORD': 'dontusethispassword',
  }
}
```


## Mail
```python
EMAIL_BACKEND = 'django.core.mail.backends.smtp.EmailBackend'
EMAIL_HOST = "smtp.example.com"
EMAIL_PORT = 587
EMAIL_USE_TLS = True
EMAIL_HOST_USER = 'jdoe'
EMAIL_HOST_PASSWORD = 'changme'
DEFAULT_FROM_EMAIL = "jdoe@example.com"
```

## Responsible Disclosure Application
```python
RESPONSIBLE_DISCLOSURE_MAIL_FROM = "responsible-disclosure@example.com"
RESPONSIBLE_DISCLOSURE_VULNERABILITY_ID_PREFIX = "vulnman-"
# Amount of days for the planned publication of the vulnerability details
RESPONSIBLE_DISCLOSURE_PLANNED_PUBLICATION_INTERVAL = 60

# Templates that just provide advisory templates and not a report template
RESPONSIBLE_DISCLOSURE_ADVISORY_TEMPLATES = {
   "myadvisory": "my_ext.advisory.MyAdvisory"
}
```