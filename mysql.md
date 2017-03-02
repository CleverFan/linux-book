1  `rpm -Uvh http://dev.mysql.com/get/mysql-community-release-el7-5.noarch.rpm` 

> 
![](http://upload-images.jianshu.io/upload_images/4047674-e81f41314ce653ac.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


2  `yum repolist enabled | grep "mysql.*-community.*"`

> ![](http://upload-images.jianshu.io/upload_images/4047674-9c40d122f26f9d09.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240) 

3 `yum install mysql-community-server`

> 
![](http://upload-images.jianshu.io/upload_images/4047674-5192861d772d62f9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  


> ![](http://upload-images.jianshu.io/upload_images/4047674-9338d267d64d0bbb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


4 `   `

> 
![](http://upload-images.jianshu.io/upload_images/4047674-4e8aa4c4d4e03b42.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


5 systemctl enable mysqld
systemctl daemon-reload

设置开机启动  两条语句 分开执行

> 
![](http://upload-images.jianshu.io/upload_images/4047674-9394816b30f40504.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


6 mysql -u root

> 
![](http://upload-images.jianshu.io/upload_images/4047674-fe5cddb5c4c01b38.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


7 `set password for 'root'@'localhost'=password('这里是密码'); `

> 
![](http://upload-images.jianshu.io/upload_images/4047674-fd50c2d5209384fb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


8 ` GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY '123456' WITH GRANT OPTION;` 

> 
![](http://upload-images.jianshu.io/upload_images/4047674-cf0b83e8815e8da9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 
![](http://upload-images.jianshu.io/upload_images/4047674-7882e76e8b17c009.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


9 `vi /etc/my.cnf`

```
[mysqld]
character_set_server=utf8
init_connect='SET NAMES utf8'
```

> 
![](http://upload-images.jianshu.io/upload_images/4047674-c8a91ebd01dccab7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240) 

10 `systemctl restart mysqld`