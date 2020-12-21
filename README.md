## some docker commands
The first instructions are to run a centos container, and inside install nginx.

But later I decided to rather run a VM with centos.

    docker run -dit -p 80:80 centos:8 /bin/bash

    docker exec -it <container id> bash

    yum -y install epel-release

    yum -y install nginx

This wouldn't be necessary in docker

Docker does not use systemctl, as its permissions mangament would be contradictory to the microservices approach. And, nginx is already started.

> systemctl status nginx

> service nginx status

## Some nginx stuff 
Main conf file
> vi /etc/nginx/nginx.conf

This will check the syntax of the conf file and output errors
> nginx -t 

WEB PAGE CONTENT
> cd /usr/share/nginx/html

If using the nginx container, this is how you reload it, instead of systemd
> docker exec <nginx-container-name-or-id> nginx -s reload

## Create our own website
create a new file in /etc/nginx
> kplabs.conf

backup the default conf files
    mv nginx.conf.default nginx.conf.default.bak
    ssl.conf # not found
    virtual.conf # not found

create the websites directory
    mkdir -p /var/www/websites
    cd /var/www/websites
    touch index.html