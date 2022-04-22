---
title: "Install Vulnman"
permalink: /docs/getting-started/install
excerpt: "How to quickly install and setup Vulnman."
last_modified_at: 2022-03-07T17:00:00
toc: true
---

## Without Docker

### Requirements

#### Fedora
```bash
sudo dnf install python3 nginx git
sudo pip install -r requirements.txt
```

#### Arch-Linux

```
sudo pacman -Sy python nginx git
sudo pip install -r requirements.txt
```

### Prepare
First we fetch the source code.

```bash
mkdir /opt/vulnman-server
git clone https://github.com/vulnman/vulnman.git
cd /opt/vulnman-server/vulnman
cp local_settings.template.py local_settings.py
```


### Configure Database
The default settings will use a sqlite database.
If you are fine with this you can continue with this tutorial.
Otherwise, you may want to read how to [configure](/docs/getting-started/configuration) your installation.


### Initializing Vulnman
In the next step, we need to initialize vulnman.

```bash
python manage.py migrate
python manage.py collectstatic
python manage.py createupseruser
```

### Systemd Service
If you want to run the vulnman-server using systemd, you can paste the following
content into the `/etc/systemd/system/vulnman-server.service` file.

```
[Unit]
Description=vulnman server
After=network.target

[Service]
User=user
Group=user
WorkingDirectory=/opt/vulnman-server
ExecStart=gunicorn --bind 127.0.0.1:8000 vulnman.wsgi

[Install]
WantedBy=multi-user.target
```

To enable the service on boot and start the vulnman service, you can use the following commands:

```bash
sudo systemctl start vulnman-server
sudo systemctl enable vulnman-server
```

### Setup Nginx

Paste the following content into the `/etc/nginx/sites-enabled/vulnman.conf` file

```
server {
    listen 80;
    return https://$host$request_uri;
}

server {
    listen 443 ssl;
    ssl_certificate_key /etc/ssl/your_cert.key;
    ssl_certificate /etc/ssl/your_cert.crt;
    ssl_protocols TLSv1.3;

    location / {
        proxy_pass http://127.0.0.1:8000;
    }
}
```

## With docker-compose

Adjust the credentials and paths in the `docker-compose.yml` file.

For the docker image to work, you need to set up vulnman to use a [postgres database](/docs/getting-started/configuration#postgresql).

To make the report generation work, add the following lines to your `local_settings.py` file:

```
CELERY_BROKER_URL = "redis://redis:6379"
CELERY_RESULT_BACKEND = "redis://redis:6379"
```

A basic settings example for the docker setup is shown below:

```
CELERY_BROKER_URL = "redis://redis:6379"
CELERY_RESULT_BACKEND = "redis://redis:6379"


DATABASES = {
  'default': {
    'ENGINE': 'django.db.backends.postgresql',
    'HOST': 'db',
    'NAME': 'vulnman',
    'USER': 'vulnman_db_user',
    'PASSWORD': 'dontusethispassword',
  }
}

ALLOWED_HOSTS = ["vulnman-web"]
# Add your host and schema here: ["https://mydomain.com", "http://mydomain.com"]
CSRF_TRUSTED_ORIGINS = ["http://localhost", "https://localhost"]
```


You can start all containers with the following command:

```bash
sudo docker-compose up --build
```


## Initial Setup
After you have installed vulnman you may want to import the default vulnerability templates and checklist.

### Import Vulnerability Templates
```bash
python manage.py update_vulnerability_templates
```

*Note: If you want to get automatic updates for vulnerability templates. You may want to create a cronjob for the command above.*

### Import Checklists
```bash
python manage.py update_checklists
```

*Note: If you want to get automatic updates for the checklists. You may want to create a cronjob for the command above.*
