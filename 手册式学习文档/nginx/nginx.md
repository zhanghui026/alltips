# Nginx 笔记	

## 基本知识

1.   重载nginx配置文件

   ```bash
   $ nginx -s <SIGNAL>
   ```

   * `quit`  -  shut down graceful
   * `reload` - Reload the configuration file
   * `reopen` - reopen log files
   * `stop` - shut down imemediately

2. nginx config file 

   1. **/usr/local/nginx/conf**, **/etc/nginx**, or **/usr/local/etc/nginx**

3. 基本语法

   Directives: 简单单行使用 `;`,多行块的用`{}`

   ```
   user             nobody;
   error_log        logs/error.log notice;
   worker_processes 1;
   ```

4.  配置文件include方式

   可将配置文件放在目录： **/etc/nginx/conf.d** 目录，使用`include` 命令

   ```bash
   include conf.d/http;
   include conf.d/stream;
   include conf.d/exchange-enhanced;
   ```

5. Contexts 上下文

   * `events` - general

   * `http`

   * `mail`

   * `stream`
   
6. Virtual Servers 虚拟servers

  使用`server`命令。One or more `location` contexts in a `server` context.

使用例子
```script
user nobody; # a directive in the 'main' context

events {
    # configuration of connection processing
}

http {
    # Configuration specific to HTTP and affecting all virtual servers  

    server {
        # configuration of HTTP virtual server 1       
        location /one {
            # configuration for processing URIs starting with '/one'
        }
        location /two {
            # configuration for processing URIs starting with '/two'
        }
    } 
    
    server {
        # configuration of HTTP virtual server 2
    }
}

stream {
    # Configuration specific to TCP/UDP and affecting all virtual servers
    server {
        # configuration of TCP virtual server 1 
    }
}

```



