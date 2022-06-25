---
categories: []
tags: ["docs"] 
title: "Configuration"
linkTitle: "Configuration"
weight: 7
---

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