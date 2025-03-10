### 介绍
java毕业设计，民宿管理系统
### 3000多套系统，需要联系
抠：3565014707 微：a13424421017

#### 软件架构
##### 整体架构模式
这是一个 民宿管理与预订系统，采用 前后端分离架构，包含以下模块：

管理后台（src/main/resources/admin）：基于 Vue.js + ElementUI 的 SPA 应用，供管理员管理民宿房源、订单、用户等。

用户端（src/main/resources/front）：基于 Layui + jQuery 的传统前端，面向用户提供民宿浏览、预订、支付、互动功能。

后端服务（src/main/java/com）：基于 Spring Boot + MyBatis 的 Java 服务，提供 RESTful API 和业务逻辑。
##### 分层架构设计
后端分层：

Controller层：controller 包（如 CommonController）处理 HTTP 请求，返回 JSON 数据。

Service层：service 包（CommonService）实现业务逻辑（如订单生成、库存管理）。

DAO层：dao 包（CommonDao）通过 MyBatis XML 文件（CommonDao.xml）操作数据库。

实体与数据模型：

entity 包定义数据库实体（如 DictionaryModel 数据字典实体）；

vo（值对象）和 view（视图模型）用于接口数据传输和复杂查询结果封装。

前端分层：

管理后台（Vue.js）：

视图层：views/modules 定义页面（如 fangjian 房源管理页）。

组件层：components 封装可复用组件（如 BreadCrumbs 面包屑导航）

状态管理：通过 Vuex（store.js）管理全局状态（如管理员权限）。

用户端（Layui）：

传统 MVC：通过 HTML + jQuery 实现动态页面（如 fangjianOrder/add.html 订单提交页）。

##### 关键技术特性
权限控制：

后端通过 AuthorizationInterceptor 拦截器和 @APPLoginUser 注解实现接口权限校验；

前端管理后台通过路由（router-static.js）限制页面访问权限。

异步处理：

MyThreadMethod 可能用于异步任务（如订单超时取消、短信通知）。

第三方服务集成：

BaiduUtil 可能用于地图服务（房源位置展示）或实名认证；

富文本编辑器（tinymce）用于发布带图文排版的房源介绍或公告。
#### 核心功能模块解析
##### 民宿管理模块
房源管理：

fangjian（民宿房源）：维护房源信息（名称、价格、设施、位置），支持图片上传（static/upload）。

dictionaryFangjian（房源类型字典）：定义房源类型（如“整租公寓”“独立房间”）。

订单管理：

fangjianOrder（民宿订单）：处理用户预订订单，支持在线支付（dictionaryFangjianOrder 支付方式管理）。

订单状态流转（待支付、已确认、已入住、已取消）。

##### 用户互动模块
社区互动：

forum（社区论坛）：用户发布旅行经验、房源评价，支持点赞和回复。

fangjianLiuyan（房源留言）：用户与房东实时沟通，解答预订问题。

评价与反馈：

用户对已完成订单的房源进行评分和文字评价。
###### 系统管理模块
数据字典：

dictionary 系列模块维护基础数据（如性别、订单状态、房源设施）。

用户与权限：

yonghu（用户管理）：审核用户注册信息，管理用户角色（普通用户/房东/管理员）。

news（新闻公告）：发布平台公告或促销活动。

###### 支付与财务
支付集成：

支持微信/支付宝支付（通过 dictionaryFangjianOrderPayment 配置支付渠道）。

财务统计：

后台统计房源收益、订单成交量，生成财务报表。
