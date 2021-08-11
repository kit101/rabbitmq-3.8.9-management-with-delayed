# rabbitmq-docker-image-ext-plugins-example

rabbitmq docker镜像构建示例，添加并启用自定义插件

### step1:
到官方网站下载插件[https://www.rabbitmq.com/community-plugins.html](https://www.rabbitmq.com/community-plugins.html)放到`build/plugins`目录

### step2:
修改Dockerfile
```Dockerfile
# 指定rabbitmq版本
FROM rabbitmq:3.8.9-management
# ...
# enable plugins begin =====
RUN rabbitmq-plugins enable rabbitmq_delayed_message_exchange
# 在这里启用需要的插件
# enable plugins end =====
# ...
```

### step3:
构建docker镜像
```bash
docker build -t rabbitmq:3.8.9-management-ext-plugins
```

### step4:
启动rabbitmq
```bash
docker run --name rabbitmq-test  -e RABBITMQ_DEFAULT_USER=guest -e RABBITMQ_DEFAULT_PASS=guest -p 15672:15672 -p 5672:5672 rabbitmq:3.8.9-management-ext-plugins
```