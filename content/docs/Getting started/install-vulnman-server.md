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




## With Docker

Adjust the credentials and paths in the [docker-compose.yml](https://github.com/vulnman/vulnman/blob/main/docker-compose.yml) file.

```bash
wget https://raw.githubusercontent.com/vulnman/vulnman/main/docker-compose.yml
```

**Note:** The main branch is used for development and is not considered production-ready. 
You may want to fetch the `docker-compose.yml` file from the latest [release](https://github.com/vulnman/vulnman/releases).

To create the initial `local_settings.py` file, you have to start the `vulnman-web` container before the others.
This step is needed only once.

```bash
sudo docker-compose up vulnman-web
```

You may want to stop the container and [adjust the settings](/docs/getting-started/configuration).

To start all containers run the following command.

```bash
sudo docker-compose up
```


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
Otherwise, you may want to read how to [configure](/docs/getting-started/configuration/) your installation.


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



### Checklists and Vulnerability Templates
After you have installed vulnman you may want to import the default vulnerability templates and checklist.

#### Import Vulnerability Templates
```bash
python manage.py update_vulnerability_templates
```

*Note: If you want to get automatic updates for vulnerability templates. You may want to create a cronjob for the command above.*

#### Import Checklists
```bash
python manage.py update_checklists
```

*Note: If you want to get automatic updates for the checklists. You may want to create a cronjob for the command above.*
