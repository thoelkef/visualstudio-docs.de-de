---
title: '&lt;EntryPoint&gt; -Element (Office-Entwicklung in Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <entryPoint> element
- <entryPoint> element
- entryPoint element
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: e6e6ffe216d800a58a34696c8577ff08adc94b0f
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804428"
---
# <a name="ltentrypointgt-element-office-development-in-visual-studio"></a>&lt;EntryPoint&gt; -Element (Office-Entwicklung in Visual Studio)
  Durch jedes `entryPoint` -Element im `vstav3` -Namespace wird eine Anpassungsassembly gekennzeichnet, die bei Installation dieser [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] -Anwendung ausgeführt werden sollte.

## <a name="syntax"></a>Syntax

```xml
<entryPoint class>
    <assemblyIdentity />
</entryPoint>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `entryPoint` -Element ist erforderlich und befindet sich im `vstav3` -Namespace.

 Jedes `entryPoint` -Element kann nur eine Anpassungsassembly enthalten. In einem Anwendungsmanifest können mehrere `entryPoint` -Elemente definiert werden.

 Das `entryPoint` -Element weist folgende Attribute auf:

|Attribut|Beschreibung|
|---------------|-----------------|
|`class`|Erforderlich. Kennzeichnet eine auszuführende Anpassungsassembly. Die Syntax für dieses Attribut ist *NamespaceName.ClassName*.|

 `entryPoint` weist das folgende Element auf:

### <a name="assemblyidentity"></a>assemblyIdentity
 Erforderlich. Das `assemblyIdentity` -Element im `vstav3` -Namespace verweist auf ein vorhandenes `assemblyIdentity` -Element im [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] -Anwendungsmanifest.

 Die Rolle des `assemblyIdentity` und ihre Attribute in [ &#60;AssemblyIdentity&#62; Element &#40;ClickOnce-Anwendung&#41;](../deployment/assemblyidentity-element-clickonce-application.md).

## <a name="document-level-customization-example"></a>Beispiel für die Anpassung auf Dokumentebene

### <a name="description"></a>Beschreibung
 Das folgende Codebeispiel veranschaulicht `entryPoint` -Elemente in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestellte Office-Projektmappe auf Dokumentebene. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Code

```xml
<vstav3:entryPoint
  class="ContosoExcelWorkbook.ThisWorkbook">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
<vstav3:entryPoint
  class="ContosoExcelWorkbook.Sheet1">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
<vstav3:entryPoint
  class="ContosoExcelWorkbook.Sheet2">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
<vstav3:entryPoint
  class="ContosoExcelWorkbook.Sheet3">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
```

## <a name="vsto-add-in-example"></a>Beispiel für VSTO-Add-in

### <a name="description"></a>Beschreibung
 Das folgende Codebeispiel veranschaulicht ein `entryPoint` -Element in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestellte Office-Projektmappe auf Anwendungsebene. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Code

```xml
<vstav3:entryPoint
  class="ContosoOutlookAddIn.ThisAddIn">
  <assemblyIdentity
    name="ContosoOutlookAddIn"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
```

## <a name="see-also"></a>Siehe auch

- [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md)