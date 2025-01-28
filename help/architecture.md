---
title: Headless自适应表单架构
description: 了解AEM Forms Headless自适应Forms的架构，以及它如何帮助您快速构建各种平台的表单。 本文深入介绍了Headless自适应Forms的工作原理，以及如何将其与各种应用程序集成以简化表单构建过程。
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: headless，自适应表单，架构
hide: false
exl-id: ee7096d8-89e2-41e0-85e7-b26457df96fb
source-git-commit: c46ac28e490a09d6f563c4b5673d30a53c277a69
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 0%

---


# Headless自适应表单的工作原理

Headless自适应表单本质上是一个JSON结构（架构），它包含表单字段（文本框、选项和更多字段）和相应的规则（条件逻辑）以向表单添加交互行为。 您可以在应用程序或网站中使用REST API来请求托管的JSON结构，并在应用程序或网站中将JSON结构本机渲染为表单。 单个Headless自适应表单可以为多个网页和应用程序提供服务，而无需对其进行任何应用程序或网站特定的更改。

![Headless自适应表单的工作方式](/help/assets/how-headless-adaprive-forms-work.png)

## 架构 {#architecture}

典型的Headless自适应表单架构构成了Adobe Experience Manager Forms Server、托管在Adobe Experience Manager Forms Server上的Headless自适应表单，以及用于特定于渠道的表单呈现的前端应用程序(网站、移动应用程序、JavaScript应用程序、聊天应用程序等)。

Headless自适应表单部署的典型架构如下所示：

![架构](/help/assets/headless-af-architecture.png)

<!-- 

You can use the React renderer component shipped with Headless adaptive forms to render an Adaptive Form or build your own custom component to natively render a Headless Form in a website or an application or use any UI framework or programming language to build your own components to render your forms.

A typical Headless adaptive forms architecture constitutes an Adobe Experience Manager Server, JSON structure of forms, various frontend apps for channel-specific form renditions.

![Architecture](/help/assets/headless-af-architecture.png) -->

### Headless自适应表单实施的组件

**Adobe Experience Manager Server**：除了充当Headless自适应表单的主机之外，Adobe Experience Manager还提供以下后端功能：

* RESTful API用于列出、提取、预填充、验证、提交、跟踪Headless表单的提交状态。
* 可视编辑器，可轻松开发Headless自适应表单。
* Forms数据模型，用于接收数据或将数据发送到不同的数据源。
* 用于自动执行复杂任务的工作流引擎。

**Headless自适应表单**： Headless自适应表单以.json文件表示。 JSON结构定义表单的组件、约束和结构。

**前端应用程序**：前端应用程序，如SPA （单页应用程序）、移动应用程序、JavaScript应用程序，使用Headless自适应表单（JSON表单表示形式）并在客户端上渲染表单。 您可以使用随Headless自适应表单提供的React渲染器组件来渲染自适应表单，或构建您自己的自定义组件以本机渲染Headless自适应表单。

<!-- ### Understanding Headless adaptive forms definition -->



### 开发人员工具

在典型的开发周期中，您需要开始在Adobe Experience Manager Forms服务器上创建和托管Headless自适应表单。 在第二步中，映射UI组件或使用公共UI组件库(如Google素材UI或Chakra UI)来设置表单的样式。 在上一步中，您在应用程序中获取并显示Headless自适应表单(网站、移动应用程序、JavaScript应用程序、聊天应用程序或许多其他表面)。

以下工具可帮助您创建Headless自适应表单并将其集成到应用程序：

**Forms Web SDK（客户端运行时）**： Forms Web SDK是客户端JavaScript库。 它允许您对表单字段应用客户端验证，维护表单的状态，并提供挂接以将表单与UI层或自适应表单渲染组件连接。 它允许客户验证应用于表单各个字段的限制，并挂接以将表单的JSON结构连接到UI框架。 Forms Web SDK包含以下组件：

* **业务规则处理器**：业务规则处理器接受表单JSON结构作为输入，管理JSON中存在的表单字段状态、执行规则和事件处理程序。
* **React绑定器**：提供挂接控制器以向窗体组件添加状态。 在预填表单时它也很有用。
* **组件库**：它提供React Spectrum组件，并在React Binder模块中使用挂接向这些组件添加状态。

除了提供用于验证应用于表单各个字段的约束的API之外，Forms Web SDK还提供挂钩，将Headless自适应表单连接到UI框架。 它还为Headless自适应表单提供&#x200B;React渲染器，以帮助将Headless自适应表单集成到应用程序。 可以使用以下Web SDK组件：

* **[@aemforms/af-react-components](https://www.npmjs.com/package/@aemforms/af-react-components)**
* **[@aemforms/af-react-renderer](https://www.npmjs.com/package/@aemforms/af-react-renderer)**
* **[@aemforms/af-core](https://www.npmjs.com/package/@aemforms/af-core)**

所有这些组件都包含在AEM原型中。 为Headless自适应表单创建AEM Archetype 37或更高版本项目时，项目中会包含以上列出库的最新版本。

* **代码游乐场**： [代码游乐场](https://experienceleague.adobe.com/landing/aem-headless-forms/developer/code.html?lang=en)是一个交互式环境，旨在供开发人员试验、了解和测试Headless自适应Forms的功能。

**已启动应用程序**：Adobe还发布了已启动应用程序，可帮助您快速启动Headless自适应表单。

<!-- **View Library (UI Layer)**: A custom form application built in a front-end language. You can use react, Angular, Flutter, NPM, Vue.js, Ionic, BootStrap, or any other language to built front end. You can also use the Headless adaptive forms Super Component, provided out-of-the-box, inside a react application to render a Headless adaptive form. Headless adaptive forms super component makes use of OOTB react spectrum -based form components to render the Headless adaptive form. 

Core-Components: It enables use to render an Adaptive Form using JSON structure. It uses rule grammar to help create dynamic field interactions. The rule grammar is based on [JSON formula](http://github.com/adobe/json-formula/). You can develop your own renderer or embed the React based Adaptive Forms renderer, provided OOTB, in your front-end app to render the form. -->

**Storybook**： [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/)提供了Headless自适应表单的不同组件的概述。 它还提供了所有受支持组件、其相应属性和约束的列表。

**Visual Studio代码扩展**： [Visual Studio代码扩展](visual-studio-code-extension-for-headless-adaptive-forms.md)以帮助创建有效的JSON结构。 它为JSON表单结构以及JSON结构的添加、删除或重命名组件等常用函数提供IntelliSense支持和验证。

**HTTP和JavaScript API**： [HTTP API](https://opensource.adobe.com/aem-forms-af-runtime/api/)允许您列出、提取、验证、提交和跟踪Headless表单的提交状态。 [JS API](https://opensource.adobe.com/aem-forms-af-runtime/jsdocs/)可帮助您将Headless自适应表单与任何基于JavaScript的UI框架结合使用。

**JSON公式**：它是Forms表达式语法的实现，可帮助您查询JSON结构并为Headless自适应表单创建规则。 语法是类似电子表格的函数和运算符以及[JMESPath](https://jmespath.org/)一种JSON查询语言的混合。 您可以使用[游乐场](https://opensource.adobe.com/json-formula/dist/index.html)来探索JSON公式语法和功能。

**自适应Forms版本2.0规范**：自适应Forms版本2.0规范提供了有关可用于定义Headless自适应表单的所有组件、约束和方法的详细信息。 规范以[PDF](/help/assets/headless-adaptive-forms-specification.pdf)格式提供。

