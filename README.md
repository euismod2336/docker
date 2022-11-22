# New Project
Follow these steps to use this docker setup for any new project

## Copy files
First copy the files into the root of the project.
Files to copy:
 - docker/composer.phar
 - docker/httpd.conf
 - docker/php
 - docker/php.ini
 - ./.dockerignore
 - ./docker-compose.yml

If there is no public_html folder you can copy the index.php along with it, but it's mainly there to be non-empty.

### docker/composer.phar
Composer in a self-containing phar file. This is so we don't have to install composer in our image but still have access to it. Keep in mind that if you run composer in your container you'll have to prefix it e.g. `php composer install`. This file is only required when the project uses composer in some capacity.

### docker/httpd.conf
The config file for the Apache container. This assumes that the site will be the only thing running on it, and that it will run with SSL.

### docker/php
The dockerfile for the PHP container. It uses PHP 8.x and installs the most common extensions. It also comes with xDebug installed. You can further modify this to suit the needs of your specific project.

### docker/php.ini
The configuration file for PHP. These are development settings, DO NOT use these on a production environment. xDebug will always run and auto-connect to any client.

### ./.dockerignore
Similar to gitignore but specifically for docker. This avoids an issue where docker would try to rebuild an image with files/config from the db images

### ./docker-compose.yml
The configuration file for `docker-compose`. This should also work with `docker compose`.

## Modify docker-compose.yml

### IP's
Make sure all the ip-adresses are changed according to what you are running locally.

### Image variations
The configuration file has some baseline images you might want or not, remove the ones you do not require. This would also be the time to uncomment some lines if you are using Craft CMS.

### MKCert
Run mkcert for your domain and add the keys to the place as given in the docker-compose.yml

## Run
run `docker-compose up`. Happy coding.
