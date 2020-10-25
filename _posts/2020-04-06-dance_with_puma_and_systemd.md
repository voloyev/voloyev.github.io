---
layout: post
title: Dance with puma and systemd
date: 2020-04-06 22:58
category: rails
author: Volodymyr Yevtushenko
tags: ["devops", "Linux", "Systemd"]
summary: Tried to configure puma server with systemd
---

So I've tried to start my puma instance with systemd in user space.

My puma.service in jinja2 template. I use ansible to provision my server.

```systemd
[Unit]
Description=Puma HTTP Server
After=network.target

[Service]
Type=simple
RemainAfterExit=true
WorkingDirectory={{ path_to_prod }}current
Environment=RAILS_ENV=production
ExecStart=/usr/local/bin/chruby-exec ruby-2.6.5 -- bundle exec puma -C {{ path_to_prod }}current/config/puma.rb -b unix://{{ path_to_prod }}shared/tmp/sockets/puma.sock
ExecReload=/bin/kill -TSTP $MAINPID
SyslogIdentifier=api-puma
Restart=always

StandardOutput={{ path_to_prod }}current/log/puma-prod.log
StandardError={{ path_to_prod }}current/log/puma-prod_err.log

[Install]
WantedBy=multi-user.target
```

It works, but when I logout from server it stops.

And finally I found this article: https://vic.demuzere.be/articles/using-systemd-user-units/

Just a memo.
