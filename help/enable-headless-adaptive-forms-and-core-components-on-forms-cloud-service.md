---
title: 在AEM Formsas a Cloud Service上启用Headless自适应Forms
seo-title: Step-by-Step Guide for enabling Headless Adaptive Forms on AEM Forms as a Cloud Service
description: 了解如何使用我们的分步指南在AEM Forms上启用Headless自适应表单as a Cloud Service。 我们的教程将引导您完成整个过程，使您可以轻松地为您的 AEM Forms 环境启用这一强大的功能。
seo-description: Learn how to enable headless adaptive forms on AEM Forms as a Cloud Service with our step-by-step guide. Our tutorial walks you through the process, making it easy to enable this powerful feature for your AEM Forms environment.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin
level: Beginner, Intermediate
contentOwner: Khushwant Singh
docset: CloudService
hide: true
hidefromtoc: true
exl-id: 7afff771-1296-4162-84c5-c8266b94af2f
source-git-commit: 999c3d092d03d7a82363bc94ce79ceb33bf0df7e
workflow-type: tm+mt
source-wordcount: '914'
ht-degree: 64%

---

# 在AEM Formsas a Cloud Service上启用Headless自适应Forms {#enable-headless-adaptive-forms-on-aem-forms-cloud-service}

在AEM Formsas a Cloud Service上启用Headless自适应Forms，允许您开始创建、发布和使用您的AEM FormsCloud Service实例向多个渠道交付Headless Forms。 您需要具备启用了自适应表单核心组件的环境才能使用 Headless 自适应表单。

## 注意事项

* 当您创建新的AEM Formsas a Cloud Service程序时，[已为您的环境启用Headless自适应Forms](#are-adaptive-forms-core-components-enabled-for-my-environment)。

* 如果您拥有的是其中[未启用](#enable-components)核心组件的旧版 Forms as a Cloud Service 程序，则您可[将自适应表单核心组件依赖项添加到](#enable-headless-adaptive-forms-for-an-aem-forms-as-a-cloud-service-environment)您的 AEM as a Cloud Service 存储库，并将该存储库部署到您的 Cloud Service 环境以启用 Headless 自适应表单。

* 如果您的现有Cloud Service环境提供了[创建基于核心组件的自适应Forms](create-a-headless-adaptive-form.md)的选项，则已为您的环境启用Headless自适应Forms，您可以将基于核心组件的自适应Forms作为Headless表单提供给需要Headless表示自适应Forms的移动、Web、本机应用程序和服务等渠道。


>[!NOTE]
>
>
> Adobe提供了自适应Forms [简易工具包（React应用程序）](create-and-publish-a-headless-form.md)，以帮助开发人员快速开始进行Headless自适应Forms开发，而无需在AEM Formsas a Cloud Service环境中启用Headless自适应Forms。 稍后在快速动手开发Headless表单后，您可以在Formsas a Cloud Service环境中启用Headless自适应Forms](create-and-publish-a-headless-form.md)。[

## 为AEM Formsas a Cloud Service环境启用Headless自适应Forms

按照列出的顺序，执行以下步骤，为AEM Formsas a Cloud Service环境启用Headless自适应Forms


![](/help/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service.png)


## 1. 克隆您的 AEM Forms as a Cloud Service Git 存储库 {#clone-git-repository}

1. 登录到 [Cloud Manager](https://my.cloudmanager.adobe.com/) 并选择您的组织和计划。

1. 从您的&#x200B;**程序概述**&#x200B;页面导航到&#x200B;**管道**&#x200B;卡片，单击&#x200B;**访问存储库信息**&#x200B;按钮以访问和管理您的 Git 存储库。该页面包括以下信息：

   * Cloud Manager Git 存储库的 URL。
   * Git 存储库的凭据（用户名和密码）Git 用户名。

   单击&#x200B;**生成密码**&#x200B;以查看或生成密码。

1. 在本地计算机上打开终端或命令提示符并运行以下命令：

   ```Shell
   git clone [Git Repository URL]
   ```

   出现提示时，提供凭据。随后将该存储库克隆到您的本地计算机。


## 2. 将自适应表单核心组件依赖项添加到您的 Git 存储库 {#add-adaptive-forms-core-components-dependencies}

1. 在纯文本代码编辑器中打开您的 Git 存储库文件夹。例如 VS Code。
1. 打开 `[AEM Repository Folder]\pom.xml` 文件以供编辑。
1. 将 `core.forms.components.version`、`core.forms.components.af.version` 和 `core.wcm.components.version` 组件的版本替换为[核心组件文档](https://github.com/adobe/aem-core-forms-components)中指定的版本。如果不存在，请添加这些组件。

   ```XML
   <!-- Replace the version with the latest released version at https://github.com/adobe/aem-core-forms-components/tags -->
   
   <properties>
       <core.forms.components.version>2.0.14</core.formscomponents.version>
       <core.forms.components.af.version>2.0.14</core.forms.components.af.version>  
       <core.wcm.components.version>2.21.2</core.wcmcomponents.version>
   </properties>
   ```

   ![提及最新版本的 Forms 核心组件](/help/assets/latest-forms-component-version.png)

1. 在 `[AEM Repository Folder]\pom.xml` 文件的依赖项部分中添加以下依赖项，然后保存该文件。

   ```XML
       <!-- WCM Core Component Examples Dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <version>${core.wcm.components.version}</version>
               <type>zip</type>
           </dependency>    
           <!-- End of WCM Core Component Examples Dependencies -->
           <!-- Forms Core Component Dependencies -->
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-core</artifactId>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-apps</artifactId>
               <version>${core.forms.components.version}</version>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-core</artifactId>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-apps</artifactId>
               <version>${core.forms.components.version}</version>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-apps</artifactId>
               <type>zip</type>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-content</artifactId>
               <type>zip</type>
               <version>${core.forms.components.version}</version>
           </dependency>
   <!-- End of AEM Forms Core Component Dependencies -->
   ```

1. 打开 `[AEM Repository Folder]/all/pom.xml` 文件以供编辑。在 `<embeddeds>` 部分中添加以下依赖项，然后保存该文件。

   ```XML
   <!-- WCM Core Component Examples Dependencies -->
   
   <!-- inside plugin config of filevault-package-maven-plugin -->  
   <!-- embed wcm core components examples artifacts -->
   
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.config</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <!-- embed forms core components artifacts -->
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   ```

   >[!NOTE]
   >
   >
   >  将 `${appId}` 替换为您的 appId。
   >
   >  要查找您的 `${appId}`，请在 `[AEM Repository Folder]/all/pom.xml` 文件中搜索 `-packages/application/install` 一词。在 `-packages/application/install` 一词之前的文本就是您的 `${appId}`。例如，下列代码 `myheadlessform` 是 `${appId}`。
   >
   >   ```
   >             <embedded>
   >                     <groupId>com.myheadlessform</groupId>
   >                     <artifactId>myheadlessform.ui.apps<artifactId>
   >                     <type>zip</type>
   >                   <target>/apps/myheadlessform-packages/application install</target>
   >             </embedded>
   >   ```

1. 在 `[AEM Repository Folder]/all/pom.xml` 文件的 `<dependencies>` 部分中添加以下依赖项，然后保存该文件：

   ```XML
           <!-- Other existing dependencies -->
           <!-- wcm core components examples dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <type>zip</type>
               </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
           </dependency>
               <!-- forms core components dependencies -->
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-apps</artifactId>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-apps</artifactId>
               <type>zip</type>
           </dependency>
               <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-content</artifactId>
               <type>zip</type>
           </dependency>
   ```

1. 打开 `[AEM Repository Folder]/ui.apps/pom.xml` 以供编辑。添加 `af-core bundle` 依赖项，然后保存该文件。

   ```XML
       <dependency>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       </dependency>
   ```

   >[!NOTE]
   >
   >确保您的项目中不包含以下自适应表单核心组件工件。
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-apps</artifactId>`
   >
   > `</dependency>`
   >
   > 和
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-core</artifactId>`
   >
   > `</dependency>`


1. 保存并关闭该文件。

## 3.更新项目以包含最新版本的Forms核心组件：

1. 打开[AEM原型项目文件夹]/pom.xml进行编辑。


1. 保存并关闭该文件。

## 4.将更新提交到Git存储库并运行管道以部署存储库 {#Commit-the-updates-to-your-git-repository}

1. 将代码提交到Git存储库：
   1. 打开终端或命令提示符。
   1. 导航到您的 `[AEM Repository Folder]`，并按列出的顺序运行以下命令

      ```Shell
      git add pom.xml
      git add all/pom.xml
      git add ui.apps/pom.xml
      git commit -m "Added dependencies for Adaptive Forms Core Components"
      git push origin
      ```

1. 将文件提交到 Git 存储库后，[运行管道](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html)。

   成功运行管道后，即为相应的环境启用自适应表单核心组件。此外，还将自适应表单（核心组件）模板和 Canvas 3.0 主题添加到您的 Forms as a Cloud Service 环境，并为您提供自定义和创建基于核心组件的自适应表单的选项。


## 常见问题解答 {#faq}

### 什么是核心组件？ {#core-components}

[核心组件](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)是一组用于 AEM 的标准化 Web 内容管理 (WCM) 组件，以缩短您网站的开发时间并降低维护成本。

### 启用核心组件时将添加哪些功能？ {#core-components-capabilities}

为您的环境启用自适应表单核心组件时，将有一个空白的基于核心组件的自适应表单模板和 Canvas 3.0 主题添加到您的环境。为您的环境启用自适应表单核心组件后，您可以：

* 创建基于核心组件的自适应Forms。
* 创建基于核心组件的自适应表单模板。
* 为基于核心组件的自适应表单模板创建自定义主题。
* 向需要表单Headless表示的渠道（如移动设备、Web、本机应用程序和服务）提供基于核心组件的自适应表单的JSON表示。

### 我的环境是否启用了自适应表单核心组件？ {#enable-components}

要查看是否为您的环境启用了自适应表单核心组件，请执行以下操作：

1. [克隆您的 AEM Forms as a Cloud Service 存储库](#1-clone-your-aem-forms-as-a-cloud-service-git-repository)。

1. 打开您的 AEM Forms Cloud Service Git 存储库的 `[AEM Repository Folder]/all/pom.xml` 文件。

1. 搜索以下依赖项：

   * core-forms-components-af-core
   * core-forms-components-core
   * core-forms-components-apps
   * core-forms-components-af-apps
   * core-forms-components-examples-apps
   * core-forms-components-examples-content


   ![找到 all/pom.xml 中的 core-forms-components-af-core 工件](/help/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service-locate-core-af-artifact.png)

   如果存在依赖项，则为您的环境启用了自适应表单核心组件。
