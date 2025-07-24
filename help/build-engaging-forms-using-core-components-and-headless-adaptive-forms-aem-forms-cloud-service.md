---
title: 使用核心组件和 Headless 构建具有吸引力的表单
seo-title: Build Engaging Forms Using Core Components and Headless
description: 使用核心组件和 Headless 构建具有吸引力的表单
seo-description: Build Engaging Forms Using Core Components and Headless
topic-tags: develop
exl-id: ef99ffe9-4a37-4f0a-a4d3-78976c92220f
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '2452'
ht-degree: 56%

---

# 在AEM Forms as a Cloud Service上使用核心组件和Headless自适应Forms构建引人入胜的Forms {#build-engaging-forms-using-core-components-and-headless}

<!-- This article is completely missing the image ALT tags (descriptions) for each added image asset. That is impacting the CQI score for Experience Manager in a negative way. Be sure you add the required missing image ALT tags.  -->

## 实验室概述 {#lab-overview}

在本实践实验中，您将学习以下内容：

如何使用AEM Forms通过最新核心组件轻松创建自适应表单。 这些组件与AEM Sites一致，通过将自适应表单作为Headless表单提供给Web、移动和聊天，支持全渠道数据捕获体验。 您还将了解有关样式化、自定义项和前端开发的最佳实践。

## 要点 {#key-takeaways}

* **业务敏捷性**：作为商业用户，我可以轻松地为多个渠道创作表单体验。

* **前端开发人员的力量**：作为前端开发人员，我可以使用 Headless 表单来控制最终用户体验。

* **开发人员速度**：作为开发人员，我可以轻松且一致地自定义 Sites 和 Forms 组件。

## 前提条件 {#prerequisites}

要使用此动手实验，请执行以下操作：

* 安装[最新版本的Git](https://git-scm.com/downloads)。 如果您是初次使用Git，请参阅[安装Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)。

* 安装[Node.js 16.13.0或更高版本](https://nodejs.org/en/download/)。 如果您是初次使用Node.js，请参阅[如何安装Node.js](https://nodejs.org/en/learn/getting-started/how-to-install-nodejs)。

* [为您的Forms as a Cloud Service环境启用自适应AEM Forms核心组件](enable-headless-adaptive-forms-and-core-components-on-forms-cloud-service.md)。

* 安装[Microsoft Visual Studio Code](https://code.visualstudio.com/download)或任何纯文本编辑器。 本文档中的示例使用了Microsoft Visual Studio Code。



## 第 1 课 {#lesson-1}

### 目标 {#lesson-1-objectives}

自行熟悉 AEM Forms as a Cloud Service 环境。

### 课程背景 {#lesson-1-context}

在本课中，您将通过导航用户界面来自行熟悉 AEM Forms as a Cloud Service 环境。

### 练习 {#lesson-1-excercise}

1. 打开浏览器，并输入Cloud Service创作环境的URL。<!-- URL is 404! EXPLAIN THE URL IS FOR ILLUSTRATION PURPOSES ONLY? For example: [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/start.html](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/start.html) -->

1. 登录到Cloud Service创作环境。
   ![](/help/assets/screenshot2028113829.png){width="50%" align="left"}

1. 要导航到AEM Forms UI，请单击&#x200B;**Forms > Forms和文档**。



   ![](/help/assets/screenshot2028113929.png){width="50%" align="left"}

   关闭任何与首选项或信息相关的弹出窗口。 将显示所有可用的表单。


## 第 2 课

### 目标

使用最新的核心组件创作自适应表单，然后配置并提交表单。

### 课程背景

在本课中，作为商业用户，您将使用自适应表单创作功能和用于数据捕获的标准化 OOTB 核心组件，为 Web、移动设备和聊天等多个渠道创作自适应表单。

### 练习

1. 为表单创建提交端点：

   1. 在新的浏览器标签页中打开 <https://pipedream.com/requestbin>。
   1. 单击&#x200B;**创建公共 bin** 并复制端点 URL。

      ![](/help/assets/screenshot2028114329.png){width="50%" align="left"}

      ![](/help/assets/screenshot202023-03-0120at206.10.0020pm.png){width="50%" align="left"}

1. 使用“向导”界面创作自适应表单：

   1. 在第 1 课中使用的浏览器标签页中，导航至 AEM Forms as Cloud Service Web 界面，然后导航至“表单和文档”。

      ![](/help/assets/screenshot2028114029.png)

   1. 单击&#x200B;**创建** > **自适应表单**。

      ![](/help/assets/screenshot2028114629.png)

   1. 从模板选择屏幕中选择&#x200B;**空白（核心组件）**&#x200B;模板，如下所示：

      ![](/help/assets/screenshot202023-03-0120at206.09.1520pm.png)

   1. 单击&#x200B;**样式**&#x200B;选项卡，选择 **wknd-theme** 主题，如下所示：

      ![](/help/assets/screenshot202023-03-0120at206.09.2320pm.png)

   1. 单击&#x200B;**提交**&#x200B;选项卡，选择&#x200B;**提交到REST端点**&#x200B;卡并在&#x200B;**URL中指定POST请求**&#x200B;字段的公共bin，如下所示：

      ![](/help/assets/screenshot202023-03-0120at206.09.5320pm.png)

   1. 单击&#x200B;**创建**。在表单上指定名称和标题。 例如，**注册**。 单击&#x200B;**创建**。

   1. 这将打开自适应表单编辑器。关闭偏好设置或信息的任何弹出窗口或对话框。单击左边栏上的组件浏览器，并将&#x200B;**页眉**&#x200B;和&#x200B;**页脚**&#x200B;组件分别添加到空白表单的顶部和底部。

      ![](/help/assets/screenshot2028121929.png)

   1. 从组件浏览器中拖放组件以创建表单，如下所示：

      ![](/help/assets/screenshot2028115129.png){width="50%" align="left"}

1. 将验证添加到表单：

   1. 单击&#x200B;**电话号码**&#x200B;组件，以便显示弹出菜单。单击菜单中的&#x200B;**“扳手”图标**&#x200B;以配置字段。

   1. 打开&#x200B;**验证选项卡**，将字段标记为&#x200B;**必填**，然后单击&#x200B;**完成**。这将显示成功消息。

      ![](/help/assets/screenshot2028123529.png){width="50%" align="left"}

      ![](/help/assets/screenshot2028123629.png){width="50%" align="left"}

1. 预览并提交表单。

   1. 单击&#x200B;**预览**&#x200B;以从最终用户的角度预览表单。

   1. 用虚拟数据填写表单。

   1. 提交表单。

      ![](/help/assets/screenshot2028125729.png)

   1. 在“请求 bin”选项卡中，检查提交的数据。

      ![](/help/assets/screenshot2028125829.png)

1. 使用规则将交互性添加到表单：

   1. 单击&#x200B;**选中此框可接收5%折扣**&#x200B;组件。 在选项工具栏上，单击规则图标。 这将打开规则编辑器选项。

   1. 创建一个规则，如果选中&#x200B;**选中接收5%折扣**&#x200B;选项的复选框，则用于应用信用卡的选项将被禁用。

1. 发布表单。

   1. 打开AEM Forms管理界面，例如`https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments`，然后选择表单。

   1. 单击&#x200B;**发布**。

      ![](/help/assets/screenshot2028115629.png)

      这将显示成功消息。

      ![](/help/assets/screenshot2028115729.png)

      表单的已发布URL将类似于`https://publish-p105303-e986623.adobeaemcloud.com/content/forms/af/registration.html`。

   1. 要查看已发布的表单，请将上述URL中的项目ID (pXXXXXX)和环境ID (eXXXXXX)替换为
环境。

## 第 3 课

### 目标

使用前端开发最佳实践更新样式。

### 课程背景

在本课中，作为前端开发人员，您将了解如何轻松地更新先前创建的自适应表单的样式。

### 练习

设置主题的本地存储库：

1. 使用管理员权限打开命令提示符或 shell：

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. 在命令提示符下，使用以下命令导航到 **c:\git** 文件夹

   ```Shell
   cd c:\git
   ```

1. 使用以下命令克隆主题前端代码：

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```


1. 按照列出的顺序使用以下命令导航到 **aem-forms-theme-canvas** 目录并打开 Visual Studio Code。

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/assets/screenshot2028126029.png)

1. 选择&#x200B;**信任父文件夹中所有文件的作者**，并单击&#x200B;**是的，我信任作者**。

   ![](/help/assets/screenshot2028116229.png){width="50%" align="left"}

1. 要呈现在云服务发布环境中托管的表单，请重命名 `env_template` 文件。要重命名此文件，请右键单击 **env_template** 文件并选择&#x200B;**重命名**&#x200B;选项。

   ![](/help/assets/screenshot2028116429.png){width="50%" align="left"}

   </br>

   ![](/help/assets/screenshot2028116529.png){width="50%" align="left"}

1. 为.env文件中的变量设置以下值并保存文件：

   * **AEM_URL**：指定您的云服务发布环境。例如，`https://publish-p105303-e986623.adobeaemcloud.com/`

   * **AEM_ADAPTIVE_FORM**：指定表单的路径。例如，如果表单路径为 `/content/forms/af/registration`，则此变量的值将为 `registration`。

     ![](/help/assets/screenshot2028116429.png){width="50%" align="left"}

1. 在AEM环境中创建本地用户。

   >[!NOTE]
   > 要创建本地用户，请转到`AEM Home` > `Tools` > `Security` > `Users`。
   > 确保用户是forms-users组的成员。


1. 在命令提示符窗口中，运行以下命令：

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028117029.png)

   >[!NOTE]
   >
   > * 如果收到要求通过`npm`命令更新`npm notice Run npm nstall -g npm@9.6.0`的消息，请忽略该消息。
   > * 除非在工作簿中向您发出指示，否则不要运行其他`npm`命令。

1. 现在，运行以下命令预览表单。

   ```Shell
   npm run live
   ```

   ![](/help/assets/screenshot2028117229.png)

   执行上述命令后，请等待`webpack compiled`消息，您将被重定向到AEM登录页面。

1. 在AEM登录页面上单击&#x200B;**本地登录（仅管理任务）**。
1. 输入已创建本地用户的凭据，表单将显示在浏览器选项卡中。

   >[!NOTE]
   >
   >如果执行`npm run live`命令超过3-4分钟后浏览器出现空白屏幕，请将浏览器URL中的`localhost`更改为127.0.0.1并按&#x200B;**Enter**。


   ![](/help/assets/screenshot2028115129.png){width="50%" align="left"}


1. 在 Visual Studio Code 中，打开 `PROJECT\src\site\_variables.scss` 文件。请注意，`$error` 颜色是红色阴影。

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. 在浏览器中，提交表单以在&#x200B;**名字**&#x200B;字段中看到红色。

   ![](/help/assets/screenshot2028120829.png)

1. 将 **$error** 颜色设置为 **#5736eb** 并保存文件。

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. 刷新浏览器并提交表单。请注意，名字字段上的错误颜色已相应更改。

   ![](/help/assets/screenshot2028121129.png)

1. 在命令提示符下，按&#x200B;**CTRL+C**，输入&#x200B;**Y**，然后按&#x200B;**Enter**&#x200B;键终止npm进程。 请务必停止 npm 服务器，以避免与下一组练习发生冲突。
1. 关闭 Visual Studio Code 和命令提示符窗口。

## 第 4 课

### 目标

将表单渲染为Headless表单以供Web/移动和其他界面使用。

### 课程背景

在本课程中，作为前端开发人员，您将学习如何使用React频谱设计框架将之前创建的自适应表单渲染为Headless表单。

### 练习

使用React入门项目设置本地存储库：

1. 使用管理员权限打开命令提示符。

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. 在命令提示符下，使用以下命令导航到 **c:\git** 文件夹

   ```Shell
   cd c:\git
   ```

1. 使用以下命令克隆自适应表单React启动程序项目：

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

要呈现在云服务发布环境中托管的表单，请执行以下操作：

1. 将env_template文件重命名为.env文件。 要重命名，请右键单击 **env_template** 文件并选择&#x200B;**重命名**&#x200B;选项。

   ![](/help/assets/screenshot2028117629.png){width="50%" align="left"}

   ![](/help/assets/screenshot2028117729.png)

1. 为 .env 文件中的变量设置以下值。更新变量后，保存文件。
   * **AEM_URL**：指定云服务发布环境的 URL。例如，`https://publish-p105303-e986623.adobeaemcloud.com`

   * **AEM_FORM_PATH**：指定上一节课中创建的自适应表单的路径。例如，`/content/forms/af/registration/`

     ![](/help/assets/screenshot202023-03-0820at202.49.1820pm.png)

1. 打开命令窗口，确保您位于 **react-starter-kit-aem-headless-forms** 目录中，然后运行以下命令：

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028118029.png)


1. 在命令提示符窗口中，运行以下命令：

   ```Shell
   npm start
   ```

   ![](/help/assets/screenshot2028118129.png)

   上述命令将启动本地开发服务器，该服务器将使用React光谱前端库以Headless方式呈现从AEM中获取的表单定义。

   >[!NOTE]
   >
   > 
   > 如果执行`npm start`命令超过3-4分钟后浏览器出现空白屏幕，请将浏览器URL中的`localhost`更改为127.0.0.1并按&#x200B;**Enter**。

   ![](/help/assets/screenshot2028118229.png)

让我们检查此Headless表单中规则的执行：

1. 选择&#x200B;**选中框以接收 5% 的折扣**&#x200B;选项。用于申请信用卡的后续选项被禁用。

   ![](/help/assets/screenshot2028126229.png)

1. 取消选择&#x200B;**选中框以接收 5% 的折扣**，启用信用卡选项。

   ![](/help/assets/screenshot2028126329.png)

让我们以商业用户的身份对服务器上的表单进行更改，并自动查看 Headless 表单中反映的更改。

1. 在浏览器中打开AEM Forms管理界面。<!-- URL is 404. Consider saying the path is for illlustration purposes only. For example, [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/forms.html/content/dam/formsanddocuments](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments). -->

1. 选择&#x200B;**`contactus`**&#x200B;表单，然后单击&#x200B;**编辑。**&#x200B;这将在自适应表单编辑器中打开表单。


1. 选择&#x200B;**电话号码**&#x200B;字段并单击工具栏中的&#x200B;**编辑图标（铅笔图标）**。如果看不到弹出式工具栏，请切换到编辑模式。 单击右上角的&#x200B;**编辑**&#x200B;按钮，左至&#x200B;**预览**&#x200B;按钮。

   ![](/help/assets/screenshot2028119629.png)

1. 将标签更改为手机号码。单击表单中的任意空白区域，这将保存对表单所做的更改。

   ![](/help/assets/screenshot2028119729.png)

让我们发布更新后的表单以将更改传播到已发布的环境。

1. 在 AEM Forms 管理界面选项卡中，选择注册表单，然后单击&#x200B;**取消发布**。如果您没有看到&#x200B;**取消发布**&#x200B;按钮，请跳至步骤 3 以直接发布更改。

1. 单击&#x200B;**取消发布**。在相应的对话框中，单击&#x200B;**关闭**。

1. 在浏览器刷新后，选择注册表单，然后单击&#x200B;**发布**。

1. 单击&#x200B;**发布**。在相应的对话框中，单击&#x200B;**关闭**。

1. 刷新显示了 Headless 表单的浏览器标签页。请注意，“电话号码”标签已更改为“手机号码”。

   ![](/help/assets/screenshot2028120529.png)

1. 打开用于启动 **react-starter-kit-aem-headless-forms** 项目的命令提示符窗口，按 **Ctrl+C**，然后输入 **Y** 并按 Enter 键以终止 npm 进程。请务必停止 npm 服务器，以避免与下一组练习发生冲突。

1. 关闭 Visual Studio Code 和命令提示符窗口。


## 第 5 课

### 目标

使用 Google Material UI 将表单呈现为 Headless 表单

### 课程背景

在本课中，作为前端开发人员，您将了解如何使用 Google Material UI 将之前创建的自适应表单呈现为 Headless 表单。

### 练习

使用材料UI入门项目设置本地存储库：

1. 使用管理员权限打开命令提示符。

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}


1. 在命令提示符下，使用以下命令导航到 **c:\git** 文件夹：

   ```Shell
   cd c:\git
   ```

1. 按列出的顺序运行以下命令以创建名为`mui`的文件夹，并使用以下命令导航到`mui`文件夹：

   ```Shell
   mkdir mui
   
   cd mui
   ```

1. 使用以下命令克隆自适应表单React启动程序项目：

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

要呈现在云服务发布环境中托管的表单，请执行以下操作：

1. 将&#x200B;**env_template**&#x200B;文件重命名为&#x200B;**.env**&#x200B;文件。 要重命名，请右键单击 **env_template** 文件并选择&#x200B;**重命名**。

   ![](/help/assets/screenshot2028126629.png){width="50%" align="left"}

1. 为 .env 文件中的变量设置以下值。更新变量后，保存文件。 使用 **Ctrl + S** 开关组合来保存文件。

   * **AEM_URL**：指定云服务发布环境的 URL。例如，[https://publish-p105303-e986623.adobeaemcloud.com](https://publish-p105303-e986623.adobeaemcloud.com/)

   * **AEM_FORM_PATH**：指定上一节课中创建的自适应表单的路径。例如，/content/forms/af/registration/

     ![](/help/assets/screenshot2028126929.png)

1. 打开命令窗口，确保您位于 **react-starter-kit-aem-headless-forms** 目录中，然后运行以下命令：

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028127029.png)

1. 在命令提示符窗口中，运行以下命令：

   ```Shell
   npm start
   ```

   ![](/help/assets/screenshot2028127129.png)

   该命令将启动一个本地开发服务器，并使用 Google Material UI 前端库以 Headless 方式呈现从 AEM 获取的表单定义。

   >[!NOTE]
   >
   >如果执行`npm start`命令超过3-4分钟后浏览器出现空白屏幕，请将浏览器URL中的`localhost`更改为127.0.0.1并按&#x200B;**Enter**。

   ![](/help/assets/screenshot2028127229.png)

1. 要评估同一业务逻辑在此表单演绎版中的执行情况，请执行以下操作：

   选择&#x200B;**选中框以接收 5% 的折扣**。后续选项&#x200B;**是否要申请`We.Finance`公司信用卡表单？**&#x200B;已被禁用。

   ![](/help/assets/screenshot2028127329.png){width="50%" align="left"}

## 第 6 课

### 目标

使用 Material UI 组件变体创建 Headless 表单的替代外观

### 课程背景

在本课程中，作为前端开发人员，您将学习如何创建不同组件的替代表示形式。 您可为业务用户之前创建的自适应表单使用材质UI。

### 练习

更新 Headless 项目中的组件变体。要将 Material UI 文本输入组件的变体更改为 `OutlinedInput`，请执行以下操作：

1. 在 Visual Code 中，通过打开位于 `src/components/textinput/index.tsx` 的 `index.tsx` 文件来导航到文本输入组件。

1. 在代码行 103 的开头添加 `//`。它将行转换为注释。

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. 在第104行添加以下内容以使用组件的其他变体并保存文件。 使用 **Ctrl + S** 开关组合来保存文件。

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/assets/screenshot2028127629.png)

   必须对“OverridedInput”变量使用正确的大小写，否则编译将失败。 本地开发环境编译自动在命令提示符处开始。等待，直到您看到以下消息

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. 如果浏览器未自动刷新，请刷新浏览器，以查看文本输入组件使用不同的变体。

   ![](/help/assets/screenshot2028127729.png)


   对于最终用户来说，无需对 AEM Forms Server 中的表单定义进行任何更改即可进行此更改，并且它特定于正在考虑的 Headless 渠道。例如，本实验中的Web渠道。

   ![](/help/assets/screenshot2028127529.png){width="50%" align="left"}


1. 关闭 Visual Studio Code 和命令提示符窗口。

## 常见问题解答 (FAQ)

+++ 自适应表单向导是否可公开使用？

是，它适用于AEM Forms as Cloud Service。

+++


+++ 核心组件是否公开可用？

是的，自适应表单核心组件与 AEM Forms as Cloud Service 一起提供。

+++

+++ Headless 表单是否公开可用？

是的，Headless 表单与 AEM Forms as Cloud Service 一起提供。

+++

+++ Headless 表单是否需要单独的许可证？

否，Headless 表单使用相同的许可价值指标，即表单提交次数。

+++

+++ AEM 6.5 Forms是否提供核心组件和Headless表单？

是的，AEM Forms 6.5 Service Pack 16 及更高版本都提供自适应表单核心组件和 Headless 表单。

+++


## 后续步骤

现在，您已了解如何构建自适应表单，并使用Headless表单跨渠道交付这些表单。 无论您的用户身在何处，都可使用这些技能来创建可扩展的高质量数据捕获体验。


## 资源

* [自适应表单核心组件简介](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-core-components/using/adaptive-forms/introduction)

* [使用核心组件创建自适应表单](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components)

* [更新基于核心组件的 AF 的样式](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components)

* [Headless 自适应表单](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-headless-adaptive-forms/using/overview)

* [使用Headless React入门工具包](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form)
