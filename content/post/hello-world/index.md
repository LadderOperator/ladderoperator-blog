---
title: Hello world！第一个帖子！
date: 2020-04-02
image: images/hello-world.jpg
author: LadderOperator
tags:
  - 记录
---
这坑爹玩意儿搭了我半天......



简单来说，利用Docker+Wordpress搭建网站的坑主要在于mysql的问题。



在网上随手找到的教程都大同小异，关键在于下面的几个问题。



首先Wordpress直接用



``` bash

docker pull wordpress

```



默认拉取`wordpress:latest`问题不大，但是mysql不能`mysql:latest`，因为`mysql:8.0`跟`mysql:5.7`变化较大（主要在密码认证机制上）。



除此之外，mysql自己的权限问题也是个坑，需要用



``` bash

docker exec -it [your-mysql-name] bash

```



然后在容器内`mysql -uroot -p`，输入密码后使用：



``` mysql

GRANT ALL ON *.* TO root@'%' IDENTIFIED BY '[your password]';

```



不过话说回来这样确实比较麻烦。下次这么部署东西，果然还是该好好看看docker-compose



> 参考：<https://stackoverflow.com/questions/37080300/cant-connect-docker-wordpress-container-to-mysql-on-host?answertab=oldest#tab-top>

