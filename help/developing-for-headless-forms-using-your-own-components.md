---
title: 使用自定义组件渲染Headless表单
description: 了解如何创建自定义组件并将它们映射到Headless自适应Forms字段。 本指南介绍如何按字段类型和资源类型映射组件以实现自定义渲染和行为。
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: 5aba1821-35dc-4da4-b188-d4853d64d5ee
source-git-commit: 780f06a39c75dbf8795ac7a971150410ed7981e9
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---


# 使用自定义组件渲染Headless表单 {#developing-for-headless-forms-using-your-own-components}

在Headless自适应Forms中，您可以创建和实施自定义组件以定义表单的外观和功能。 虽然默认组件提供标准行为，但您可能需要特定的UI元素或交互，例如自定义“公告”组件或专用的“涂写签名”字段。

本文指导您创建自定义React组件并将其映射到Headless自适应表单。

## &#x200B;1. 创建自定义React组件

首先，创建将渲染表单字段的React组件。 此组件可以使用任何React库（如材料UI、Ant设计或您自己的自定义样式）。

例如，让我们创建一个自定义&#x200B;**公告**&#x200B;组件，该组件呈现具有特定样式的只读消息。

1. 导航到React项目的组件目录（如`src/components`）。
2. 为您的组件创建新文件夹和文件，例如`Announcement/index.tsx`。
3. 实施组件。 它应该接受与Headless Forms运行时兼容的`props`（通常接收字段的状态）。

```tsx
import React from 'react';
import { useRuleEngine } from '@aemforms/af-react-renderer';
import { FieldJson, State } from '@aemforms/af-core';

const Announcement = function (props: State<FieldJson>) {
    // The useRuleEngine hook connects the component to the form logic
    const [state, handlers] = useRuleEngine(props);

    if (!state.visible) {
        return null;
    }

    return (
        <div className="custom-announcement" style={{ border: '1px solid #ccc', padding: '10px', backgroundColor: '#f9f9f9' }}>
            <h3>{state?.label?.value}</h3>
            <p>{state?.default}</p>
        </div>
    );
}

export default Announcement;
```

## &#x200B;2. 映射自定义组件

要使用自定义组件，必须在`mappings.ts`文件中映射它。 Headless Forms运行时使用此映射确定要为JSON形式的每个字段呈现的React组件。

有两种主要方法来映射组件：按&#x200B;**字段类型**&#x200B;或按&#x200B;**资源类型**。

### 按字段类型映射

标准映射基于表单JSON中的`fieldType`属性（例如，`text-input`、`checkbox`、`button`）。 当您想要将标准组件的&#x200B;*所有*&#x200B;实例替换为自定义版本时，此功能非常有用。

1. 打开`src/utils/mappings.ts`（或定义映射的位置）。
2. 导入自定义组件。
3. 使用`fieldType`作为键将其添加到映射对象。

```typescript
import { mappings } from "@aemforms/af-react-components";
import Announcement from "../components/Announcement";

const customMappings: any = {
  ...mappings,
  "text-input": Announcement // This would replace ALL text-input fields (use with caution)
};

export default customMappings;
```

### 按资源类型映射（自定义组件）

如果您在AEM中创建了自定义组件（例如，扩展标准文本组件的“Announcement”组件），并且希望在React应用程序中以不同的方式呈现该特定组件&#x200B;*仅*，则应按其&#x200B;**资源类型**&#x200B;或唯一标识符映射它。

此方法允许您正常呈现标准文本组件，而自定义“Announcement”组件使用专门的React实施。

1. 标识组件的唯一标识符。 在Headless表单JSON中，这通常可在`:type`属性或自定义`fieldType`（如果已配置）中找到。
2. 使用此标识符添加映射。

```typescript
import { mappings } from "@aemforms/af-react-components";
import Announcement from "../components/Announcement";

const customMappings: any = {
  ...mappings,
  // Map by resource type or custom identifier
  "my-project/components/announcement": Announcement
};

export default customMappings;
```

> **注意：**&#x200B;请确保您的AEM表单模型导出正确的`:type`或与您在`mappings.ts`中使用的键匹配的标识符。

## &#x200B;3. 应用映射

最后，确保您的Headless表单实例使用这些自定义映射。

```tsx
import React from 'react';
import { AdaptiveForm } from '@aemforms/af-react-renderer';
import customMappings from './utils/mappings';
import formJSON from './form-def.json';

function App() {
  return (
    <AdaptiveForm
      formJson={formJSON}
      mappings={customMappings}
    />
  );
}

export default App;
```

按照这些步骤，您可以通过符合您的特定设计和功能要求的组件来扩展Headless自适应Forms的功能。
