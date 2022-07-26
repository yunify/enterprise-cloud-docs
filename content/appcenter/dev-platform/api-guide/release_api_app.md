---
title: "应用上架"
description: 介绍如何上架 API 应用。
keyword: AppCenter, API 应用, 上架
draft: false
weight: 1
---

## 简介

服务商/开发者可以在 AppCenter 应用开发平台创建 API 应用，将部署的 API 服务上架到 AppCenter 应用市场进行售卖，用户选购 API 应用后，可以通过 API 服务调用地址来获取相关的服务（数据或算法）。

## 前提条件

- 已入驻 AppCenter 应用市场。具体操作请参见[服务商入驻流程](/appcenter/dev-platform/serviceprovider/20_contracts/)。
- 已在云平台 API 网关上部署您的 API 服务。具体操作请参考 [API 网关文档](/middware/api_gateway/manual/create_apiservice/)。

## 上架流程

1. 在 API 网关上部署相关 API 服务，操作详情可参见 [API 网关文档](/middware/api_gateway/manual/create_apiservice/)。
2. 在 AppCenter 应用开发平台创建 API 应用并提交 AppCenter 管理后台审核。
3. 审核通过后，应该自动上架到应用市场。

## 操作步骤

1. 登录 AppCenter 应用开发平台，点击“应用”部分的“+”号按钮，弹出**创建应用**窗口。

   <img src="/appcenter/dev-platform/_images/add_app.png"  style="zoom:80%;" />

2. **应用类型**选择`API 应用`，然后设置**应用名称**及**应用概述**，点击**创建应用**，进入**应用设置**页面。

   <img src="/appcenter/dev-platform/_images/create_api_app.png"  style="zoom:80%;" />

3. 点击**增加规格**，设置**规格信息**及**套餐价格**。

   可新增规格配置，最多支持 50 个规格。规格参数说明如下表。

   <table>
     <thead>
       <tr><td colspan="2">参数</td><td>说明</td></tr>
     </thead>
       <tr><td rowspan="3">规格信息</td><td>规格排序</td><td>输入 0-10000 的整数值，值越大，排序越靠前。</td></tr>
       <tr><td>规格名称</td><td>规格是用户购买时的重要参考，请规范命名。</td></tr>
    		<tr><td>API 服务</td><td>选择当前 API 应用需要关联的 API 服务。<br/>先选择区域，然后选择区域下的 API 服务。<div style="background-color: #D8ECDE; padding: 10px 24px; margin: 10px 0; border-left: 3px solid #00a971;"><b>说明</b><br/>API 服务需要提前在 API 网关进行部署。</div></td>
   </tr>
       <tr><td colspan="2">套餐价格</td><td>设置当前规格下的套餐包信息。可添加多个套餐包。</td></tr>
   </table>

4. 设置完成后，点击页面右上角**保存**。

5. 点击**前往应用信息**，进入应用信息设置页面。

6. 设置应用信息。

   应用信息参数说明如下表。

   | 参数             | 说明                                                         |
   | :--------------- | :----------------------------------------------------------- |
   | 应用 ID          | 系统自动生成，不可修改。                                     |
   | 应用名称         | API 应用的名称。字数不可超过 50 字。                         |
   | 概述             | 应用的概述会出现应用名称下方。字数不可超过 30 字。           |
   | 应用描述         | 对应用的描述说明，将出现在应用展示详情页面。                 |
   | 商品描述（可选） | 不在应用中心展示，可不填写。                                 |
   | 用户案例（可选） | 填写产品成功合作的案例详情。支持 Markdown 编辑模式进行编写。可不填写。 |
   | 使用说明（可选） | 应用的使用说明。支持 Markdown 编辑模式进行编写或输入指导文档链接。 |
   | 服务支持（可选） | 填写用户使用中遇到问题可以寻求支持的联系方式，如电话、邮箱、服务时间等信息。 |
   | 服务条款（可选） | 与用户之间的服务条款。支持 Markdown 编辑模式进行编写或输入外部链接。 |
   | 应用分类         | 选择该 API 应用所应用的产品类别。                            |
   | 应用图标         | 上传应用图标。<br/>图片支持 JPG 和 PNG 格式，尺寸 96 x 96 px。 |
   | 应用截图（可选） | 上传应用相关截图，用于应用上架后的详情页展示。<br/>图片不超过 6 张，支持 JPG 和 PNG 格式，尺寸 1024 x 768 px。 |
   | 网站（可选）     | 可选项，填写公司网站信息。                                   |

7. 应用信息设置完成后，点击页面右上角**保存**。

8. 点击**应用设置**，进入**应用设置**页面，点击**提交审核**。

   >**说明**
   >
   >完整、准确的应用信息能够让您的应用更容易被用户搜索到，也是应用审核过程中管理员严格审核的内容之一，请尽量按照规范填写完整、准确。

9. 提交后，在**全部应用**页面，可以看到应用处于`审核中`状态，请耐心等待审核通过。

   <img src="/appcenter/dev-platform/_images/app_on_check.png" style="zoom:80%;" />

   审核通过后，应用状态变为`已上架`，应用将自动上架到应用市场，即可在应用市场查看到该应用的详细信息。用户也可通过应用市场或控制台应用中心查看、购买该应用。

## 相关文档

- [购买 API 应用](/appcenter/market/manual/20_purchase_app/40_api_app/)
- [管理应用](/appcenter/market/manual/30_mgmt_app/)

