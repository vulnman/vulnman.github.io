---
categories: []
tags: ["docs"] 
title: "LDAP Authentication"
linkTitle: "LDAP Authentication"
weight: 5
---

In the first step, you need to install `django-auth-ldap`.
This can be done with pip.

```
pip install django-auth-ldap
```

## Settings
Add the following lines to your [local_settings.py](/docs/getting-started/configuration) file.

```python
##############
# LDAP
# You need to install `django-auth-ldap` to use LDAP authentication
# See https://django-auth-ldap.readthedocs.io/en/latest/install.html for library usage
##############

import ldap
from django_auth_ldap.config import LDAPSearch, PosixGroupType

AUTH_LDAP_BIND_DN = "cn=admin,dc=example,dc=org"
AUTH_LDAP_BIND_PASSWORD = "admin"
AUTH_LDAP_USER_SEARCH = LDAPSearch(
    "ou=Users,dc=example,dc=org", ldap.SCOPE_SUBTREE, "(uid=%(user)s)"
)

AUTH_LDAP_FIND_GROUP_PERMS = True
AUTH_LDAP_CACHE_TIMEOUT = 3600
AUTH_LDAP_SERVER_URI = "ldap://172.17.0.2"

AUTH_LDAP_GROUP_TYPE = PosixGroupType(name_attr='cn')
AUTH_LDAP_GROUP_SEARCH = LDAPSearch(
    'ou=Groups,dc=example,dc=org',
    ldap.SCOPE_SUBTREE,
    '(objectClass=posixGroup)',
)

AUTH_LDAP_USER_ATTR_MAP = {
    "first_name": "givenName", "last_name": "sn",
    "email": "mail"
}
```