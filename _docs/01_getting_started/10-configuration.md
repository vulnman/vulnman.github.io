---
title: "Configure Vulnman"
permalink: /docs/getting-started/configuration
excerpt: "Available Settings"
last_modified_at: 2022-03-07T17:00:00
toc: true
---

This section shows how to configure vulnman.


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