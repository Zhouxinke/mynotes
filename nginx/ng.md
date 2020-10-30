初识Nginx

Nginx基础架构

HTTP模块

反向代理与负载均衡

Nginx系统层性能优化

源码



Nginx三个主要的应用场景

- 静态资源服务

  通过本地文件系统提供服务

- 反向代理服务

  Nginx的强大性能

  缓存（加速访问）

  负载均衡

- API服务

  OpenResty

  

  

  contribution文件夹下的vim 复制到自己的vim中  可以不同色彩显示ng语法

  ```shell
  cp -r contrib/vim/* ~/.vim/
  ```

  

Nginx配置语法

配置文件由指令和指令块（如http{}）构成

每条指令以；结尾，指令与参数之间以空格符号分隔

指令块以{}大括号将多条指令组织在一起

include语句允许组合多个配置文件以提升可维护性

使用#号添加注释

使用$符号使用变量

部分指令支持正则表达式



配置参数时间单位

ms、s、m、h、d、w（weeks）、M（months  30 days）y（years 365days）

配置大小

b、k、m、g



Nginx命令行

![image-20201021150745181](C:\Users\Zhouxinke\Desktop\myNotes\nginx\image-20201021150745181.png)



重载

nginx -s reload

热部署

```
ps -ef | grep nginx 查看正在运行的nginx
cp nginx nginx.old  备份原来的文件
cp -r nginx nginx/sbin/ -f

```



日志切割

```
mv access.log bak.log 备份日志文件
../sbin/nginx -s reopen 
```



静态资源使用gzip进行压缩

autoindex on 使网页打开成类似ftp下载的样子



上游服务器：对公网不提供访问



master-work进程



nginx多进程结构（多进程不会相互影响）

分为worker进程和cache（Cache manager和Cacheloader）相关进程

work进程处理，master管理worker进程，worker进程之间使用共享内存通信

一般worker进程数量=cpu核数



reload流程



优雅关闭nginx(work进程)

```

```



事件模型性能（epoll、poll、select）



4大模块http、event、upstream、mail