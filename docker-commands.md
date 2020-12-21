docker run -dit -p 80:80 centos:8 /bin/bash

docker exec -it <container id> bash

yum -y install epel-release

yum -y install nginx

yum -y install httpd; yum clean all; systemctl enable httpd.service

### NOOO
systemctl status nginx
service nginx status
## this is not necessary. Docker does not use systemctl, as its permissions mangament would be contradictory to the microservices approach.
## nginx is already started.


vi /etc/nginx/nginx.conf

nginx -t 
# will check the syntax of the conf file and output errors

## WEB PAGE CONTENT
cd /usr/share/nginx/html

docker exec <nginx-container-name-or-id> nginx -s reload

# create a new file in /etc/nginx
kplabs.conf

# backup the default conf files
mv nginx.conf.default nginx.conf.default.bak
ssl.conf # not found
virtual.conf # not found

# create the websites directory
mkdir -p /var/www/websites
cd /var/www/websites
touch index.html