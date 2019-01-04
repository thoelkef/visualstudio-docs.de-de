---
title: '&lt;PostAction&gt; -Element (Office-Entwicklung in Visual Studio)'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postAction> element
- <postAction> element
- postAction element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1886a1c0be486cfae8e85d0accd0fb42dc5d5353
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53958799"
---
# <a name="ltpostactiongt-element-office-development-in-visual-studio"></a>&lt;PostAction&gt; -Element (Office-Entwicklung in Visual Studio)
  Das `postAction` -Element des `vstav3` -Namespace enthält alle `entrypoint` -Elemente und alle `postActionData` -Elemente, die Aktionen nach der Bereitstellung zugeordnet sind, die ausgeführt werden, sobald Office-Projektmappen installiert sind.

## <a name="syntax"></a>Syntax

```xml
<postAction>
  <entryPoint>
  </entryPoint>
  <postActionData>
  </postActionData>
</postAction>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `postAction` -Element ist optional und befindet sich im `vstav3` -Namespace. In einem Anwendungsmanifest ist für jede Aktion nach der Bereitstellung ein `postAction` -Element definiert.

 Das `postAction`-Element hat keine Attribute.

 `postAction` hat die folgenden Elemente:

### <a name="entrypoint"></a>entrypoint
 Dies ist optional. Die Rolle der `entryPoint` Element in der `vstav3` Namespace definiert ist, [ &#60;EntryPoints&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md).

### <a name="postactiondata"></a>postActionData
 Dies ist optional. Die Rolle der `postActionData` Element in der `vstav3` Namespace definiert ist, [ &#60;PostActionData&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md).

## <a name="post-deployment-action-example"></a>Beispiel für die Aktion nach der Bereitstellung

### <a name="description"></a>Beschreibung
 Das folgende Codebeispiel veranschaulicht das `postAction` -Element in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestellte Office-Projektmappe. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Code

```xml
<vstav3:postAction>
  <vstav3:entryPoint
    class="PostDeploymentAction.PostDeploymentActionSample">
    <assemblyIdentity
      name="PostDeploymentAction"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="msil" />
  </vstav3:entryPoint>
  <vstav3:postActionData>
  </vstav3:postActionData>
</vstav3:postAction>
```

## <a name="see-also"></a>Siehe auch

- [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md)
