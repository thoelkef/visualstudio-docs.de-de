---
title: '&lt;Beschreibung&gt; -Element (Office-Entwicklung in Visual Studio) | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 13755a20b091696bf741c1f25360941e01b65945
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;Beschreibung&gt; -Element (Office-Entwicklung in Visual Studio)
  Im `description` -Element des `vstov4` -Namespace wird die Beschreibung für die Office-Projektmappe gespeichert, die im Dialogfeld für COM-Add-Ins von Microsoft Office-Anwendungen angezeigt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
<description>  
</description>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Dies ist optional. Das `description` -Element befindet sich im `vstov4` -Namespace. Es enthält die Beschreibung des Add-Ins, das im Dialogfeld für COM-Add-Ins von Microsoft Office-Anwendungen angezeigt wird.  
  
 Das `description` Element weist keine Attribute oder Elemente auf.  
  
## <a name="vsto-add-in-example"></a>Beispiel für ein VSTO-Add-In  
  
### <a name="description"></a>description  
 Das folgende Codebeispiel veranschaulicht das `description` -Element für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestellte Projektmappe auf Anwendungsebene. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```  
<vstov4:description>  
  ContosoOutlookAddIn - Outlook add-in   
  created with Visual Studio Tools for Office  
</vstov4:description>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce-Anwendungsmanifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  