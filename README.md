You Only Learn Once: Docker... wtf?
-----------------------------------
TL;DR: Result of learning by making tool I need.
_Project strongly inspired by https://github.com/maxpou/docker-symfony_

List of available services (each has its own container):

|     Service   | Version |  Additions   |
|---------------|---------|------------- |
|     Apache    |   2.4   |              |
|      PHP      |   7.0   |              |
|      MySQL    |   5.7   |              |
|      Node     |   7.5   |  Gulp 3.9    |

I want to keep this as simple and framework-independent as possible.

How to...
============
...use yolo-docker
------------------
Just clone the repository and run docker-compose build.
You can use only particular services by remove these not whih you don't need from docker-compose.yml

...use composer:
-----------------
Composer is already installed in php container, so run `docker-compose exec php bash` and then use composer as normal.

...use gulp with sass
-----------------------
Before 'docker-compose build':
1. Edit both _./docker/gulp/package.json_ and _./docker/gulp/gulpfile.js_ in order to fit them to your requirements
2. In both _./docker-compose.yml_ and _./docker/gulp/Dockerfile_ replace 'theme' folder name with path to your theme.

Default Gulp plugins (you can change it by editing _docker/gulp/gulpfile.js_)

|        Plugin     |                      What it does                    |                                                                                                                                  
| ----------------- | --------------------------------------------------   |                                                                                                                                  
| gulp-sass         | compile scss files into css ones,                    |                                                                                                                                 
| gulp-autoprefixer | forget about browser-related prefixes e.g in flexb   |                                                                                                                               
| gulp-postcss      | some usefeull actions gulp can do on compiled css,   |                                                                                                                                  
| gulp-sourcemaps   | allow you to inspect scss files in browser inspector |   


FAQ
============
#### Symfony: get access to app_dev.php:
1. Check host ip addres from php container: `docker-compose exec php /sbin/ip route|awk '/default/ { print $3  }'`
2. Edit web/app_dev.php, go to line 15 and replace 127.0.0.1 with host address from cmmand above

Repeat this when you want to get access to _web/config.php_ script.

#### I want to install php extension without rebuild php container
Let's install mysqli extension from inside the container:
```
docker-compose exec php bash
docker-php-ext-install mysqli
```
#### Dump sql database
``` $ docker-compose exec db mysqldump -uusername -puserpassword dbname > backup.sql```

___

Don't hesistate to create issue/feature request.
