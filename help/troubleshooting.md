---
title: Headless自适应Forms疑难解答
description: Headless自适应Forms疑难解答
keywords: headless，自适应表单，故障排除
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: bfb7e688-d2be-4aaa-ac9b-147cbd74b516
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 6%

---

# 疑难解答

## 无法在本地开发环境中部署原型项目

### 问题

当您使用`mvn -PautoInstallPackage clean install`或类似命令部署AEM项目时，该项目无法部署。

### 原因

由于`node.js`或`NPM`的版本不受支持或安装损坏，可能发生这种情况。

### 解决方案

1. 从您的环境中完全[删除当前安装的Node.JS](https://khushwantsehgal.wordpress.com/2022/06/28/how-to-remove-node-js-completely-from-windows-10/)。

1. 安装`node.JS 16.13.0`或更高版本的`NPM`。

1. 重新启动计算机。


## `mvn clean install`命令无法运行

### 问题

当您使用`mvn clean install`或类似命令部署AEM项目时，该命令无法运行。

### 原因

如果未安装Git，则可能会发生这种情况。

### 解决方案

下载并安装[最新版本的Git](https://git-scm.com/downloads)。 如果您是初次使用Git，请参阅[安装Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)。
