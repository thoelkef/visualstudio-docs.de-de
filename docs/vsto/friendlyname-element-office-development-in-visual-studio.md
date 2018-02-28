---
title: '&lt;FriendlyName&gt; -Element (Office-Entwicklung in Visual Studio) | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <friendlyName> element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 446a64c402ed9eb70b933b8c32f86426277564c5
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="ltfriendlynamegt-element-office-development-in-visual-studio"></a>&lt;FriendlyName&gt; -Element (Office-Entwicklung in Visual Studio)
  Das `friendlyName` -Element des `vstov4` Namespace speichert den angezeigten Namen in der Liste der installierten Programme.  
  
## <a name="syntax"></a>Syntax  
  
```  
<friendlyName>  
</friendlyName>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Das `friendlyName` -Element befindet sich im `vstov4` Namespace. Der Wert wird in der Liste der installierten Programme auf dem Computer und im Dialogfeld der COM-VSTO-Add-Ins von Microsoft Office-Anwendungen angezeigt.  
  
 Das `friendlyName` Element weist keine Attribute oder untergeordnete Elemente auf.  
  
## <a name="vsto-add-in-example"></a>Beispiel für ein VSTO-Add-In  
  
### <a name="description"></a>Beschreibung  
 Das folgende Codebeispiel veranschaulicht das `friendlyName` -Element in einer mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestellten Projektmappe auf Anwendungsebene. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```  
<vstov4:friendlyName>  
  ContosoOutlookAddIn  
</vstov4:friendlyName>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce-Anwendungsmanifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  