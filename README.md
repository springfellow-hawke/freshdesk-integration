# freshdesk-integration

Creating the DB users:
Startup a Docker isntance for MariaDB locally. The following command will startup with shared folders
so that we have persistent storage for restart.

$ docker run -e TZ=Africa/Johannesburg --restart unless-stopped \
    --name mariadb-andre -p 3306:3306 \
    -v /opt/docker-folders/mariadb:/var/lib/mysql \
    -e MYSQL_ROOT_PASSWORD=admin -d mariadb:latest
    
Create the two db users and databases that we are going to use:

CREATE DATABASE crm;
CREATE USER 'crm'@'%' IDENTIFIED BY 'helpmyasb';
GRANT ALL PRIVILEGES ON crm . * TO 'crm'@'%';


CREATE DATABASE fresh;
CREATE USER 'fresh'@'%' IDENTIFIED BY 'helpmyasb';
GRANT ALL PRIVILEGES ON fresh . * TO 'fresh'@'%';