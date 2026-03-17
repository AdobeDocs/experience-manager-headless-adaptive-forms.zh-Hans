---
title: 移动表单最佳实践
description: 对于移动和离线表单用例，请构建您自己的本机应用程序，并通过Headless自适应Forms API获取表单定义。 本机移动设备应用程序的推荐方法。
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: 移动表单，本机应用程序，离线表单， Headless API
index: true
exl-id: 6f25039f-61fc-4366-9e17-6b2809162c58
source-git-commit: 86129488bec7faed87600a237ac034ca1b601187
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# 移动表单最佳实践 {#mobile-forms-best-practices}

对于移动和离线表单用例，建议构建您自己的本机应用程序，并通过Headless自适应Forms API获取表单定义。 这使您能够完全控制移动体验，并确保随着移动平台的发展提供持续的支持。

## 推荐的方法 {#recommended-approach}

构建符合以下条件的本机移动应用程序（iOS或Android）：

1. **获取Headless表单定义** — 使用[Headless自适应Forms API](https://opensource.adobe.com/aem-forms-af-runtime/api/)按需检索表单JSON（例如，当用户打开表单或在应用程序中导航到表单时）。 您可以列出可用的表单，然后通过ID获取表单定义。

2. **在应用程序中呈现表单** — 使用首选的UI框架（例如，React Native或本机视图）从JSON呈现表单。 您可以在适合您栈栈的位置使用Forms Web SDK和现有Headless自适应表单React组件，也可以构建您自己的使用相同JSON结构的渲染器。

3. **可选支持脱机** — 在您的应用程序中实施本地存储和同步。 例如，联机时缓存表单定义，在本地保存草稿，并在设备重新联机时提交或同步数据。

这种方法可保持应用程序在Android和iOS更改时的可维护性，并使用受支持的Headless自适应Forms平台进行表单创作、验证和提交。

## 快速入门 {#getting-started}

* [AEM Headless自适应表单概述](overview.md) — 功能和概念。
* [无头自适应表单API](https://opensource.adobe.com/aem-forms-af-runtime/api/) — 以编程方式列出、获取、验证和提交表单。
* [架构](architecture.md) - Headless自适应表单的工作方式以及前端应用程序如何使用它们。

有关分步集成，请参阅[创建并发布Headless表单](create-and-publish-a-headless-form.md)和[开发人员门户](https://experienceleague.adobe.com/landing/aem-headless-forms/developer.html?lang=en)。
