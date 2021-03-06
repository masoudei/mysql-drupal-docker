# mysql-drupal-docker
MySQL &amp; Drupal Docker Stack


# How To Install Drupal with Docker & Docker Compose

You can run this stack with seperated docker commands like this :

1 - Create MySQL data volume :

`$ docker volume create mysql_data`

2 - Create a bridge network :

`$ docker network create drupal_mysql_net --driver=bridge`

3 - Run MySQL container :

`$ docker run -d --name=mysql-drupal --restart=always -v mysql_data:/var/lib/mysql --net=drupal_mysql_net -e MYSQL_ROOT_PASSWORD="mypassword" -e MYSQL_DATABASE="drupal" mysql`

4 - Run Drupal container :

`$ docker run -d --name=drupal -p 8080:80 --restart=always -v /var/www/html/modules -v /var/www/html/profiles -v /var/www/html/themes -v /var/www/html/sites --link mysql:mysql --net=drupal_mysql_net drupal`

