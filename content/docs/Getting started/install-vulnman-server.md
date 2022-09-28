---
categories: []
tags: ["docs"]
title: "Install Vulnman Server"
linkTitle: "Install Vulnman Server"
weight: 5
date: 2022-06-20
description: 
---

<div class="alert alert-warning">
    <i class="fa fa-warning"></i>
Vulnman is in a really early stage of development. Feel free to use, test it and please report bugs and other ideas.
You should <b>not</b> use it in production, because there may be breaking changes in the database schema.
</div>

Welcome to the vulnman installation guide! This guide will walk you through
the process of installing vulnman.

## Install Server

### Create User
Since we do not want to run vulnman as root, we create a new user.
```bash
useradd -m vulnman
```

### Install Dependencies

#### Debian
```bash
apt install git python3-pip nginx
```

### Get Code
```bash
cd /opt
git clone https://github.com/vulnman/vulnman.git
cd vulnman/
chown vulnman:vulnman -R .
```

### Install Requirements
Before we start to deploy vulnman, we need to install some dependencies.
```bash
pip install -r requirements.txt
```

## Configure Vulnman
```bash
su - vulnman
cd /opt/vulnman
cp local_settings.template.py vulnman/conf/local_settings.py
exit
```
You may want to read how to [configure](/docs/getting-started/configuration/) your installation.


## Setup Database (optionally)
This is an optional step, which depends on your setup and configuration.
For example, if you plan to use a *sqlite* database, you do not need to do anything from this section.

### PostgreSQL
To Be Done

## Initializing Vulnman
In the next step, we need to initialize vulnman.

```
su - vulnman
cd /opt/vulnman
python manage.py migrate
python manage.py collectstatic
python manage.py createupseruser
exit
```

## Systemd Service
If you want to run the vulnman-server using systemd, you can paste the following
content into the `/etc/systemd/system/vulnman-server.service` file.

```
[Unit]
Description=vulnman server
After=network.target

[Service]
User=vulnman
Group=vulnman
WorkingDirectory=/opt/vulnman
ExecStart=gunicorn --bind 127.0.0.1:8000 vulnman.wsgi

[Install]
WantedBy=multi-user.target
```

To enable the service on boot and start the vulnman service, you can use the following commands:

```bash
systemctl start vulnman-server
systemctl enable vulnman-server
```

For the `qcluster` which is for example used to create the reports, create a file `/etc/systemd/system/vulnman-qcluster.service` file.

```
[Unit]
Description=vulnman server
After=network.target

[Service]
User=vulnman
Group=vulnman
WorkingDirectory=/opt/vulnman
ExecStart=python3 manage.py qcluster

[Install]
WantedBy=multi-user.target
```

```bash
systemctl start vulnman-qcluster
systemctl enable vulnman-qcluster
```


## Setup Nginx

Paste the following content into the `/etc/nginx/conf.d/vulnman.conf` file.
You may want to further hardening the TLS configuration, which is not part of this guide.

```
server {
    listen 80 default_server;
    server_tokens off;
    return 301 https://$host$request_uri;
}

server {
    listen 443 ssl;
    server_name _;
    server_tokens off;

    ssl_certificate /etc/ssl/yourcert.crt;
    ssl_certificate_key /etc/ssl/yourcertkey.key;

    ssl_protocols TLSv1.3;
    ssl_prefer_server_ciphers on;
    ssl_ciphers ECDH+AESGCM:ECDH+AES256:ECDH+AES128:DH+3DES:!ADH:!AECDH:!MD5;

    location / {
        proxy_pass http://127.0.0.1:8000;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
	proxy_set_header Host $host;
    }
    location /static/ {
        alias /opt/vulnman/static_files/;
    }

    location /uploads/ {
        alias /opt/vulnman/uploads/;
    }

    add_header X-XSS-Protection '1; mode=block';
    add_header Strict-Transport-Security "max-age=31536000; includeSubDomains" always;
    add_header Referer-Policy 'strict-origin';
    add_header X-Frame-Options 'SAMEORIGIN';
    add_header X-Content-Type-Options 'nosniff';
}
```

## Import Default Templates (optionally)
If you want to use our (currently quite small) default templates, run the following command:

```bash
su - vulnman
cd /opt/vulnman
python3 manage.py import_vulnerability_templates vulnman_default_templates
exit
```
