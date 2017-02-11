#YOLO: Docker

**This is simple, easy to extend and reconfigure,docker-compose stack to develop php-powered websites.**
Project strongly inspired by https://github.com/maxpou/docker-symfony

### Use composer:
Composer is already installed in php container

### Get access to app_dev.php:
1. Check host ip addres from php container: `docker-compose exec php /sbin/ip route|awk '/default/ { print $3  }'`
2. Edit web/app_dev.php, go to line 15 and replace 127.0.0.1 with host address from cmmand above

Repeat this when you want to get access to _web/config.php_ script.
