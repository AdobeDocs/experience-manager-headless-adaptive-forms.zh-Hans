---
title: AEM Headless自适应表单概述
description: AEM Headless自适应表单概述。
hide: true
exl-id: cd7c7972-376c-489f-a684-f479d92c37e7
source-git-commit: 0127f8ddede38083f0932b0e8d7efdd0dd77c3a6
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 3%

---


# 发行说明

欢迎使用Experience ManagerHeadless自适应表单早期采用者版本。 请阅读并获取开始使用并充分利用此版本的资源和说明。

您可以使用Adobe Experience Manager Headless自适应表单通过React、Angular等前端UI框架构建表单应用程序，并使用Adaptive Forms Web SDK实现状态管理、验证和与其他各种接触点集成等功能。

率先采用者版本允许您在中使用无头自适应表单 [本地开发环境](setup-development-environment.md). 您可以使用本地开发环境构建和测试Headless自适应表单。

Headless自适应表单将持续改进。 要了解最新动态，请定期访问此页面。本页提供了有关提前访问、最新版本、新增功能、改进、错误修复、已弃用功能、特殊说明和未来更改计划的信息。

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

### AEM FORMSAS A CLOUD SERVICESDK

AEM Formsas a Cloud ServiceSDK可帮助您创建、存储和获取Headless自适应表单。 它还有助于为Headless自适应表单提供预填充、服务器端规则验证和提交服务。

### Forms Web SDK

Forms Web SDK提供API来验证应用于表单各个字段的约束，并提供挂钩以将表单的JSON结构连接到UI框架。 它还为Headless自适应表单提供&#x200B;React渲染器，以帮助将Headless自适应表单集成到应用程序。 以下Web SDK组件可用：

* **[@aemforms/af-react-components](https://www.npmjs.com/package/@aemforms/af-react-components)**
* **[@aemforms/af-react-renderer](https://www.npmjs.com/package/@aemforms/af-react-renderer)**
* **[@aemforms/af-core](https://www.npmjs.com/package/@aemforms/af-core)**

<!-- npm i --save @aemforms/af-react-components @aemforms/af-react-renderer @aemforms/af-core -->

#### Storybook

[Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/) 概述Headless自适应表单的不同组件。 它还提供了所有受支持组件、其相应属性和约束的列表。

### Forms核心组件

<!-- Forms components are the structural elements that constitute the content of the form being authored. These components provide various form fields and ability to customize those fields. -->

核心组件是一组标准化的Web内容管理(WCM)组件，可帮助您加快表单的开发速度并减少维护成本。 Forms容器组件是一个核心组件。 它可帮助您在Formsas a Cloud ServiceSDK的自适应Forms编辑器中嵌入和渲染Headless自适应表单的JSON结构。

### 自适应Forms V2规范

Headless自适应表单规范提供了有关可用于定义Headless自适应表单的所有组件、约束和方法的详细信息。 该规范位于 [PDF](/help/assets/Headless-Adaptive-Form-Specification.pdf) 格式。

### HTTP和JS API

[HTTP API](https://opensource.adobe.com/aem-forms-af-runtime/api/) 允许您列出、提取、验证、提交、跟踪Headless表单的提交状态。 [JS API](https://opensource.adobe.com/aem-forms-af-runtime/jsdocs/) 帮助您将Headless自适应表单与任何基于JavaScript的UI框架结合使用。

### Visual Studio代码扩展

[Visual Studio代码扩展](visual-studio-code-extension-for-headless-adaptive-forms.md) 以帮助创建有效的JSON结构。 它为JSON表单结构以及JSON结构的添加、删除或重命名组件等常用功能提供IntelliSense支持和验证。

<!-- ## What's next

The following features would be available in upcoming releases:

* HTTP APIs to invoke a business logic.
* Server-side capabilities (Prefill, server-side validation, generating Document of Record (DoR), Submitting to a Form Data Model or using Form Data Models for creating rules, and more).
* Continuous improvements to specifications and Headless adaptive form runtime.
* Use  Adaptive Forms editor for easier management and authoring Headless adaptive forms.
-->