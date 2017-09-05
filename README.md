# 接口约定测试系统
> api-mocker

## 第三方定制部署

### Config - Server

需要https支持的话，证书路径的配置在入口 `server/index.js` 中。其他服务端的配置都在 `server/config`目录下。其中：

`clientRoot`: 客户端地址，目前仅在发送提示邮件中有作用;

`transporter`: 邮件推送的相关配置，请设置自己推送邮箱。有些邮件服务商安全策略比价高，会发生推送错误，请自行充分测试。如果未配置，则系统不推送提示邮件;

`pushInterval`: 邮件推送的时间间隔配置。目前仅只针对api修改这一项配置；

`mongoose`: mongoDB的相关配置;

`bodyParser.jsonLimit`: 接口请求信息最大限制。因为接口更新时，数据量比较大，所以得设置一下。

其他相关配置，请看egg.js文档中[相关内容](https://eggjs.org/zh-cn/basics/config.html#container)。


### Config - Client

客户端配置在 `client/config/index.js` 中。其中：

`serverRoot`: 服务端接口根路径;

`assetsPublicPath`: 静态文件公共路径，所有的静态文件资源地址，以此路径开头。请根据自身发布需求配置。

其他相关配置，请参考vue-cli脚手架[webpack模板](https://github.com/vuejs-templates/webpack)


## Install

安装依赖外部命令(`mongod`)

* `make install`

同时该命令也会确保`mongod`的启动，如果未启动会在本地建立`db`目录，并启动`mongod`.
如果服务器新开机可重新执行`make install`确保数据库启动.

## 开发启动(dev)

### Client

* `make client` 或者  `cd client && npm install && npm run dev`

### Server

* `make server` 或者 `cd server && npm install && npm run dev`

## 发布启动(prods)

### Client

* `make prod_client` 或者 `cd client && npm install && npm run build`

*** 此处需要调整

若用make命令资源文件会放在`./dist/`下面(注: 不是 `./client/dist`)，直接进行nginx托管即可

***

### Server

* `make prod_server` 或者 `cd server && npm install && npm start`

默认端口号为7001
