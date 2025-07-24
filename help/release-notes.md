---
title: AEM Headless自适应Forms概述
description: AEM Headless自适应表单概述。
hide: true
exl-id: cd7c7972-376c-489f-a684-f479d92c37e7
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 4%

---


# 发行说明

欢迎使用Experience Manager Headless自适应表单早期采用者版本。 请阅读并获取开始使用并充分利用此版本的资源和说明。

使用Adobe Experience Manager Headless自适应表单构建具有前端框架(如React、Angular等)的表单应用程序。 使用自适应Forms Web SDK进行状态管理、验证以及与其他接触点集成。


早期采用者版本允许您在[本地开发环境](setup-development-environment.md)中使用Headless自适应表单。 您可以使用本地开发环境构建和测试Headless自适应表单。

Headless自适应表单将持续改进。 要了解最新动态，请定期访问此页面。本页提供了有关以下内容的信息：

* 抢先体验
* 最新版本
* 新增功能
* 改进功能
* 错误修复
* 已弃用功能
* 特殊说明
* 未来变更计划

<!-- 

## July 2022 (v0.22.1)

### New features

* Introduced the `validateFormData` API. It validates all the components against the rules and constraints an returns the list of errors. The validation takes place on the server.
* Introduced the `FormLoad` event.
* Introduced the `importData` and `exportData`.
* You can now dynamically add or remove items, that expect unqiue values, from a repeatable panel. You can use the `minItems` and `maxitems` constraint to set limit of item.
* You can now use constraint to set maximum file upload size, accepted file types, minimum files, and maximum files to upload.

### Improvements and bug fixes

* The service was executing some event handlers twice. The issue is fixed.
* Fixing Data Generation with different values of dataRef, name and type.

<!-- ### React Renderer component -->

## 早期采用者版本中可用的工件

在将Adobe Experience Manager Headless自适应表单提供给您的历程中，早期采用者版本中提供了以下构件：

### AEM Forms as a Cloud Service SDK

AEM Forms as a Cloud Service SDK可帮助您创建、存储和获取Headless自适应表单。 它还有助于为Headless自适应表单提供预填充、服务器端规则验证和提交服务。

### Forms Web SDK

Forms Web SDK提供API来验证应用于表单各个字段的约束，并提供挂钩以将表单的JSON结构连接到UI框架。 它还为Headless自适应表单提供&#x200B;React渲染器，以帮助将Headless自适应表单集成到应用程序。 可以使用以下Web SDK组件：

* **[@aemforms/af-react-components](https://www.npmjs.com/package/@aemforms/af-react-components)**
* **[@aemforms/af-react-renderer](https://www.npmjs.com/package/@aemforms/af-react-renderer)**
* **[@aemforms/af-core](https://www.npmjs.com/package/@aemforms/af-core)**

<!-- npm i --save @aemforms/af-react-components @aemforms/af-react-renderer @aemforms/af-core -->

#### Storybook

[Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/)提供了Headless自适应表单的不同组件的概述。 它还提供了所有受支持组件、其相应属性和约束的列表。

### Forms核心组件

<!-- Forms components are the structural elements that constitute the content of the form being authored. These components provide various form fields and ability to customize those fields. -->

核心组件是一组标准化的Web内容管理(WCM)组件，可帮助您加快表单的开发速度并降低表单维护成本。 Forms容器组件是一个核心组件。 它可帮助您在Forms as a Cloud Service SDK的自适应Forms编辑器中嵌入和渲染Headless自适应表单的JSON结构。

### 自适应Forms V2规范

Headless自适应表单规范提供了有关可用于定义Headless自适应表单的所有组件、约束和方法的详细信息。 规范以[PDF](/help/assets/Headless-Adaptive-Form-Specification.pdf)格式提供。

### HTTP和JS API

[HTTP API](https://opensource.adobe.com/aem-forms-af-runtime/api/)允许您列出、提取、验证、提交和跟踪Headless表单的提交状态。<!-- URL is 404! [JS APIs](https://opensource.adobe.com/aem-forms-af-runtime/jsdocs/) helps you use Headless adaptive forms with any JavaScript based UI framework. -->

### Visual Studio代码扩展

[Visual Studio代码扩展](visual-studio-code-extension-for-headless-adaptive-forms.md)以帮助创建有效的JSON结构。 它为JSON表单结构以及JSON结构的添加、删除或重命名组件等常用函数提供IntelliSense支持和验证。

<!-- ## What's next

The following features would be available in upcoming releases:

* HTTP APIs to invoke a business logic.
* Server-side capabilities (Prefill, server-side validation, generating Document of Record (DoR), Submitting to a Form Data Model or using Form Data Models for creating rules, and more).
* Continuous improvements to specifications and Headless adaptive form runtime.
* Use  Adaptive Forms editor for easier management and authoring Headless adaptive forms.
-->