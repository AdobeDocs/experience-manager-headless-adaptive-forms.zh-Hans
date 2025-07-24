---
title: Headless自适应Forms的已知问题
description: Headless自适应表单的已知问题。
keywords: headless，自适应表单，已知问题
hide: true
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 16%

---


# 已知问题 {#known-issues}

* 不支持编辑、显示和数据模式。 (CQ-4327047)
* minItems约束无法动态更改。 (CQ-4342499)
* 违反的面板级别验证不会引发任何错误。 (CQ-4342373)
* 违反的文件验证未引发任何错误。 (CQ-4342372)
* 自定义属性不是动态的。 (CQ-4342376)
* 使用表达式在更改事件上动态更改文件数据会导致无限循环。 (CQ-4342377)
* 文件附件不支持帮助文本。 (CQ-4342370)
* 如果未选中所需的复选框，则在提交时不会显示错误。 (CQ-4342371)
* aria-label未添加到文件附件中。 (CQ-4341494)
