---
title: 在AEM 6.5 Forms上启用Headless自适应Forms
seo-title: Step-by-Step Guide for enabling Headless Adaptive Forms on AEM 6.5 Forms
description: 了解如何使用Adobe的分步指南在AEM 6.5 Forms上启用Headless自适应表单。 本教程将指导您完成该过程，以便您可以轻松将此强大功能集成到您的网站中并改善用户体验。
contentOwner: Khushwant Singh
role: Admin
exl-id: e1a5e7e0-d445-4cca-b8d7-693d9531f075
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 8%

---

# 在AEM 6.5 Forms上启用Headless自适应Forms {#enable-headless-adaptive-forms-on-aem-65-forms}

要在您的AEM 6.5 Forms环境中启用Headless自适应Forms，请设置一个基于AEM Archetype 41或更高版本的项目，并将其部署到您的所有创作和发布实例。

通过将基于AEM Archetype 41或更高版本的项目部署到AEM 6.5 Forms实例，您可以[创建基于核心组件的自适应Forms](create-a-headless-adaptive-form.md)。 这些表单以JSON格式表示，用作`Headful`和`Headless`自适应Forms，从而允许在各种渠道（包括移动应用程序、Web和本机应用程序）中提供更大的灵活性和自定义设置。

## 先决条件 {#prerequisites}

在AEM 6.5 Forms环境中启用Headless自适应Forms之前，

* [升级到AEM 6.5 Forms Service Pack 16 (6.5.16.0)或更高版本](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-65/content/release-notes/aem-forms-current-service-pack-installation-instructions)。

* 安装[Apache Maven](https://maven.apache.org/download.cgi)的最新版本。

* 安装纯文本编辑器。 例如，Microsoft Visual Studio Code。

## 创建和部署最新的基于AEM原型的项目

要创建基于AEM Archetype 41或[稍后](https://github.com/adobe/aem-project-archetype)的项目并将其部署到所有创作实例和发布实例，请执行以下操作：

1. 以管理员身份登录到您的计算机，托管并运行AEM 6.5 Forms实例。
1. 打开命令提示符或终端。
1. 运行以下命令可创建基于AEM Archetype 41的项目：

   * Microsoft Windows

   ```Shell
      mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate ^
      -D archetypeGroupId=com.adobe.aem ^
      -D archetypeArtifactId=aem-project-archetype ^
      -D archetypeVersion=41 ^
      -D appTitle="My Form" ^
      -D appId="myform" ^
      -D groupId="com.myform" ^
      -D includeFormsenrollment="y" ^
      -D aemVersion="6.5.23" 
   ```

   * Linux®或Apple macOS

   ```Shell
      mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate \
      -D archetypeGroupId=com.adobe.aem \
      -D archetypeArtifactId=aem-project-archetype \
      -D archetypeVersion=41 \
      -D appTitle="My Form" \
      -D appId="myform" \
      -D groupId="com.myform" \
      -D includeFormsenrollment="y" \
      -D aemVersion="6.5.23" 
   ```

   执行上述命令时，请务必考虑以下事项：

   * 更新命令以反映环境的特定值，包括appTitle、appId和groupId。 此外，将includeFormsenrollment的值设置为`y`。 如果您使用Forms Portal，请设置&#x200B;_includeExamples=y_&#x200B;选项以将Forms Portal核心组件包含在您的项目中。


1. （仅适用于基于Archetype版本41的项目）创建AEM Archetype项目后，请为基于核心组件的自适应Forms启用主题。 要启用主题，请执行以下操作：

   1. 打开[AEM原型项目文件夹]/ui.apps/src/main/content/jcr_root/apps/__appId__/components/adaptiveForm/page/customheaderlibs.html以进行编辑：

   1. 在第21行添加以下代码：

      ```XML
      <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html"
      data-sly-use.formstructparser="com.adobe.cq.forms.core.components.models.form.FormStructureParser"
      data-sly-test.themeClientLibRef="${formstructparser.themeClientLibRefFromFormContainer}">
      <sly data-sly-test="${themeClientLibRef}" data-sly-call="${clientlib.css @ categories=themeClientLibRef}"/>
      </sly>
      ```

      ![在第21](/help/assets/code-to-enable-themes.png)行添加上述代码

   1. 保存并关闭该文件。

1. 更新项目以包含最新版本的Forms核心组件：

   1. 打开[AEM原型项目文件夹]/pom.xml进行编辑。
   1. 将`core.forms.components.version`和`core.forms.components.af.version`的版本设置为[最新的Forms核心组件](https://github.com/adobe/aem-core-forms-components/tree/release/650)版本。

   1. 保存并关闭该文件。


1. 成功创建AEM原型项目后，为您的环境构建部署包。 要构建包，请执行以下操作：

   1. 导航到AEM原型项目的根目录。


   1. 运行以下命令为您的环境构建AEM原型项目：

      ```Shell
      mvn clean install
      ```

      ![archetypebuild-success](assets/corecomponent-build-successful.png)


   成功构建AEM原型项目后，将生成一个AEM包。 您可以在[AEM原型项目文件夹]\all\target\[appid].all-[version].zip中找到该包

1. 使用[包管理器](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-65/content/sites/administering/contentmanagement/package-manager)在所有创作实例和发布实例上部署[AEM原型项目文件夹]\all\target\[appid].all-[version].zip包。

>[!NOTE]
>
>
>
>如果在通过包管理器访问发布实例的登录对话框时遇到困难，请尝试通过以下URL登录： `http://[Publish Server URL]`：[PORT]/system/console。 通过此过程可登录“发布”实例，并允许您继续安装过程。


为您的环境启用了核心组件。 将基于空核心组件的自适应表单模板和画布3.0主题部署到您的环境，使您能够[创建基于核心组件的自适应Forms](create-a-headless-adaptive-form.md)。

## 常见问题解答

### 核心组件包括哪些？

[核心组件](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-core-components/using/introduction)是一组适用于AEM的标准化Web内容管理(WCM)组件，可加快开发速度并降低网站的维护成本。

### 在启用核心组件上添加了哪些功能？


为您的环境启用自适应表单核心组件时，将有一个空白的基于核心组件的自适应表单模板和 Canvas 3.0 主题添加到您的环境。为您的环境启用自适应表单核心组件后，您可以：

* 创建基于核心组件的自适应Forms。
* 创建基于核心组件的自适应表单模板。
* 为基于核心组件的自适应表单模板创建自定义主题。
* 向需要表单Headless表示的渠道（如移动设备、Web、本机应用程序和服务）提供基于核心组件的自适应表单的JSON表示。
