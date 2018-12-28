---
title: '&lt;VstoRuntime&gt; -Element (Office-Entwicklung in Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <vstoRuntime> element
- <vstoRuntime> element
- vstoRuntime element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 80ef1c8e347aa2447ff48838015bb6499236e123
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/27/2018
ms.locfileid: "53802662"
---
# <a name="ltvstoruntimegt-element-office-development-in-visual-studio"></a>&lt;VstoRuntime&gt; -Element (Office-Entwicklung in Visual Studio)
  Das `vstoRuntime` -Element des `vstav3` -Namespace enthält eine unterstützte Version der Visual Studio Tools for Office-Laufzeit für eine bestimmte Office-Projektmappe.

## <a name="syntax"></a>Syntax

```xml
<vstoRuntime
    release
    version
    supportUrl />
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `vstoRuntime` -Element ist erforderlich und befindet sich im `vstav3` -Namespace. Wenn eine Office-Projektmappe zwei Versionen der Visual Studio-Tools für Office-Laufzeit unterstützt, gibt es zwei `vstoRuntime` -Elemente im Anwendungsmanifest.

 Das `vstoRuntime` -Element weist folgende Attribute auf.

|Attribut|Beschreibung|
|---------------|-----------------|
|`release`|Erforderlich. Die Releaseversion der Visual Studio Tools for Office-Laufzeit.|
|`version`|Erforderlich. Versionsnummer der Visual Studio Tools for Office-Laufzeit.|
|`supportUrl`|Dies ist optional. Link zum Installationspfad der Visual Studio Tools for Office-Laufzeit.|

 `vstoRuntime` enthält keine Elemente.

## <a name="example"></a>Beispiel
 Das folgende Codebeispiel veranschaulicht das `vstoRuntime` -Element in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestellte Office-Projektmappe. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).

```xml
<vstav3:vstoRuntime
    release="VSTOR40Beta1"
    version="10.0.20303"
    supportUrl="http://www.microsoft.com" />
```

## <a name="see-also"></a>Siehe auch

- [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md)
