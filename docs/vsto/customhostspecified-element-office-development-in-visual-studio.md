---
title: '&lt;CustomHostSpecified&gt; -Element (Office-Entwicklung in Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0880e0ddf4763cf2c67c10871992a24b76f59ef2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53896642"
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;CustomHostSpecified&gt; -Element (Office-Entwicklung in Visual Studio)
  Die `customHostSpecified` Element gibt an, dass diese Lösung nicht um eine eigenständige Anwendung ist. Office-Projektmappen enthalten die Komponenten, die in Microsoft Office-Anwendungen gehostet werden.

## <a name="syntax"></a>Syntax

```xml
<customHostSpecified />
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Die `customHostSpecified` Element ist erforderlich für Office-Projektmappen. Dieses Element ist der `co.v1` Namespace und gibt an, dass diese Bereitstellung eine Komponente enthält, die innerhalb eines benutzerdefinierten Hosts bereitgestellt werden und ist keine eigenständige Anwendung.

 Dieses Element ist ein untergeordnetes Element des ersten `<entrypoint>` Elements im Manifest Anwendung. Es können keine anderen untergeordneten Elemente in dieser werden `<entrypoint>` Element oder [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] löst einen Validierungsfehler während der Installation.

 Dieses Element weist keine Attribute und keine untergeordneten Elemente.

## <a name="example"></a>Beispiel
 Das folgende Codebeispiel veranschaulicht die `customHostSpecified` Element in einem Anwendungsmanifest für eine Office-Projektmappe. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

## <a name="see-also"></a>Siehe auch

- [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md)