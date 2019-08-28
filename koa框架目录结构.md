# 总结整理koa框架项目结构

```
.
├── apidoc.json
├── commitlint.config.js
├── config
│   ├── dev.json
│   └── production.json
├── ecosystem.json
├── modules   // 项目主要代码都在该目录下
│   ├── controllers // index.js中路由分发后，逻辑部分会引用该文件夹文件，用来处理操作数据库给客户端返回数据
│   │   └── test.js
│   ├── index.js   // 入口文件，引入中间件 监听端口 启动服务
│   ├── middleware  // 中间件 中间件的配置 设置
│   │   ├── cors.js
│   │   └── request_log.js
│   ├── models   // 数据库 可以理解为数据库的映射，逻辑中操作数据库主要是操作这里就ok了
│   │   ├── db.js
│   │   └── vip_black_shop
│   │       ├── index.js
│   │       ├── sms_activity.js
│   │       ├── sms_banner.js
│   │       ├── sms_hot_sale.js
│   │       └── sms_icon.js
│   ├── routers // 路由分发、逻辑部分会调用上面controllers里面的逻辑
│   │   └── test.js
│   ├── services // 操作数据库 封装一些对数据库的增删改查的方法 供需要操作数据库的逻辑使用 如上面的controllers 
│   │   └── test.js
│   └── web_router.js   // 路由入口，汇总router里面的文件
├── package.json
├── package-lock.json
└── README.md
```