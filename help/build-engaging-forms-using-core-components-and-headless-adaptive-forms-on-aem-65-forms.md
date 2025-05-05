---
title: 使用核心组件和 Headless 构建具有吸引力的表单
seo-title: Build Engaging Forms Using Core Components and Headless
description: 使用核心组件和 Headless 构建具有吸引力的表单
seo-description: Build Engaging Forms Using Core Components and Headless
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
topic-tags: develop
hide: true
exl-id: 07a71aac-de38-4839-b8d6-b47c3f575eb3
source-git-commit: 999c3d092d03d7a82363bc94ce79ceb33bf0df7e
workflow-type: tm+mt
source-wordcount: '2130'
ht-degree: 58%

---

# 在AEM 6.5 Forms上使用核心组件和Headless自适应Forms构建吸引人的Forms {#build-engaging-forms-using-core-components-and-headless}

## 实验室概述 {#lab-overview}

在此动手实验室中，您将学习：

如何使用AEM Forms轻松地使用与AEM Sites一致的最新核心组件创建自适应Forms，通过将自适应Forms作为Headless表单交付到Web、移动和聊天来实现全渠道数据捕获体验。 您还将了解有关样式化、自定义项和前端开发的最佳实践。

## 要点 {#key-takeaways}

* **业务敏捷性**：作为商业用户，我可以轻松地为多个渠道创作表单体验。

* **前端开发人员的力量**：作为前端开发人员，我可以使用 Headless 表单来控制最终用户体验。

* **开发人员速度**：作为开发人员，我可以轻松且一致地自定义 Sites 和 Forms 组件。

## 开始之前 {#pre-requisites}

要在实验室中使用此手，请执行以下操作：

* 安装[最新版本的Git](https://git-scm.com/downloads)。 如果您是初次使用Git，请参阅[安装Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)。

* 安装[Node.js 16.13.0或更高版本](https://nodejs.org/en/download/)。 如果您是初次使用Node.js，请参阅[如何安装Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs)。

* [在您的AEM 6.5 Forms环境中启用Headless自适应Forms](enable-headless-adaptive-forms-and-core-components.md)。

* 安装[Microsoft Visual Studio Code](https://code.visualstudio.com/download)或任何纯文本编辑器。 文档中的示例使用了Microsoft Visual Studio Code。

## 第 1 课 {#lesson-1}

### 目标 {#lesson-1-objectives}

熟悉AEM 6.5 Forms环境。

### 课程背景 {#lesson-1-context}

在本课程中，您可以通过导航用户界面来熟悉AEM 6.5 Forms。

### 练习 {#lesson-1-excercise}

1. 打开浏览器，输入创作环境的URL。 例如：
   [https://localhost:4502](https://localhost:4502)。

1. 登录后，导航至 AEM Forms UI。单击&#x200B;**表单**。

   ![](/help/assets/screenshot2028113829.png){width="50%" align="left"}

1. 单击&#x200B;**表单和文档**。关闭任何与偏好设置或信息相关的弹出窗口。

   ![](/help/assets/screenshot2028113929.png){width="50%" align="left"}

   将显示所有可用的表单。

   ![](/help/assets/screenshot2028114029.png){width="50%" align="left"}

## 第 2 课

### 目标

使用最新的核心组件创作自适应表单、配置并提交表单。

### 课程背景

在本课程中，作为企业用户，您会使用带标准化的现成核心组件的自适应Forms编辑器为多个渠道（如Web、移动和聊天）创作自适应表单以捕获数据。

### 练习

1. 为表单创建提交端点：

   1. 在新的浏览器标签页中打开 <https://requestbin.com/>。

      ![](/help/assets/screenshot2028114329.png){width="50%" align="left"}

   1. 单击&#x200B;**创建公共 bin** 并复制端点 URL。

      ![](/help/assets/screenshot202023-03-0120at206.10.0020pm.png){width="50%" align="left"}

   此特定端点用作提交和查看数据的示例。 在实际生产中，您使用自己的端点或数据源来存储捕获的数据。

1. 创作自适应表单：

   1. 在第1课中使用的浏览器选项卡中，导航到AEM Forms Web界面，然后导航到&#x200B;**Forms** > **Forms和文档**。

   1. 单击&#x200B;**创建**&#x200B;并选择“自适应表单”。

      ![](/help/assets/creating-adaptive-form-6-5.png){width="50%" align="left"}

   1. 从模板选择屏幕中选择&#x200B;**Blank with Core Components**&#x200B;模板，如下所示，然后单击&#x200B;**下一步**。

      ![](/help/assets/creating-adaptive-form-6-5-select-blank-template.png){width="50%" align="left"}

   1. 将`Contact us`指定为表单的&#x200B;**标题**。 确保表单的&#x200B;**Name**&#x200B;为`contact-us`。

      ![](/help/assets/creating-adaptive-form-65-specify-title.png){width="50%" align="left"}

   1. 单击&#x200B;**创建**。此时将显示一个对话框。

   1. 在该对话框中，单击&#x200B;**编辑**。 该表单将在自适应表单编辑器中打开。 关闭任何弹出窗口或对话框以获取首选项或信息。

   1. 打开组件浏览器，并将面板组件拖放到屏幕中间。

      ![](/help/assets/lab65-add-panel.png){width="50%" align="left"}

   1. 从组件浏览器中拖放组件以创建表单，如下所示：

      ![](/help/assets/contact-us-headless-adaptive-form.png){width="50%" align="left"}


   1. 打开“内容浏览器”，单击“指南容器”属性图标，然后打开&#x200B;**提交**&#x200B;选项卡。 选择&#x200B;**提交到REST端点**&#x200B;提交操作，选择&#x200B;**启用POST请求**&#x200B;选项，并在&#x200B;**POST请求的URL**&#x200B;文本框中指定在第2课中创建的REST端点，然后单击&#x200B;**完成**&#x200B;图标。

      ![](/help/assets/configure-submit-action.png){width="50%" align="left"}

1. Publish自适应表单：

   1. 打开AEM UI，导航到&#x200B;**Forms** > **Forms和文档**。 选择在上一步中创建的表单，然后单击&#x200B;**Publish**。

   1. 在Publish Assets对话框中，单击&#x200B;**Publish**。 这将显示成功消息。

## 第 3 课

### 目标

使用前端开发最佳实践更新样式。

### 课程背景

在本课程中，作为前端开发人员，您将学习如何轻松更新之前创建的自适应表单的样式。

### 练习

设置主题的本地存储库：

1. 使用管理员权限打开命令提示符或 shell：

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. 在命令提示符下，使用以下命令导航到`c:\git`文件夹。

   ```Shell
   cd git
   ```

   如果该文件夹不存在，请使用`md git`命令创建它。

1. 使用以下命令克隆主题前端代码：

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```

1. 按照列出的顺序使用以下命令导航到 **aem-forms-theme-canvas** 目录并打开 Visual Studio Code。

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/assets/screenshot2028126029.png){width="50%" align="left"}

1. 选择&#x200B;**信任父文件夹中所有文件的作者**，并单击&#x200B;**是的，我信任作者**。

   ![](/help/assets/screenshot2028116229.png){width="50%" align="left"}

1. 将`env_template`文件重命名为.env。  要重命名此文件，请右键单击 **env_template** 文件并选择&#x200B;**重命名**&#x200B;选项。

   ![](/help/assets/screenshot2028116429.png){width="30%" align="left"}

   </br>

   ![](/help/assets/screenshot2028116529.png){width="50%" align="left"}

1. 为 .env 文件中的变量设置以下值并保存文件：

   * **AEM_URL**：指定&#x200B;**发布**&#x200B;实例的URL。 例如，`https://localhost:4502/`

   * **AEM_ADAPTIVE_FORM**：指定表单的名称。 例如：`contact-us`。

   </br>

   ![](/help/assets/lab65-theme-environment-variable.png)


1. 在命令提示符窗口中，运行以下命令：

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028117029.png)

   >[!NOTE]
   >
   > * 如果您收到一条消息，要求您通过 `npm notice Run npm nstall -g npm@9.6.0` 命令更新 npm，请忽略此消息。
   > * 除非工作簿中指示您运行其他 npm 命令，否则不要这样做。

1. 现在，运行以下命令来预览表单。

   ```Shell
   npm run live
   ```

   ![](/help/assets/screenshot2028117229.png)

   执行上述命令后，等待 `webpack compiled` 消息。表单将显示在浏览器标签页中。

   >[!NOTE]
   >
   >如果在执行 `npm run live` 命令超过 3-4 分钟后，浏览器出现黑屏，请将浏览器 URL 中的 `localhost` 更改为 127.0.0.1，并点按 **Enter**。


   ![](/help/assets/contact-us-headless-adaptive-form-with-canvas-theme.png){width="50%" align="left"}


1. 在 Visual Studio Code 中，打开 `PROJECT\src\site\_variables.scss` 文件。请注意，`$error` 颜色是红色阴影。

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. 在浏览器中，提交表单以在&#x200B;**名字**&#x200B;字段中看到红色。

   ![](/help/assets/error-color-before.png)

1. 将 **$error** 颜色设置为 **#5736eb** 并保存文件。

1. 刷新浏览器并提交表单。请注意，“名字”字段上的错误颜色已相应地发生变化。

   ![](/help/assets/error-color-after.png)

1. 在命令提示符中，按 **Ctrl+C**，输入 **Y**，然后按 **Enter** 键以终止 npm 进程。请务必停止 npm 服务器，以避免与下一组练习发生冲突。
1. 关闭 Visual Studio Code 和命令提示符窗口。

## 第 4 课

### 目标

将表单作为 Headless 表单呈现到 Web/移动设备和其他界面。

### 课程背景

在本课程中，作为前端开发人员，您将学习如何使用反应频谱设计框架将之前创建的自适应表单渲染为Headless表单。

### 练习

使用 React 初学者项目设置本地存储库：

1. 使用管理员权限打开命令提示符。

   ![](/help/assets/screenshot2028115829.png){width="30%" align="left"}

1. 在命令提示符下，使用以下命令导航到`c:\git`文件夹。

   ```Shell
   cd git
   ```

1. 使用以下命令克隆自适应表单react启动程序项目：

   ```Shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/assets/screenshot2028117329.png)

1. 按照列出的顺序使用以下命令导航到 **react-starter-kit-aem-headless-forms** 目录并打开 Visual Studio Code。

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/assets/screenshot2028117529.png)


   这将打开 Visual Studio Code 窗口。

   ![](/help/assets/screenshot2028117429.png){width="50%" align="left"}

要呈现在发布环境中托管的表单，请执行以下操作：

1. 将 env_template 文件重命名为 .env 文件。要重命名，请右键单击 **env_template** 文件并选择&#x200B;**重命名**&#x200B;选项。

   ![](/help/assets/screenshot2028117629.png){width="30%" align="left"}

   ![](/help/assets/screenshot2028117729.png)

1. 为 .env 文件中的变量设置以下值。更新变量后，保存文件。

   * **AEM_URL**：指定发布环境的URL。 例如，`https://localhost:4503/`

   * **AEM_FORM_PATH**：指定在上一课程中创建的自适应表单的路径。 例如，`/content/forms/af/contact-us/`

   </br>

   ![](/help/assets/lab65-starter-kit-environment-variable.png)

1. 打开命令窗口，确保您位于 **react-starter-kit-aem-headless-forms** 目录中，然后运行以下命令：

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028118029.png)


1. 在命令提示符窗口中，运行以下命令：

   ```Shell
   npm start
   ```

   ![](/help/assets/lab65-starter-kit-start.png)

   上面的命令将启动一个本地开发服务器，该服务器将使用 react-spectrum 前端库以 Headless 方式呈现从 AEM 获取的表单定义。

   >[!NOTE]
   >
   > 
   > 如果在执行 `npm start` 命令超过 3-4 分钟后，浏览器出现黑屏，请将浏览器 URL 中的 `localhost` 更改为 127.0.0.1，并点按 **Enter**。

   ![](/help/assets/headless-adaptive-form-lab.png)

让我们以商业用户的身份对服务器上的表单进行更改，并自动查看 Headless 表单中反映的更改。

1. 在浏览器中打开 AEM Forms 管理界面。例如，[http://localhost:4502/aem/forms.html/content/dam/formsanddocuments](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments)。

1. 选择&#x200B;**联系我们**&#x200B;表单，然后单击&#x200B;**编辑。**&#x200B;它会在自适应Forms编辑器中打开表单。


1. 选择&#x200B;**联系电话**&#x200B;字段并单击工具栏中的&#x200B;**编辑图标（铅笔图标）**。 如果您看不到弹出工具栏，请单击右上角的&#x200B;**编辑**&#x200B;按钮（**预览**&#x200B;按钮左侧）以切换到编辑模式。

   ![](/help/assets/change-field-title.png){width="50%" align="left"}

1. 将标签更改为&#x200B;**手机号码**。 单击表单中的任意空白区域，这将保存对表单所做的更改。

让我们发布更新后的表单以将更改传播到发布环境。

1. 在AEM Forms管理界面选项卡中，选择与我们联系表单，然后单击&#x200B;**取消发布**。 如果您没有看到&#x200B;**取消发布**&#x200B;按钮，请跳至步骤 3 以直接发布更改。


1. 单击&#x200B;**取消发布**。在相应的对话框中单击&#x200B;**关闭**。

1. 浏览器刷新后，选择与我们联系表单，然后单击&#x200B;**Publish**。


1. 单击&#x200B;**发布**。在相应的对话框中，单击&#x200B;**关闭**。

1. 刷新显示了 Headless 表单的浏览器标签页。请注意，“联系电话”标签已更改为“手机号码”。

   ![](/help/assets/headless-adaptive-form.png)

1. 打开用于启动 **react-starter-kit-aem-headless-forms** 项目的命令提示符窗口，按 **Ctrl+C**，然后输入 **Y** 并按 Enter 键以终止 npm 进程。请务必停止 npm 服务器，以避免与下一组练习发生冲突。

1. 关闭 Visual Studio Code 和命令提示符窗口。


## 第 5 课

### 目标

使用 Google Material UI 将表单呈现为 Headless 表单

### 课程背景

在本课程中，作为前端开发人员，您将了解如何使用Google材料UI将之前创建的自适应表单渲染为Headless表单。

### 练习

使用 Material UI 初学者项目设置本地存储库：

1. 使用管理员权限打开命令提示符。

   ![](/help/assets/screenshot2028115829.png){width="30%" align="left"}

1. 在命令提示符下，使用以下命令导航到`c:\git`文件夹。

   ```Shell
   cd git
   ```

1. 按列出的顺序运行以下命令以创建名为 mui 的文件夹，并使用以下命令导航到 mui 文件夹：

   ```Shell
   mkdir mui
   
   cd mui
   ```

1. 使用以下命令克隆自适应表单react启动程序项目：

   ```Shell
   git clone -b mui-lab https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/assets/screenshot2028126529.png)

1. 按照列出的顺序使用以下命令导航到 **react-starter-kit-aem-headless-forms** 文件夹，并在 Visual Studio Code 中打开代码：

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/assets/screenshot2028126829.png)

要呈现在发布环境中托管的表单，请执行以下操作：

1. 将 **env_template** 文件重命名为 **.env** 文件。要重命名，请右键单击 **env_template** 文件并选择&#x200B;**重命名**。

   ![](/help/assets/screenshot2028126629.png){width="30%" align="left"}

1. 为 .env 文件中的变量设置以下值。更新变量后，保存文件。使用 **Ctrl + S** 开关组合来保存文件。

   * **AEM_URL**：指定发布环境的URL。 例如，[https://localhost:4503](https://localhost:4503)

   * **AEM_FORM_PATH**：指定在上一课程中创建的自适应表单的路径。 例如，/content/forms/af/contact-us/


1. 打开命令窗口，确保您位于 **react-starter-kit-aem-headless-forms** 目录中，然后运行以下命令：

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028127029.png)

1. 在命令提示符窗口中，运行以下命令：

   ```Shell
   npm start
   ```

   ![](/help/assets/lab65-mui-starter-kit-start.png)

   该命令将启动本地开发服务器，并使用Google材料UI前端库以Headless方式呈现从AEM获取的表单定义。

   >[!NOTE]
   >
   >如果在执行 `npm start` 命令超过 3-4 分钟后，浏览器出现黑屏，请将浏览器 URL 中的 `localhost` 更改为 127.0.0.1，并点按 **Enter**。

   ![](/help/assets/google-mui-form.png)

## 第 6 课

### 目标

使用 Material UI 组件变体创建 Headless 表单的替代外观

### 课程背景

在本课程中，作为前端开发人员，您将了解如何使用材料UI为业务用户之前创建的自适应表单创建不同组件的替代表示形式。

### 练习

更新 Headless 项目中的组件变体。要将 Material UI 文本输入组件的变体更改为 `OutlinedInput`，请执行以下操作：

1. 在 Visual Code 中，通过打开位于 `src/components/textinput/index.tsx` 的 `index.tsx` 文件来导航到文本输入组件。

1. 在代码行 104 的开头添加 `//`。它将行转换为注释。

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. 在第 105 行添加以下内容以使用不同的组件变体并保存文件。使用 **Ctrl + S** 开关组合来保存文件。

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/assets/aem65-lab-code-update.png)

   必须为“OutlinedInput”变体使用正确的大写形式，否则编译将失败。本地开发环境编译自动在命令提示符处开始。等待，直到您看到以下消息

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. 刷新浏览器（如果它未自动刷新）可以看到文本输入组件使用了其他变体。

   ![](/help/assets/screenshot2028127729.png){width="50%" align="left"}


   对于最终用户来说，无需对 AEM Forms Server 中的表单定义进行任何更改即可进行此更改，并且它特定于正在考虑的 Headless 渠道。例如，本实验室中的 Web 渠道。

   ![](/help/assets/aem65-lab-mui-style-update.png)


1. 关闭 Visual Studio Code 和命令提示符窗口。

## 常见问题解答 (FAQ)

+++ 核心组件是否可公开发布？

是，自适应Forms核心组件在AEM 6.5 Forms和Forms中作为Cloud Service提供。 您需要AEM Forms 6.5 Service Pack 16或更高版本才能使用自适应Forms核心组件。

+++

+++ Headless 表单是否需要单独的许可证？

否，Headless 表单使用相同的许可价值指标，即表单提交次数。

+++




## 后续步骤

现在您已了解如何构建自适应Forms并使用Headless表单将它们交付到多个渠道，您应该尝试将新技能付诸实践。 通过为您的最终用户大规模创建和提供卓越的数据捕获体验，享受其中的乐趣并继续前进！

## 资源

* [自适应表单核心组件简介](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html)

* [使用核心组件创建自适应表单](https://experienceleague.corp.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html)

* [更新基于核心组件的 AF 的样式](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html?lang=en)

* [Headless自适应Forms](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=en)

* [使用 Headless React 初学者套件](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form.html?lang=en)
