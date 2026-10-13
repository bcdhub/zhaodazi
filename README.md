# 找搭子系统 | CityGather

## 项目简介

本项目基于前后端分离架构开发，后端采用模块化设计，涵盖用户服务、活动服务、报名服务、支付结算服务、消息通知服务、社交互动服务、安全风控服务等核心模块，支持高并发活动发布与报名处理。
前端适配用户端（H5/小程序/APP）、运营管理端多端展示，核心实现 LBS 附近活动推荐、活动状态机、报名名额校验、AA 分账引擎、活动群聊（WebSocket）、活动签到与核销、用户信用体系、
权限与数据隔离等能力。系统代码结构清晰、接口规范，支持 JAR 私有库依赖管理，可配合 NDA 协议进行源码交付，便于客户团队后续维护、扩展与自主上线部署。

- **用户端**：活动浏览、报名参与、群聊互动
- **运营管理端**：活动审核、用户管理、数据统计
- ️ **后端服务**：RESTful API、WebSocket 实时通知

### 活动功能

- 附近活动推荐
- 活动分类浏览与搜索（聚餐/桌游/剧本杀/徒步/露营/球局等）
- 活动详情查看（时间、地点、人数、费用）
- 一键报名/取消报名
- 活动发起人审核报名
- 活动签到与核销

### 支付功能

- 微信支付（H5/Native）
- 支付宝支付
- 聚合支付（嘉联）
- 支付方式后台可控
- AA 分账自动结算
- 活动保证金机制

### 会员系统

- 手机号登录（短信验证码）
- 个人资料与兴趣标签
- 用户信用体系
- 积分体系

### 运营管理

- 实时活动通知（WebSocket）
- 活动审核管理（待审核/已发布/已结束）
- 用户资质审核与黑名单
- 活动分类管理
- 平台数据统计
- 系统信息配置

## ️ 技术栈

| 层级 | 技术 |
| ------ |------ |
| **后端框架** | Spring Boot + MyBatis Plus |
| **JDK** | Java 8+ |
| **数据库** | MySQL 5.7+ |
| **缓存** | Redis |
| **消息队列** | RabbitMQ |
| **实时通信** | Netty WebSocket |
| **地图服务** | 高德地图 |
| **支付** | 微信支付 + 支付宝支付 |
| **管理后台** | Vue 2.x + Element UI + ECharts |
| **构建工具** | Maven 3.8+ / Vue CLI 5（webpack 5） |

#### 4️⃣ 启动系统

- 通过git下载源码
- idea、eclipse需安装lombok插件，不然会提示找不到entity的get set方法
- 创建数据库fast_build，数据库编码为UTF-8
- 执行db/mysql.sql文件，初始化数据
- 修改application-dev.yml，更新MySQL账号和密码
- Eclipse、IDEA运行fastApplication.java，则可启动项目
- Swagger文档路径：http://localhost:8005/fast_build/swagger/index.html
- Swagger注解路径：http://localhost:8005/fast_build/swagger-ui.html

## 部署包结构

```
fb-gather-server
├── src/main/java/com/fast
│ ├── common # 公共模块（注解、切面、异常、工具类、XSS过滤）
│ ├── config # 全局配置（Shiro、Redis、MyBatis、Swagger、CORS等）
│ ├── datasource # 多数据源支持（动态数据源切换）
│ ├── modules # 业务模块
│ │ ├── app # APP端用户接口（登录、注册、Token认证）
│ │ ├── sys # 系统管理（用户、角色、菜单、字典、日志）
│ │ ├── activity # 活动核心业务（发布、编辑、下架）
│ │ ├── enrollment # 报名管理（报名、审核、取消）
│ │ ├── pay # 支付模块（微信支付、支付宝、AA分账、回调处理）
│ │ ├── member # 会员管理
│ │ ├── address # 活动地点管理
│ │ ├── category # 活动分类管理
│ │ ├── coupon # 优惠券管理
│ │ ├── integral # 积分管理
│ │ ├── invite # 邀请奖励
│ │ ├── message # 消息推送
│ │ ├── chat # 活动群聊（WebSocket）
│ │ ├── checkin # 活动签到核销
│ │ ├── credit # 用户信用体系
│ │ ├── datacentre # 数据统计中心
│ │ ├── oss # 文件存储（阿里云OSS）
│ │ ├── file # 文件上传
│ │ ├── common # 业务公共模块
│ │ └── utils # 业务工具类
│ └── FastApplication.java # 启动类
├── src/main/resources
│ ├── mapper # MyBatis XML映射文件
│ ├── static/swagger # Swagger静态资源
│ ├── weixin # 微信支付证书
│ ├── application.yml # 主配置文件
│ └── application-prod.yml # 生产环境配置
├── db # 数据库脚本
│ └── gather.sql # 数据库初始化SQL
```

## 联系我们

- 电话：15596655525
- 微信：15596655525（同号）

️ 开源版仅用于学习交流，商用请购买商业版授权。

## 支持项目

如果这个项目对你有帮助，请给一个 **Star**  支持一下！

---

**找搭子系统**  2024-2025

让同城社交更有趣

