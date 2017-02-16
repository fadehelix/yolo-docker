You Only Learn Once: Docker... wtf?
-----------------------------------
TL;DR: Result of learning by making tool I need.
_Project strongly inspired by https://github.com/maxpou/docker-symfony_

Stack:
- Apache 2.4
- PHP 7.0 FPM
- MySQL
- Nodejs (with Gulp and SASS preprocessor)

I want to keep this as simple and framework-independent as possible.

FAQ
---
### Use composer:
Composer is already installed in php container, so run `docker-compose exec php bash` and then use composer as normal.

### Get access to app_dev.php:
1. Check host ip addres from php container: `docker-compose exec php /sbin/ip route|awk '/default/ { print $3  }'`
2. Edit web/app_dev.php, go to line 15 and replace 127.0.0.1 with host address from cmmand above

Repeat this when you want to get access to _web/config.php_ script.

### Use gulp with sass
=======
Before 'docker-compose build':
1. Edit both _./docker/gulp/package.json_ and _./docker/gulp/gulpfile.js_ in order to fit them to your requirements
2. In both _./docker-compose.yml_ and _./docker/gulp/Dockerfile_ replace 'theme' folder name with path to your theme.
___
Don't hesistate to create issue/feature request.
