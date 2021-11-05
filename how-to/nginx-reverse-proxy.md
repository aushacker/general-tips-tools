# NGINX Reverse Proxy Example

Stephen Davies

Red Hat

5 Nov 2021

## Introduction

How to configure a basic Nginx reverse proxy.

## Nginx Customisation

[Nginx Docker Page](https://hub.docker.com/_/nginx/)

[Nginx beginners guide](https://nginx.org/en/docs/beginners_guide.html)

## Ubuntu Nginx Container Test

```
podman run -d --name nginx -p 8080:80 docker.io/nginx
curl http://localhost:8080/
podman rm --force nginx
```

## Ubuntu Nginx Proxy Config Sample

1. `mkdir -p /home/<user>/etc/nginx`
1. Create file `/home/<user>/etc/nginx/nginx.conf`

```
user  nginx;
worker_processes  auto;

error_log  /var/log/nginx/error.log notice;
pid        /var/run/nginx.pid;

events {
    worker_connections  1024;
}

http {
    include       /etc/nginx/mime.types;
    default_type  application/octet-stream;

    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for"';

    access_log  /var/log/nginx/access.log  main;

    sendfile        on;
    #tcp_nopush     on;

    keepalive_timeout  65;

    #gzip  on;

    #include /etc/nginx/conf.d/*.conf;

    server {
        listen 80;
        listen [::]:80;
        server_name localhost;

        # Local, static content from within the image (default)
        location / {
            root /usr/share/nginx/html;
        }

        # URI path to a local server e.g. RH Web Server
        location /abc {
            proxy_pass http://localhost:7080;
        }

        # URI path mapping to OCP hosted service (Code Ready Container)
        location /abc/def {
            proxy_set_header Host "myroute-myproject.apps-crc.testing";
            proxy_pass http://ocp.external.ip;
        }

    }
}
```

## Run Nginx Container

```
podman run -d --name nginx -p 8080:80 -v ./etc/nginx/nginx.conf:/etc/nginx/nginx.conf docker.io/nginx
```

## Windows Subsystem for Linux 2

This next bit applies if you're running your nginx container inside WSL2.

### Expose the WSL2 port

1. On Linux - `ip a`
1. Use previous command output to determine virtual ip address e.g. 172.22.88.x
1. On Windows - `netsh interface portproxy add v4tov4 listenport=8080 listenaddress=127.0.0.1 connectport=8080 connectaddress=172.22.88.x`
1. `curl http://localhost:8080/`
