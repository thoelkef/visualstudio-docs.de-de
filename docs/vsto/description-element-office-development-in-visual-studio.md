---
title: '&lt;Beschreibung&gt; -Element (Office-Entwicklung in Visual Studio) | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
ms.assetid: 27c90f8c-393d-4557-9371-2e4e3c4a2d95
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 350a9003fcb87a6226e9ea14f7734aa40b9e62db
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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
  
  