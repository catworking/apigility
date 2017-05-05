# Apigility Logic
## 概述
Apigility Logic 是一个可复用的业务逻辑库。它建立在[Apigility](https://apigility.org/)框架之上，Apigility是一个基于[Zend Framework](http://framework.zend.com/)框架的API开发框架。

Apigility Logic 的组件是没有用户界面的，本质上只是数据、业务逻辑、接口的集合。
这些组件主要用于手机APP开发，为手机APP和管理后台提供数据接口。
管理后台一般是使用React.js/Angular.js/Vue.js开发的单页Web应用。

## 组件清单
- [Apigility User](https://github.com/catworking/apigility-user) 用户组件
  
  用户注册，用户资料管理等功能。
  
- [Apigility Oauth2 Adapter](https://github.com/catworking/apigility-oauth2-adapter) Oauth2认证组件
  
  用户登录，退出登录，刷新Token等功能。
  
- [Apigility Object Storage](https://github.com/catworking/apigility-object-storage) 对象存储组件
  
  文件存储功能，集成了阿里云OSS服务。
  
- [Apigility Vendor Integrate](https://github.com/catworking/apigility-vendor-integrate) 第三方服务整合组件
  
  提供了一个机制去集成一些零散的第三方服务，这些服务是可配置的。
  
- [Apigility Catwork Foundation](https://github.com/catworking/apigility-catwork-foundation) 基础组件
  
  其它组件共用的公共库，主要是一些基类，所有的组件都依赖此组件。
  
- [Apigility App Info](https://github.com/catworking/apigility-app-info) 应用信息组件
  
  提供应用信息的管理功能，主要是管理应用的名称、应用简介、公司名称，企业地址，客服电话、使用协议等内容。
  
- [Apigility Photo Album](https://github.com/catworking/apigility-photo-album) 相册组件
  
  提供相册和照片管理的功能。
  
- [Apigility Order](https://github.com/catworking/apigility-order) 订单组件
  
  提供通用的订单管理功能，包括订单支付功能。
  
- [Apigility Address](https://github.com/catworking/apigility-address) 地址组件
  
  提供地址管理功能，此组件包含一个来自国家统计局的全国省市区数据库。
  
- [Apigility Ad](https://github.com/catworking/apigility-ad) 广告组件
  
  提供地广告管理功能，包括广告位置、广告图及其链接的管理。
  
- [Apigility Admin](https://github.com/catworking/apigility-admin) 管理员组件
  
  提供管理员帐号的管理功能，包括角色的管理、权限的管理。
  
- [Apigility Vip](https://github.com/catworking/apigility-vip) 会员组件
  
  提供付费会员功能，包括会员合约管理、会员购买管理。

- [Apigility Blog](https://github.com/catworking/apigility-blog) 日志博文组件
  
  提供基本的博客功能，管理文章分类、文章、文章附加的媒体等。
  
- [Apigility Message](https://github.com/catworking/apigility-message) 消息组件
  
  提供用户对用户的站内消息发送功能。
  
- [Apigility Social](https://github.com/catworking/apigility-social) 社交组件
  
  提供用户与用户之音的好友关系管理功能。
  
- [Apigility Feedback](https://github.com/catworking/apigility-feedback) 反馈组件
  
  提供用户反馈功能，包括反馈问题、举报用户的功能。
  
- [Apigility Finance](https://github.com/catworking/apigility-finance) 财务记账组件
  
  提供财务记账功能。以会计原理为概念的记账功能。
  
- [Apigility Communicate](https://github.com/catworking/apigility-communicate) 通讯组件
  
  提供发送手机验证码，发送电子邮件，发送手机系统通知的功能。
  
- [Apigility O2o Service Trade](https://github.com/catworking/apigility-o2o-service-trade) O2O服务交易组件
  
  提供O2O服务交易功能，个体或组织发布服务，消息者用户线上购买服务，并线下消费服务。

## 组件的基本结构
一个组件，实际上是一个[Zend Framework模块](https://docs.zendframework.com/zend-modulemanager/intro/)。

组件定义了一系列数据库结构（通过[Doctrine ORM](http://doctrine-project.org/projects/orm.html)处理），
实现了一些业务逻辑（通过[Zend Framework ServiceManager](https://docs.zendframework.com/zend-servicemanager/quick-start/)管理），
并提供RESTFul接口（通过[Apigility RESTFul](https://apigility.org/documentation/intro/first-rest-service)实现）。

接口调用服务，服务管理数据。下面是广告组件的目录结构：
```bash
ApigilityAd
├── config
│   ├── doctrine.config.php          // Doctrine实体类扫描配置
│   ├── module.config.php            // 由Apigility Web界面工具管理的Apigility配置
│   └── service.config.php           // ServiceManager管理的服务类配置
├── Module.php
├── README.md
└── src
    ├── DoctrineEntity               // Doctrine实体类目录
    │   ├── Banner.php
    │   └── Position.php
    ├── Service                      // ServiceManager管理的服务类目录
    │   ├── BannerServiceFactory.php
    │   ├── BannerService.php
    │   ├── PositionServiceFactory.php
    │   └── PositionService.php
    └── V1
        └── Rest                    // Apigility RESTFul接口类目录，每个子目录对应一个资源
            ├── Banner
            │   ├── BannerCollection.php
            │   ├── BannerEntity.php
            │   ├── BannerResourceFactory.php
            │   └── BannerResource.php
            └── Position
                ├── PositionCollection.php
                ├── PositionEntity.php
                ├── PositionResourceFactory.php
                └── PositionResource.php
```

## 如何了解一个组件的具体功能
现有的组件是暂时是没有文档的，每个组件的文档编写已经纳入工作计划。

在文档完善之前，开发者需要通过阅读代码来了解一个组件的具体功能。参考上一节中的内容，
可以知道这其实并不算是一件困难的事。
每个组件都只有3种主要代码：
- Doctrine 实体，用来生成数据库表的
- Service 类，是具体的业务逻辑，主要是通过Doctrine处理数据，主要是增删查改逻辑，也会有一些额外的逻辑。
- Apigility RESTFul 接口类，定义了RESTFul资源，及其相关的Method，这些接口类调用Service类来执行具体的任务。

了解一个组件的具体功能，应该从它的数据库结构开始，再看看都提供了哪些接口，
最后再看看service中有没有除增删查改以外的特殊业务逻辑。由此可以基本上了解一个组件所提供的功能。