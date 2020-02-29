# Docker: Nginx with PHP support
Dockerfile for PHP with mSMTP client.

docker-compose file includes:
 - Nginx
 - Traefik support
 - MariaDB
 - Adminer
 - Backup

## Setup
1. clone the repo
2. edit .env file
3. create msmtp/msmtprc from provided msmtprc.example

## Network settings:
The stack is divided into two networks, backend and frontend.

the idea behind splitting the stack into two networks
is to block the access of the reverse proxy to the backend containers.

both networks are unique and will be named with stack-name_network-name such as:

- docker-nginx-php-fpm_backend
- docker-nginx-php-fpm_frontend

after running docker-compose up you need to connect your reverse proxy to your new frontend network:
 you can do that manually using:
 - docker network connect docker-nginx-php-fpm_frontend PROXY_CONTAINER_NAME

if you are using my Traefik setup there is a 'connect.sh' script included
that will connect all your frontend networks to your Traefik container.

Author: [RaveMaker][RaveMaker].

[RaveMaker]: http://ravemaker.net
 