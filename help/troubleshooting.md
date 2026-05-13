---
title: Headless自适应Forms疑难解答
description: Headless自适应Forms疑难解答
keywords: headless，自适应表单，故障排除
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
index: true
exl-id: bfb7e688-d2be-4aaa-ac9b-147cbd74b516
TQID: https://experienceleague.adobe.com/yjO3VhNmqIAyfnD7daHB7eAEUNmaAjnUgEm0fHc1ArY
product_v2:
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 12f711845becc93305717fb0c95e82355a8e97a5
workflow-type: tm+mt
source-wordcount: 152
ht-degree: 7%

---

# 疑难解答

## 无法在本地开发环境中部署原型项目

### 问题

当您使用`mvn -PautoInstallPackage clean install`或类似命令部署AEM项目时，该项目无法部署。

### 原因

由于`node.js`或`NPM`的版本不受支持或安装损坏，可能发生这种情况。

### 解决办法

1. 从您的环境中完全[删除当前安装的Node.JS](https://khushwantsehgal.wordpress.com/2022/06/28/how-to-remove-node-js-completely-from-windows-10/)。

1. 安装`node.JS 16.13.0`或更高版本的`NPM`。

1. 重新启动计算机。


## `mvn clean install`命令无法运行

### 问题

当您使用`mvn clean install`或类似命令部署AEM项目时，该命令无法运行。

### 原因

如果未安装Git，则可能会发生这种情况。

### 解决办法

下载并安装[最新版本的Git](https://git-scm.com/downloads)。 如果您是初次使用Git，请参阅[安装Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)。
