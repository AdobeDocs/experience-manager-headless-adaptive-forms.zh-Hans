---
title: 了解Headless表单 — 概念和常见问题解答
description: 回答有关Headless表单是什么、它们与传统表单库有何不同、实施详细信息、UI控制、性能以及与框架和后端集成的常见问题。
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: headless forms， headless form library，无头表单库， adaptive forms，自适应表单，状态管理，验证，设计系统， SSR， CMS
hide: false
exl-id: a1b2c3d4-e5f6-7890-abcd-ef1234567890
source-git-commit: 780f06a39c75dbf8795ac7a971150410ed7981e9
workflow-type: tm+mt
source-wordcount: '2605'
ht-degree: 0%

---


# 了解Headless表单 — 概念和常见问题解答 {#understanding-headless-forms}

本指南解答了有关Headless表单的一般常见问题以及它们如何应用于AEM Headless自适应Forms。 使用它可决定何时使用Headless方法，以及如何在栈栈中实施、样式化和集成表单。

## 基础知识和理解 {#basics-understanding}

### 什么是Headless表单库？

**Headless表单库**&#x200B;是将&#x200B;**表单逻辑**（状态、验证、规则、提交）与&#x200B;**演示**（UI组件和样式）分开的表单解决方案。 “head”是可见的UI形式；“headless”表示库不规定或提供固定UI。 相反，它公开以下内容：

* **表单模型**（通常为JSON）：结构、字段、约束和规则。
* **API或挂接**&#x200B;以读取和更新表单状态、运行验证和处理提交。
* **事件和生命周期**，以便您的UI能够响应更改。

在AEM Headless自适应Forms中，表单是托管在Adobe Experience Manager上的[JSON结构](architecture.md)。 [Forms Web SDK](architecture.md#developer-tools)（客户端运行时）提供逻辑层 — 业务规则处理器、状态管理、验证，而应用程序提供呈现该结构的UI。

### Headless表单与传统表单库有何不同？

| 方面 | 传统表单库 | Headless表单库 |
|--------|---------------------------|------------------------|
| **UI** | 随附内置组件和样式 | 没有规定的UI；您自带组件 |
| **样式** | 库组件上的主题化或覆盖 | 完全控制；按原样使用设计系统 |
| **表单定义** | 通常为仅代码(JSX/HTML中的组件) | 通常数据驱动(来自CMS或API的JSON/架构) |
| **状态和验证** | 已绑定到库组件 | 通过API/挂接公开；任何UI都可以绑定到它们 |
| **渠道** | 通常为Web（有时为一个框架） | 相同的表单定义可以驱动Web、移动设备、聊天等。 |

使用AEM Headless自适应Forms，您可以在AEM中[创建并发布表单](create-and-publish-a-headless-form.md)一次；任何客户端(React、Angular、本机移动设备、聊天机器人)都可以[获取表单JSON](architecture.md)，并使用适用于该渠道的适当UI进行渲染。

### 为什么我应该使用Headless表单而不是基于UI的表单解决方案？

Headless表单非常适合于您需要：

* **设计系统一致性** — 使用现有组件和品牌，而无需对抗库默认值。
* **多渠道** - Web、移动和其他接触点的一个表单定义（请参阅[概述](overview.md)）。
* **CMS或后端驱动的表单** — 作者无需部署代码即可更改表单结构和规则；您的应用程序仅使用JSON。
* **框架灵活性** - [AF-core](https://www.npmjs.com/package/@aemforms/af-core)库独立于框架；提供React绑定是为了方便起见，但您可以为其他框架生成绑定。
* **后端功能** — 利用AEM Forms进行预填充、验证、提交、工作流和Forms数据模型，而无需锁定到特定UI栈栈中。

### 何时可以使用Headless方法？

在以下情况下使用Headless表单：

* 您拥有或需要强大的设计系统或组件库。
* Forms由非开发人员创作(例如，在CMS中)，并且必须在多个应用程序或渠道中使用。
* 您需要跨Web、移动或其他客户端使用相同的表单逻辑（验证、规则）。
* 您希望最大限度地减少重新渲染并保持表单逻辑可独立于UI测试。

在以下情况下，请考虑包含UI的传统表单库：

* 您需要在单个Web应用程序中快速设置工作表单，并且无需自定义UI或多渠道。
* 您的团队更喜欢仅在一个框架中的代码中定义表单。

### “无头”只是流行语，还是可以解决实际问题？

它解决了真正的体系结构问题：

* **关注点分离** — 表单结构、规则和验证在数据和逻辑层上实时；UI层仅呈现和调度用户操作。 这提高了可测试性和可重用性。
* **渠道独立性** — 一个表单定义可以驱动不同的UI(例如，React Web、React Native、Angular或语音)。 AEM Headless自适应Forms专为此而构建：[构建一次，跨React、SPA、Web、移动等交付](overview.md)。
* **不使用代码进行创作** — 业务用户可以在[自适应表单编辑器](create-a-headless-adaptive-form.md)中更改字段和规则；开发人员不需要重新部署内容更改。
* **与现有栈栈集成** — 您保留设计系统、状态管理和路由；Headless层仅处理表单状态、验证和提交。

## 实施和技术问题 {#implementation-technical}

### Headless表单如何管理状态？

在AEM Headless自适应Forms中，状态由&#x200B;**Forms Web SDK**&#x200B;管理：

* **业务规则处理器** — 接受表单JSON，管理字段状态，并执行JSON中定义的规则和事件处理程序。
* **React绑定器** — 在控制器上提供挂接（例如`useRuleEngine`），以便React组件接收当前状态和处理程序；非React UI可通过核心API使用相同的状态。
* **状态**&#x200B;包括字段值、可见性、有效性以及表单模型中定义的任何自定义属性。

您的UI组件接收状态和处理程序（例如，`[state, handlers] = useRuleEngine(props)`）；您从`state`进行渲染，并在用户交互时调用`handlers`。 运行时使状态与表单定义和规则保持同步。 查看[架构](architecture.md)和[使用自定义组件呈现Headless表单](developing-for-headless-forms-using-your-own-components.md)。

### 在Headless表单设置中如何进行验证？

验证是表单逻辑层的一部分：

* 以JSON格式定义&#x200B;**约束**（例如，必需、最小/最大、模式）。 Forms Web SDK应用这些约束并将验证状态（例如，有效/无效的错误消息）公开给组件。
* **客户端验证**&#x200B;由SDK基于表单结构应用；您的UI显示状态错误。
* **服务器端验证**&#x200B;可通过AEM API使用（例如，验证端点）；您可以在提交之前或提交期间进行验证。

您未在UI中实施验证逻辑，您只显示由运行时提供的验证状态和消息。

### 我能否将Headless表单与架构验证(Yup、Zod、Joi)集成？

内置验证由表单JSON约束驱动。 要使用Yup、Zod、Joi或类似功能：

* 您可以&#x200B;**从架构派生或生成** Headless自适应表单JSON（例如，将JSON架构转换为表单JSON），以便一个真实来源同时驱动架构验证和表单结构。
* 对于表单JSON之外的&#x200B;**自定义验证**，您可以在事件处理程序中或在提交之前运行自己的验证器(Yup/Zod/Joi)，并将结果推送到表单状态或块提交中。 集成点与用于状态和提交的挂接/API相同。

[自适应Forms规范](/help/assets/headless-adaptive-forms-specification.pdf)和[JSON公式](architecture.md)定义运行时使用的规则和约束模型。

### 如何处理异步验证（如用户名可用性）？

可以在应用程序层中实施异步验证：

* 在字段更改时，使用JSON格式的&#x200B;**规则或事件处理程序**（如果支持）来触发逻辑。
* 在&#x200B;**自定义组件**&#x200B;中，使用相同的状态/处理程序挂接调用后端（例如，用户名可用性API），然后更新字段的有效性或通过UI中显示的运行时API或本地状态显示错误。
* 或者，在模糊时或提交&#x200B;**之前执行检查**，如果异步检查失败，则使用自定义消息将字段状态设置为无效。

确切的模式取决于您的应用程序如何与[业务规则处理器](architecture.md)和自定义组件集成。

### 如何使用Headless表单将数据提交到API？

提交与UI脱钩：

* **AEM提交操作** — 您在AEM中将表单配置为提交到REST端点、电子邮件或集成(例如Microsoft Dynamics、Salesforce)。 表单通过AEM提交，后者处理实际的HTTP/后端调用。 请参阅[使用事件处理和提交表单数据](use-events-to-handle-and-submit-form-data.md)。
* **客户端提交** — 您的应用程序可以从运行时状态侦听提交或收集表单数据，并将其发送到您自己的API。 [HTTP API](https://opensource.adobe.com/aem-forms-af-runtime/api/)文档列表，提取、验证、提交和跟踪提交状态。
* **预填充** — 可以通过REST端点或服务器端预填充数据，以便在加载表单时填充状态。 请参阅[Storybook — 预填充示例](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data)。

## UI和设计控件 {#ui-design-control}

### 我可以对Headless表单使用我自己的设计系统或组件库吗？

是。 这是Headless表单的核心优势。 使用AEM Headless自适应Forms：

* 您&#x200B;**将您自己的组件映射**&#x200B;到表单模型（按字段类型或资源类型）。 查看[使用自定义组件渲染Headless表单](developing-for-headless-forms-using-your-own-components.md)和[使用Google Material UI React组件渲染Headless表单](use-google-material-ui-react-components-to-render-a-headless-form.md)。
* 运行时提供&#x200B;**状态和处理程序**；组件使用设计系统渲染，并调用处理程序，以使表单逻辑保持同步。
* 您可以使用&#x200B;**React Spectrum**、Material UI、Chakra UI或任何自定义组件库；可以为自定义组件（例如，Chakra UI、Vue.js）扩展[规范](/help/assets/headless-adaptive-forms-specification.pdf)。 请参阅[常见问题解答 — 自定义框架](faq.md#is-it-possible-to-use-headless-adaptive-forms-with-custom-frameworks)。

### Headless表单是否提供无障碍支持（ARIA、键盘处理）？

辅助功能在您提供的&#x200B;**UI层**&#x200B;中实现。 Headless层不会渲染DOM，因此它本身不会添加ARIA或键盘行为。 您可以通过以下方式获取辅助功能：

* 使用设计系统或库中的&#x200B;**可访问的组件**（许多组件包括ARIA和键盘支持）。
* 在自定义字段组件（标签、错误消息、焦点管理、键盘导航）中遵循&#x200B;**辅助功能最佳实践**。
* 确保您收到的表单结构和状态（例如，必需、无效、可见）反映在组件的ARIA属性和行为中。

如果您使用现成的基于React Spectrum的组件，则可从这些组件的内置辅助功能中获益。

### 如何处理复杂的UI组件（日期选取器、自定义下拉列表）？

将它们视为&#x200B;**自定义组件**，这些组件映射到JSON格式的相应字段类型或自定义资源类型：

* 实施您的组件以接受与其他字段组件相同的&#x200B;**props/state/handlers**（例如，通过`useRuleEngine`）。
* 使用&#x200B;**状态**&#x200B;获取值、可见性和有效性；使用&#x200B;**处理程序**&#x200B;更新值并触发验证。
* 使用所选的UI库呈现日期选取器或自定义下拉列表；发生更改时，使用新值调用处理程序，以使表单状态保持正确。

请参阅[使用自定义组件呈现按字段类型和资源类型映射的Headless表单](developing-for-headless-forms-using-your-own-components.md)。

### 我可以动态添加或删除字段（动态表单）吗？

表单结构由从服务器返回的&#x200B;**表单JSON**&#x200B;定义。 动态行为可通过以下方式实现：

* **JSON格式的规则** — 基于表达式显示/隐藏、启用/禁用或设置值。 [业务规则处理器](architecture.md)执行这些规则；您的组件会对`state.visible`等做出反应。
* **服务器驱动结构** — 不同的用户或上下文可以接收不同形式的JSON（例如，不同的步骤或部分），因此“动态”可能意味着“每个请求都具有不同的形式定义”。
* **客户端更改** — 如果您的应用程序可以修改表单模型（例如，在可重复结构中添加/删除项目），则运行时可以反映这一点；确切的功能取决于表单架构和运行时API。

[Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/)包含动态行为示例。

### 如何处理条件字段（根据输入显示/隐藏）？

条件可见性由JSON格式的&#x200B;**规则**&#x200B;驱动，由业务规则处理器评估。 您定义条件（例如“当字段A等于X时，显示字段B”）；运行时更新状态（例如，`state.visible`）。 您的组件只需要&#x200B;**遵循状态**（例如`if (!state.visible) return null;`）。 除了从状态呈现之外，显示/隐藏不需要额外的UI逻辑。 级联和条件行为记录在[自适应Forms规范](/help/assets/headless-adaptive-forms-specification.pdf)中，并在[Storybook — 级联字段](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/adaptive-form-dynamic-behaviour--options&args=formJson.items[0].fieldType：drop-down；formJson.items[0].minimum：！未定义；formJson.items[0].maximum：！未定义；formJson.items[0].label.value：Choose+number+of+options；formJson.items[0].enum[0]：1；formJson.items[0].enum[1]：2；formJson.items[0].enum[2]：3；formJson.items[1].fieldType：down)中演示。 另请参阅[常见问题解答 — 级联字段](faq.md#do-headless-adaptive-forms-support-cascading-fields)。

## 性能和可扩展性 {#performance-scalability}

### Headless表单的性能是否优于传统表单库？

它们可以是，但取决于实施：

* **目标更新** — 设计良好的Headless运行时仅更新状态并通知依赖它的组件，与单片式表单组件相比，可减少不必要的重新渲染。
* **较小的UI包** — 您只发送您使用的UI组件（您的设计系统），而不是完整的库组件集。
* **延迟加载** — 需要时可获取表单JSON；初始包可以保持较小。

性能还取决于您实施组件的方式（例如，避免不必要的重新渲染、记忆）。

### 它们如何最大限度地减少重新渲染？

* **状态形状** — 运行时在允许细粒度更新的结构中保持窗体状态，因此只有受影响的树部分需要重新呈现。
* **挂接设计** — 可以实施类似`useRuleEngine`的挂接以仅将组件订阅到它们使用的状态，因此父项或同级更改不会强制重新呈现每个字段。
* **您的责任** — 您可以在自定义组件中使用React最佳实践（例如，`React.memo`、稳定回调），进一步将重新渲染最小化。

### Headless表单是否适合大型、多步表单？

是，如果设计合理：

* **表单定义** — 可以在JSON中将大型表单拆分为步骤或部分；只有可见的步骤/部分才需要在UI中完全处于活动状态，并且如果支持，可以对隐藏部分的规则进行延迟评估。
* **状态** — 运行时有一个一致的表单状态；步骤导航只是显示/隐藏节，或者更新“当前步骤”而不复制数据。
* **分块和延迟加载** — 您可以在分块中获取JSON表单，或按步骤加载其他部分，以保持初始有效负载和解析成本较低。

对于非常大的表单，请考虑结构（例如，向导步骤）、服务器驱动的表单变体，以及使用实际负载测量渲染和规则执行。

## 整合与生态系统 {#integration-ecosystem}

### Headless表单能否与Next.js/SSR/服务器操作配合使用？

* **Next.js / React** — 是。 React渲染器和挂接在React环境中工作。 在客户端组件中使用Forms Web SDK；根据需要从服务器或客户端上的JSON中获取。
* **SSR** — 您可以在服务器上获取表单JSON并将其传递给客户端，以使表单与数据水合。 表单交互（状态、验证、规则）在加载SDK的客户端上运行。 避免在SSR期间渲染依赖仅客户端状态的表单字段，或使用在客户端上水合的占位符。
* **服务器操作(Next.js)** — 您可以从提交处理程序中调用服务器操作：当用户提交时，您的客户端代码会收集表单数据（从Headless状态）并调用服务器操作，而不是在AEM提交端点之外调用服务器操作。

### Headless表单如何与CMS、Headless Commerce或后端系统集成？

* **CMS** - AEM是表单定义的CMS：作者创建和发布表单JSON。 其他CMS可以引用或链接到表单URL/API。 您的应用程序会从AEM（或CDN）中提取表单，并可以选择从其他CMS中提取副本或布局。
* **预填充和提交** - [预填充](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data)和提交可以点击REST端点，因此您可以从CRM、DAM或商务后端预填充和提交到相同或不同的系统。 AEM Forms还支持[Microsoft Dynamics和Salesforce](faq.md)、REST、电子邮件和自定义提交操作。
* **Forms数据模型** - AEM Forms提供了一个Forms数据模型以连接到不同的数据源；Headless表单可以使用这些功能进行预填充、验证和提交，而无需您自己构建每个集成。

对于移动和离线场景，推荐的方法是[构建您自己的应用程序，并通过Headless自适应Forms API获取表单定义](mobile-forms-best-practices.md)。

## 另请参阅 {#see-also}

* [概述](overview.md)
* [架构](architecture.md)
* [常见问题解答](faq.md)
* [创建和发布Headless表单](create-and-publish-a-headless-form.md)
* [Headless自适应表单API](https://opensource.adobe.com/aem-forms-af-runtime/api/)
* [代码游乐场](https://experienceleague.adobe.com/landing/aem-headless-forms/developer/code.html?lang=zh-Hans)
* [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/)
