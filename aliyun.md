# 阿里云安装

## 安装docker

> apt-get install docker.io

## ssh 登陆

## 安装java8

> apt-get install python-software-properties
> apt install software-properties-common
> add-apt-repository ppa:webupd8team/java
> apt-get update
> apt-get install oracle-java8-installer

## 设置网络端口
 》 安全组设置
端口8580
端口3306

## 安装nginx

> apt-get install nginx
> cp nginx /etc/nginx/nginx.conf
>/etc/init.d/nginx restart

## 安装docker-mysql
> mkdir -p /db/data
> docker run  --privileged  -d -e TIMEZONE=Asis/Shanghai -v /db/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=docker -p 3306:3306  mariadb --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
