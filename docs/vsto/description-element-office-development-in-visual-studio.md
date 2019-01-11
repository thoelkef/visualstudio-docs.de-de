---
title: '&lt;Beschreibung&gt; -Element (Office-Entwicklung in Visual Studio)'
titleSuffix: ''
ms.custom: secdec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 61c71bac86bed67750997ac225e3a17250183429
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854489"
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;Beschreibung&gt; -Element (Office-Entwicklung in Visual Studio)
  Im `description` -Element des `vstov4` -Namespace wird die Beschreibung für die Office-Projektmappe gespeichert, die im Dialogfeld für COM-Add-Ins von Microsoft Office-Anwendungen angezeigt werden.

## <a name="syntax"></a>Syntax

```xml
<description>
</description>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Dies ist optional. Das `description` -Element befindet sich im `vstov4` -Namespace. Es enthält die Beschreibung des Add-Ins, das im Dialogfeld für COM-Add-Ins von Microsoft Office-Anwendungen angezeigt wird.

 Das `description` Element weist keine Attribute oder Elemente auf.

## <a name="vsto-add-in-example"></a>Beispiel für VSTO-Add-in

### <a name="description"></a>Beschreibung
 Das folgende Codebeispiel veranschaulicht das `description` -Element für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestellte Projektmappe auf Anwendungsebene. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Code

```xml
<vstov4:description>
  ContosoOutlookAddIn - Outlook add-in
  created with Visual Studio Tools for Office
</vstov4:description>
```

## <a name="see-also"></a>Siehe auch

- [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md)