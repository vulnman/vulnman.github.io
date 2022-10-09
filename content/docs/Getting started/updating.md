---
categories: []
tags: ["docs"]
title: "Updating Vulnman Server"
linkTitle: "Updating Vulnman Server"
weight: 25
date: 2022-10-09
description: 
---

```bash
cd /opt/vulnman
git pull
pip install -r requirements.txt
python3 manage.py migrate
python3 manage.py collectstatic
```