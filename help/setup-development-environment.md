---
title: 为AEM Headless自适应表单设置开发环境
description: 为AEM Headless自适应表单设置开发环境
hide: true
exl-id: fd92f057-1217-42f8-a454-1bc7e3827e01
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 2%

---


# 设置本地开发环境 {#headless-adaptive-forms-setup-development-environment}

您可以设置本地开发环境，在本地计算机上创建和测试Headless自适应表单。 开发环境包括安装在AEM SDK上的AEM SDK和AEM Forms功能存档。
<!--
 After a Headless adaptive form or related assets are ready on the local development environment, you can deploy the Headless adaptive form application to your publishing environment. -- >

You require knowledge to build application using react, Git, and Maven to use Headless adaptive forms.

<!-- 

### Download the latest version of AEM as a Cloud Service SDK or Forms feature archive (AEM Forms add-on) from Software Distribution {#software-distribution}

To download the supported version of Adobe Experience Manager as a Cloud Service SDK or Forms feature archive (AEM Forms add-on):

1. Log in to [Software Distribution](https://experience.adobe.com/#/downloads) portal with your Adobe ID.

    >[!NOTE]
    >
    > Your Adobe Organization must be provisioned for AEM as a Cloud Service to download the AEM as a Cloud Service SDK.

1. Navigate to the **[!UICONTROL AEM as a Cloud Service]** tab.
1. Sort by published date in descending order.
1. Click on the latest Adobe Experience Manager as a Cloud Service SDK or Forms feature archive (AEM Forms add-on).
1. Review and accept the EULA. Tap the **[!UICONTROL Download]** button. -->

## 系统要求 {#headless-adaptive-forms-system-requirements}

要安装AEM SDK，您的本地计算机必须满足以下最低要求：

* [Java开发工具包11](https://experience.adobe.com/#/downloads/content/software-distribution/en/general.html?1_group.propertyvalues.property=.%2Fjcr%3Acontent%2Fmetadata%2Fdc%3AsoftwareType&1_group.propertyvalues.operation=equals&1_group.propertyvalues.0_values=software-type%3Atooling&fulltext=Oracle%7E+JDK%7E+11%7E&orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&orderby.sort=desc&layout=list&p.offset=list&p.offset=0&p.limit=14&p.limit=144)
* [最新版本的Git](https://git-scm.com/downloads)。 如果您是初次使用Git，请参阅[安装Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)。
* [Node.js 16.13.0或更高版本](https://nodejs.org/en/download/)。<!-- URL is 404! If you are new to Node.js, see [How to install Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs). -->
* [Maven 3.6或更高版本](https://maven.apache.org/download.cgi)。 如果您不熟悉Maven，请参阅[安装Apache Maven](https://maven.apache.org/install.html)。

## 设置开发环境 {#headless-adaptive-forms-procedure-to-setup-development-environment}

要设置新的本地开发环境并使用它来开发和测试Headless自适应表单，请执行以下操作：

1. [设置AEM as a Cloud Service SDK](#setup-author-instance)。
1. [将AEM Forms存档(AEM Forms Cloud Service加载项)添加到AEM SDK](#add-forms-archive)。

<!--

1. (Optional) [Add Forms-specific users to your local Author instance](#configure-users-and-permissions).
1. (Optional) Install [Adaptive forms builder extension for Microsoft Visual Studio Code](#microsoft-visual-studio-code-extension-for-headless-adaptive-forms). 

-->

### 1.设置AEM as a Cloud Service SDK {#setup-author-instance}

AEM as a Cloud Service SDK (AEM SDK)为开发人员创建和测试Headless自适应表单提供了本地体验。 您可以使用AEM as a Cloud Service SDK创建和预览Headless自适应表单，从而能够在本地执行与开发相关的大多数验证。 要设置本地创作实例，请执行以下操作：

1. [下载](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)最新的[!DNL Adobe Experience Manager]as a Cloud Service SDK。 使用发布日期列对最新的SDK进行排序并轻松找到它们。
它采用.zip格式。 支持的版本为aem-sdk-2022.7.8085.20220725T140323Z-220700.zip及更高版本。

   ![从软件分发门户下载AEM Cloud Service SDK](assets/software-distribution.png)


1. 将下载的.zip文件解压到本地计算机上的某个目录。
1. 在本地计算机上创建一个目录，用作创作实例的安装位置。 例如 `~/aem-sdk/author`。
1. 将.jar文件从提取的SDK文件复制到安装位置，并将文件重命名为`aem-author-p4502.jar`。 文件名中的`p4502`字符串指定要使用的端口号。 您还可以指定其他端口号。

   >[!NOTE]
   >
   > 不要双击.jar文件来启动它。 它导致[错误](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime#troubleshooting-double-click)。

1. 打开命令提示符：
   * 在Windows上，使用&#x200B;**以管理员身份运行**&#x200B;选项在提升的模式下打开命令提示符。
   * 在Linux®上，确保以root用户身份打开终端窗口。

1. 导航到包含复制的.jar文件的安装位置，然后运行以下命令：

   `java -jar aem-author-p4502.jar -r prerelease`

   ![从软件分发门户下载AEM Cloud Service SDK](assets/install-sdk.png)

   * `-r prerelease`开关启用仅在预发行版和有限发行版程序下可用的功能。
   * 您可以使用`admin`作为本地开发的用户名和密码，以减少认知负载。

   AEM启动后，登录页面将在Web浏览器中打开。 您还可以在Web浏览器中打开地址为`http://localhost:<port>`的AEM SDK实例的登录页面。 例如，[http://localhost:4502](http://localhost:4502)。

1. 登录到您的创作实例。 点按![帮助](/help/assets/Help-icon.svg)图标，点按“关于Adobe Experience Manager”，并确保版本号包含“预发行版”后缀。

   ![帮助](/help/assets/prerelease.png)

如果未看到PRERELEASE后缀，请停止服务器，删除`[AEM SDK installation]/crx-quickstart folder`，然后使用`-r prerelease`开关重新启动AEM SDK .jar文件。 有关更多选项，请参阅[疑难解答](/help/troubleshooting.md)。

### 2.将AEM Forms存档(AEM Forms Cloud Service附加组件)添加到AEM SDK {#add-forms-archive}

AEM Forms as a Cloud Service功能存档(AEM Forms Cloud Service加载项)提供了用于在本地开发环境中创建Headless自适应表单的工具。 要安装功能存档，请执行以下操作：

1. 从[!DNL AEM Forms]Software Distribution[下载并提取最新的](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?fulltext=AEM*+Forms*+add*+on*&orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&orderby.sort=desc&layout=list&p.offset=0&p.limit=20)功能存档(AEM Forms加载项)。 使用发布日期列对最新的SDK进行排序并轻松找到它们。 支持的版本为aem-forms-addon-2022.07.06.02-220600及更高版本。

1. 导航到crx-quickstart/install目录。 如果该文件夹不存在，请创建它。
1. 停止AEM SDK实例。 您可以终止运行AEM SDK实例的命令提示符窗口以停止AEM。
1. 将[!DNL AEM Forms]加载项功能存档从第1步提取的文件`aem-forms-addon-<version>.far`复制到安装文件夹。
1. 使用以下命令重新启动AEM SDK实例：

   `java -jar aem-author-p4502.jar -r prerelease`

<!-- 

### 3. (Optional) Configure users and permissions {#configure-users-and-permissions}

Create seperate user accounts for Form Developer, Form Practitioner, and end users. These account help you test Headless adaptive forms for various types of users. To create a user account and add roles to the account:

1. Login to your AEM SDK instance.
1. Go to Tools > Security > Users and tap Create. The Create New User wizard opens.
1. In the details tab, specify an ID and Password. All other fields are optional. It is recommended to provide name and an email address.
1. In the Groups tab, search and select user-groups for a user depending on their role. The table below lists all types of users and pre-defined groups for each type of forms users based on their role:
  
    | User Type | AEM Group |
    |---|---|
    | Form developer | [!DNL forms-users] (AEM Forms Users), [!DNL template-authors], [!DNL workflow-users], [!DNL workflow-editors], and [!DNL fdm-authors]  |
    | Customer Experience Lead or UX Designer| [!DNL forms-users], [!DNL template-authors]|
    | AEM administrator | [!DNL aem-administrators], [!DNL fd-administrators] |
    | End user| When a user must log in to view and submit an Adaptive Form, add such users to [!DNL forms-users] group. </br> When no user authentication is required to access Adaptive Forms, do not assign any group to such users.|

<!-- ### 4. (Optional) Install Visual Studio Code extension for Headless adaptive forms {#microsoft-visual-studio-code-extension-for-headless-adaptive-forms}

You can use any IDE for developing Headless adaptive forms. Adobe provides an extension for Microsoft&reg;reg; Visual Studio Code to make it easier for you to navigate structure and develop Headless adaptive forms. The extension adds adaptive forms related IntelliSense capabilities and helps auto-complete Headless adaptive forms JSON syntax. It also adds a panel, titled Forms Tree, to help navigate structure of Headless adaptive form. To use the extension: 

1. Ensure [Microsoft Visual Studio Code 1.62.0 or later](https://code.visualstudio.com/docs/supporting/FAQ#_how-do-i-find-the-version) is installed. If you have an older version or no version installed, download the latest version from [Microsoft Website](https://code.visualstudio.com/docs/setup/setup-overview)
   >[!NOTE]
   >
   >
   > To use Visual Studio from command line on macOS, see [Launching from the command line](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line).

1. Download the [Adaptive forms builder extension](/help/assets/adaptive-form-builder-0.12.0.vsix).

1. Navigate the directory containing the *adaptive-form-builder-[version].vsix* file.

1. Run the following command or see [Install from a VSIX](https://code.visualstudio.com/docs/editor/extension-marketplace#_install-from-a-vsix) article for detailed instructions to install a Visual Studio Code extension from a VSIX file:

    `code -–install-extension adaptive-form-builder-[version].vsix`

    </br> Replace the [version] with actual version of the extension. For example, `code -–install-extension adaptive-form-builder-0.12.0.vsix`

    </br> 

    ![Installing extension](/help/assets/install-extension.png)

<!-- ## Create and setup a react app

Adaptive forms renderer component is a react based component. It requires a react app to run and render a Headless adaptive form. To create and setup react app:

1. Open terminal in Visual Studio code and run the following command to create a react app and installs all related dependencies:

    ```shell
    npx create-react-app [react-app-name] --scripts-version 4.0.3 --template typescript
    ```

    Where [react-app-name] represents name of the project, script version is 4.0.3, and template of type typescript. For example, the following command creates a react app named *headless-forms-demo*.

    ```shell
    npx create-react-app headless-forms-demo --scripts-version 4.0.3 --template typescript
    ```

    It may take some time to create the react app and install all the dependencies. The command creates an empty react app with latest version of react and react-dom dependencies. It does not have any artifacts related to adaptive forms renderer component.

1. Adaptive forms renderer component is based on react spectrum and requires react 16.0.0 and react-dom 16.0.0. To install react 16.0.0 and related dependencies:
    1. Open the Visual Studio code terminal Window or command prompt.
    1. Navigate to the directory of react project.  
    1. Run the following command:

        ```shell
        npm install --save react@16.0.0 react-dom@16.14.0 -force
        ```

1. Run the following command to install adaptive forms renderer component related dependencies:

    ```shell
    npm i --save @aemforms/forms-super-component @aemforms/forms-react-core-components @aemforms/forms-super-component @adobe/react-spectrum @react/react-spectrum
    ```

<!-- 1. Install dependencies for adaptive forms renderer component. Packages for these dependencies are available in Adobe Artifactory. To authenticate with Adobe Artifactory and install dependencies for adaptive forms renderer component:

    1. Create environment variables ARTIFACTORY_USER and ARTIFACTORY_API_TOKEN. The ARTIFACTORY_USER stores Adobe LDAP username and ARTIFACTORY_API_TOKEN stores your [Adobe Artifactory token](https://wiki.corp.adobe.com/display/Artifactory/API+Keys)

    1. Run the following command to set NPM_TOKEN and NPM_EMAIL tokens:

        ```shell

        auth=$(curl -s -u${ARTIFACTORY_USER}:${ARTIFACTORY_API_TOKEN} https://artifactory.corp.adobe.com/artifactory/api/npm/auth)
        export NPM_TOKEN=$(echo "${auth}" | grep "_auth" | awk -F " " '{ print $3 }')
        export NPM_EMAIL=$(echo "${auth}" | grep "email" | awk -F " " '{ print $3 }')
        ```

        These tokens are required to communicated with Adobe Artifactory.

    1. Create a .npmrc file in the react project.

        ![.npmrc file](/help/assets/npmrc.png)

    1. Add the following code to the file:

        ```shell
        @aemforms:registry=https://artifactory.corp.adobe.com/artifactory/api/npm/npm-aem-release/
        @react:registry=https://artifactory.corp.adobe.com/artifactory/api/npm/npm-react-release/
        @quarry:registry=https://artifactory.corp.adobe.com/artifactory/api/npm/npm-adobe-release-local/
        //artifactory.corp.adobe.com/artifactory/api/npm/npm-adobe-release-loca/:_auth=${NPM_TOKEN}
        //artifactory.corp.adobe.com/artifactory/api/npm/npm-aem-release/:_auth=${NPM_TOKEN}
        //artifactory.corp.adobe.com/artifactory/api/npm/npm-react-release/:_auth=${NPM_TOKEN}
        _auth=${NPM_TOKEN}
        email=${NPM_EMAIL}
        always-auth=true
        ```

        It defines the antifactory repositories to use for Headless adaptive forms, react, and quarry related scope.
    1. Run the following command to install adaptive forms renderer component related dependencies:

    ```shell
    npm i --save @aemforms/crispr-react-bindings @aemforms/crispr-react-core-components @adobe/react-spectrum @react/react-spectrum
    ```
 
-->
您的本地环境已就绪。 您可以继续创建Headless自适应表单。
