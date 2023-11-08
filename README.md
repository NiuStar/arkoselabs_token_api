# arkoselabs_token_api

# 升级
## 2023-11-08更新： 
新增自动生成接口文档接postman文档 公共接口文档地址为：https://showdoc.ai00.xyz/web/#/676794187/170896388

## 2023-10-08 升级
1）增加http://localhost:8080/api/login登录接口

参数为json格式的：

{ "email":"XXX", "password":"XXX" }

2）去除了内置har，内置har使用太多，易失效，建议使用自己的


## 使用Chrome获取HAR文件

使用Chrome浏览器获取HAR (HTTP Archive) 文件是一个相对简单的过程。HAR文件记录了一个网页加载过程中的所有网络请求和响应，它在网络性能分析和调试中是一个非常有用的工具。

### 步骤

1. **打开Chrome浏览器**。

2. **开启Chrome开发者工具**：
    - 按下 `F12` 
    - 或者在页面上右键点击选择“检查”（Inspect）。

3. **选择“网络”（Network）选项卡**。

4. **（可选）清空现有的记录**：
    - 在Network选项卡中，你可能会看到一些已经加载的资源的记录。
    - 为了开始一个全新的记录，你可以点击左上角的红色圆圈（录制按钮）确保它是红色的。
    - 然后点击左边的“清除”按钮（一个像垃圾桶的图标）。

5. **加载或重新加载网页**：
    - 使用chatgpt，并完成一次会话
    - 开发者工具会记录所有的网络请求。

6. **保存HAR文件**：
    - 确保需要的(https://tcr9i.chat.openai.com/fc/gt2/public_key/35536E1E-65B4-4D96-9D97-6ADB7EFF8147) 网络请求已经完成。
    - 在Network选项卡中的任何地方右键点击，选择“Save as HAR with content”。
    - 选择保存位置，并为文件命名（默认是 `www.example.com.har`）。
    - 点击“保存”。

现在，你已经成功地保存了一个HAR文件。



## 2023-09-28 升级
已测试支持platform的登录，使用login_token接口

支持new api ke的token生成

http://localhost:8080/newapikey_token

支持更多其他token的生成，需上传对应的har

http://localhost:8080/other_token?pk=23AAD243-4799-4A9E-B01D-1166C5DE02DF

## 2023-09-27 升级
支持login处的arkoselabs_token生成，修改放置多个har至har目录中

</br>目前有两个接口，分别为：

</br>http://localhost:8080/token

</br>http://localhost:8080/login_token

## 2023-09-20 升级支持官网最新1.5.5版本

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
      showdoc_uri = https://showdoc.ai00.xyz
      showdoc_username = "test"
      showdoc_password = "123456"
    volumes:
      - ./har目录:/home/app/har
    ports:
      - 8080:8081
    restart: unless-stopped
```

## arkoselabs token api共享
提供一个在线服务，可以获取到chatgpt的arkoselabsToken

2023年10月27日：最新接口地址为：https://arktoken.mukj.cn/token?key=XXXXX


接口地址为：http://1.tcp.vip.cpolar.top:10102/token（已取消）<br/>
请求方式为get<br/>

新增两个服务器：<br/>
https://gpttoken2.mukj.cn/token （已取消）<br/>
http://gpttoken.mukj.cn/token （已取消）<br/>

2023-7-17 新增服务器
http://gpttoken3.mukj.cn/token（已取消）

开放镜像以便私有化部署
 2023-08-02
目前只有
https://gpttoken2.mukj.cn/token?key=xxx<br/>
http://gpttoken.mukj.cn/token?key=xxx<br/>
这两台服务器可用
如果需要key请联系yjkj02@gmail.com
大户请根据docker-compose自建服务器，如需使用公共服务器，请联系yjkj02@gmail.com，不联系的大户会被限流
