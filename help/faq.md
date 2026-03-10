---
title: 有关Headless自适应Forms的常见问题解答
description: 常见问题解答
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: headless，自适应表单，常见问题解答
hide: false
exl-id: 5bfc307d-96a3-4007-b65f-32176ecdb710
source-git-commit: 780f06a39c75dbf8795ac7a971150410ed7981e9
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 0%

---

# 常见问题解答（FAQ） {#headless-adaptive-forms-faq}

## 我是否应该知道React.js才能使用Headless自适应表单？

您可以使用任何框架、库或语言来渲染Headless自适应表单，并使用Adobe的REST API来验证和提交表单。 现成提供的AF核心库与框架无关。 为方便起见，也为您提供了现成的React-Render和React-component库。 您可以构建自己的组件；您不仅可以使用提供的组件。


<!-- 
## Did Adobe release a new AEM Archetype for Headless adaptive forms?

You can use Archetype 37 with flag `includeFormsheadless` or later flag to create an AEM project with Headless adaptive forms functionality. 

-->

## 是否需要Forms as a Cloud Service沙盒才能使用Headless自适应表单？

您可以使用入门应用程序开始开发和设置Headless自适应表单的样式。 您需要Forms as a Cloud Service来托管和提供Headless自适应表单以及后端表单功能。

<!-- ## Do I need an archetype project to develop Headless adaptive forms?

You can use the starter app to start developing and styling your Headless adaptive forms. Later on, you can use the 
archetype project to deploy the finished Headless adaptive forms and corresponding custom code, created using starter app, to Forms as a Cloud Service environment. The Forms as a Cloud Service environment helps you test and productionize the forms. -->

## 在哪里可以获取Headless自适应表单的预览？ {#storybook-example}

您可以使用入门应用程序呈现和预览自定义Headless自适应表单。 您还可以修改[storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--introduction)示例以预览Headless自适应表单。

![](/help/assets/storybook-example.png)

## 是否可以将Headless自适应表单与自定义框架结合使用？

Headless自适应表单基于[标准规范](/help/assets/headless-adaptive-forms-specification.pdf)。 您可以扩展规范以使用它来构建自定义组件。 例如，Chakra UI、Vue.js等的组件。

## Headless自适应表单是否支持层叠字段？

在级联字段中，第二个字段的内容取决于在第一字段中选择的内容。 [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/adaptive-form-dynamic-behaviour--options&args=formJson.items[0].fieldType：drop-down；formJson.items[0].minimum：！未定义；formJson.items[0].maximum：！未定义；formJson.items[0].label.value：Choose+number+of+options；formJson.items[0].enum[0]：1；formJson.items[0].enum[1]：2；formJson.items[0].enum[2]：3；formJson.items[1].fieldType：down)提供了级联字段的示例。

## Headless自适应表单是否允许使用个性化数据预填表单？

Headless自适应表单允许使用个性化数据预填表单。 [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data)提供了预填充Headless自适应表单的示例。

<!-- >
## Can I use existing Adaptive Forms editor to create a Headless adaptive form?

At this moment, you use the Adaptive Form Editor to specify the JSON structure and set submit action for the forms. Support for drag-and-drop components, applying rules using editor, and more editor-related options would be available later in the beta phase. Keep a watch on release notes.  -->

## 我能否将Headless自适应表单用于Angular SPA？

您可以使用Web SDK将Headless自适应表单与Angular SPA集成。 它独立于任何框架。 您可以将React SDK用作参考。

<!-- ## Should the `-r prerelease` switch be used every time to start the AEM SDK instance or only for the first time?

During the limited release program, use the `-r prerelease` switch every time you start the AEM SDK instance. 

## What is AEM Forms add-on (.far file) and how to install it?

Adobe Experience Manager Forms as a Cloud Service feature archive provides tools to create Headless adaptive forms on the local development environment. To install the feature archive, see [Setup development environment](setup-development-environment.md).

<!-- 
## Where do one get the license.properties file from?

You do not require a license.properties file to run AEM Cloud Service SDK. 

-->

## 是否有任何插件可简化Headless AF的开发？

是 — Visual Studio代码扩展允许您在JSON中手动创作Headless自适应表单。

## 推荐使用哪种方法处理移动设备表单或离线表单？ {#mobile-offline-forms}

构建您自己的本机应用程序，并通过Headless自适应Forms API获取表单定义。 您可以选择实施离线支持（例如，本地存储和同步）。 请参阅[移动设备表单最佳实践](mobile-forms-best-practices.md)，以了解推荐的方法以及指向API的链接。

## 如何将GraphQL或headless API与AEM Forms结合使用？

AEM Headless自适应Forms使用&#x200B;**HTTP/REST API**，而不是GraphQL。 应用程序调用这些API来列出表单、获取表单定义(JSON)、验证、提交和跟踪提交状态。 使用[Headless自适应表单HTTP API](https://opensource.adobe.com/aem-forms-af-runtime/api/)获取完整引用。 有关如何获取和渲染表单，请参阅[架构](architecture.md)和[了解Headless表单](understanding-headless-forms.md)。

## 如何使用Adobe AEM Forms中的React组件实施和设置Headless表单样式？

您可以使用自己的React组件和CSS（或UI库，如材质UI）来实施和设置Headless表单的样式。 表单逻辑（状态、验证和规则）来自Forms Web SDK和表单JSON；您的应用程序提供用于渲染它的UI。

* 要使用React UI库为Headless表单设置样式，请参阅[使用自定义react库呈现Headless表单](use-google-material-ui-react-components-to-render-a-headless-form.md)。
* 要生成自定义React组件并将其映射到表单字段，请参阅[使用自定义组件渲染Headless表单](developing-for-headless-forms-using-your-own-components.md)。

有关何时使用Headless表单、状态管理和验证等概念，请参阅[了解Headless表单](understanding-headless-forms.md)。

## 如何使用自定义CSS、主题、规则编辑器和Headless表单实施和自定义AEM Forms？

**Headless表单：**&#x200B;样式和外观完全由您控制。 您使用自己的React（或其他）组件和自己的CSS；没有内置主题。 请参阅[使用自定义react库呈现Headless表单](use-google-material-ui-react-components-to-render-a-headless-form.md)和[使用自定义组件呈现Headless表单](developing-for-headless-forms-using-your-own-components.md)以实施和样式Headless表单。

**经典AEM Forms（主题、规则编辑器、可视编辑器）：**&#x200B;自定义CSS、主题编辑器和规则编辑器适用于经典（非headless）自适应Forms创作体验。 有关这些主题，请参阅Experience League上的[AEM Forms文档](https://experienceleague.adobe.com/docs/experience-manager-forms.html)。

## Headless自适应表单能否连接到任何CRM以读取或写入数据？

您可以使用Microsoft Dynamics和Salesforce提交或预填充Headless自适应表单。 除CRM外，Headless自适应表单支持使用REST端点、电子邮件和自定义提交操作提交或预填充。
