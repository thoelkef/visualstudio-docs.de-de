---
title: '&lt;PostActionData&gt; -Element (Office-Entwicklung in Visual Studio) | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <postActionData> element
- application manifests [Office development in Visual Studio], <postActionData> element
- postActionData element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c33e2bae7214252f0d0a871ed5a21a62d3fb9372
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ltpostactiondatagt-element-office-development-in-visual-studio"></a>&lt;PostActionData&gt; -Element (Office-Entwicklung in Visual Studio)
  Das `postActionData` -Element des `vstav3` -Namespace gibt die Daten an, die jeder Aktion nach der Bereitstellung zugeordnet sind, die nach der Installation von Office-Projektmappen ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
<postActionData>  
</postActionData>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Das `postActionData` -Element ist optional und befindet sich im `vstav3` -Namespace. In einem Anwendungsmanifest ist für jede Aktion nach der Bereitstellung ein `postActionData` -Element definiert.  
  
 Das `postActions` -Element weist keine Attribute auf.  
  
 `postActions` hat keine untergeordneten Elemente.  
  
## <a name="post-deployment-action-example"></a>Beispiel für eine Aktion nach der Bereitstellung  
  
### <a name="description"></a>Beschreibung  
 Das folgende Codebeispiel veranschaulicht das `postAction` -Element in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestellte Office-Projektmappe. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```  
<vstav3:postActionData>  
  data in any format  
</vstav3:postActionData>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce-Anwendungsmanifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  