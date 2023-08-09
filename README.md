# arkoselabs_token_api

## 自建token池

使用方法，在支持访问到https://tcr9i.chat.openai.com的电脑上执行dokcer-compose up -d
如何判断能否访问到https://tcr9i.chat.openai.com

```curl -v https://tcr9i.chat.openai.com/v2/35536E1E-65B4-4D96-9D97-6ADB7EFF8147/api.js```

然后可以使用http://localhost:8080/token获取到token

## docker-compose.yaml

```
version: '3'
services:
  arkoselabs_token_api.get:
    container_name: arkoselabs_token_api.get
    image: 24802117/arkoselabs_token_api.get:latest
    environment:
      sql_host: mysqlIP
      sql_userName: root
      sql_port: 3306
      sql_password: mysql密码
      db: false
      http_proxy: http://localhost:40000
    volumes:
      - ./chat.openai.com.har:/home/app/chat.openai.com.har
    ports:
      - 8080:8081
    restart: unless-stopped
```

## arkoselabs token api共享
提供一个在线服务，可以获取到chatgpt的arkoselabsToken

接口地址为：http://1.tcp.vip.cpolar.top:10102/token（已取消）<br/>
请求方式为get<br/>

新增两个服务器：<br/>
https://gpttoken2.mukj.cn/token<br/>
http://gpttoken.mukj.cn/token<br/>

2023-7-17 新增服务器
http://gpttoken3.mukj.cn/token（已取消）

开放镜像以便私有化部署
 2023-08-02
目前只有
https://gpttoken2.mukj.cn/token<br/>
http://gpttoken.mukj.cn/token<br/>
这两台服务器可用

大户请根据docker-compose自建服务器，如需使用公共服务器，请联系yjkj02@gmail.com，不联系的大户会被限流
