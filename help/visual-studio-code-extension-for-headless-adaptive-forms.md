---
title: 适用于Headless自适应表单的Visual Studio代码扩展
description: 适用于Headless自适应表单的Visual Studio代码扩展
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: headless，自适应表单，Visual Studio代码扩展
hide: false
exl-id: 11960e91-6c09-48d4-9d57-37537f808cd4
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# 适用于Headless自适应表单的Microsoft Visual Studio代码扩展

如果您使用Microsoft® Visual Studio Code作为IDE，则可以使用适用于Microsoft Visual Studio Code的Adaptive Forms扩展。 扩展：

* 在Visual Studio代码中添加了用于自适应Forms的IntelliSense功能
* 帮助验证和自动完成Headless自适应表单组件的JSON语法
* 提供了一个面板，用于轻松导航Headless自适应表单的结构
* 帮助翻译Headless自适应表单

<!-- 

The extension o easily navigate the structure 

Adobe provides an extension for Microsoft&reg; Visual Studio Code to make it easier for you to navigate structure and develop Headless adaptive forms in Visual Studio Code. The extension adds Adaptive Forms related IntelliSense capabilities and helps auto-complete Headless adaptive forms JSON syntax. It also adds a panel, titled Forms Tree, to help navigate structure of Headless adaptive form. 

-->

## 先决条件

* 下载并安装[Microsoft Visual Studio Code 1.62.0或更高版本](https://code.visualstudio.com/docs/supporting/FAQ#_how-do-i-find-the-version)。 如果您安装了旧版本或未安装版本，请从[Microsoft网站](https://code.visualstudio.com/docs/setup/setup-overview)下载最新版本。 若要从Apple macOS上的命令行使用Visual Studio，请参阅[从命令行启动](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line)。
* 下载[自适应表单生成器扩展](/help/assets/adaptive-form-builder-0.12.0.vsix)。

## 安装扩展

1. 打开命令提示符并导航到包含下载的扩展文件&#x200B;*adaptive-form-builder-[version].vsix*&#x200B;的目录。

1. 运行以下命令以安装扩展：

   `code -–install-extension adaptive-form-builder-0.12.0.vsix`

   <br>

   ![正在安装扩展](/help/assets/install-extension.png)


   有关.vsix文件的信息，请参阅[Microsoft Visual Studio代码帮助](https://code.visualstudio.com/docs/editor/extension-marketplace#_install-from-a-vsix)。
