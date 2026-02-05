---
layout:     post
title:      "如何使用非root用户执行docker命令"
subtitle:   ""
description: "如何使用非root用户执行docker命令"
excerpt: "如何使用非root用户执行docker命令"
date:       2025-02-09 10:00:00
image:     "/img/tag-bg.jpg"
showtoc: false 
tags:
    - Tips
    - Docker
URL: "/2018/02/09/docker-without-sudo/"
categories: [ Tips ]
---

Add the docker group if it doesn't already exist:

```shell
sudo groupadd docker
```

Add the connected user "$USER" to the docker group. Change the user name to match your preferred user if you do not want to use your current user:

```shell
sudo gpasswd -a $USER docker
```

Either do a newgrp docker or log out/in to activate the changes to groups.
