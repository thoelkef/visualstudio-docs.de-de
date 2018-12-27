---
title: '&lt;FriendlyName&gt; -Element (Office-Entwicklung in Visual Studio)'
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
- application manifests [Office development in Visual Studio], <friendlyName> element
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: bcb22c14931992f572f7ffbb4ea74bec852714d0
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648457"
---
# <a name="ltfriendlynamegt-element-office-development-in-visual-studio"></a>&lt;FriendlyName&gt; -Element (Office-Entwicklung in Visual Studio)
  Das `friendlyName` -Element des `vstov4` Namespace speichert den angezeigten Namen in der Liste der installierten Programme.  
  
## <a name="syntax"></a>Syntax  
  
```xml
<friendlyName>  
</friendlyName>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Das `friendlyName` -Element befindet sich im `vstov4` Namespace. Der Wert wird in der Liste der installierten Programme auf dem Computer und im Dialogfeld der COM-VSTO-Add-Ins von Microsoft Office-Anwendungen angezeigt.  
  
 Das `friendlyName` Element weist keine Attribute oder untergeordnete Elemente auf.  
  
## <a name="vsto-add-in-example"></a>Beispiel für VSTO-Add-in  
  
### <a name="description"></a>Beschreibung  
 Das folgende Codebeispiel veranschaulicht das `friendlyName` -Element in einer mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestellten Projektmappe auf Anwendungsebene. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```xml  
<vstov4:friendlyName>  
  ContosoOutlookAddIn  
</vstov4:friendlyName>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce-Anwendungsmanifest](/visualstudio/deployment/clickonce-application-manifest)  
  